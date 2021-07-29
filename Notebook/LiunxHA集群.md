# LinuxHA集群群集

[TOC]

## RHEL 7快速搭建HA集群

[RHEL 7快速搭建HA集群](https://blog.51cto.com/lduan/1741584)

## CentOS 7下Redis5集群的搭建和使用

[CentOS 7下Redis5集群的搭建和使用](https://m.linuxidc.com/Linux/2019-06/159177.htm)

CentOS 7下Redis5集群的搭建和使用
2019/06/27 12:45:39 来源：Linux社区 作者：hxun
25-31 minutes

1、简要说明

Redis5.0版是Redis产品的重大版本发布，推出了各种新特性，其中一点是放弃 Ruby的集群方式，改为 使用 C语言编写的 redis-cli的方式，是集群的构建方式复杂度大大降低。关于集群的更新可以在 Redis5 的版本说明中看到，如下：

The cluster manager was ported from Ruby (redis-trib.rb) to C code inside redis-cli. check `redis-cli --cluster help ` for more info.

可以查看Redis官网查看集群搭建方式，连接如下

https://redis.io/topics/cluster-tutorial

集群中应该至少有三个节点，每个节点有一备份节点。需要6台服务器。

如果条件有限，可以搭建伪分布式，以下步骤是在一台 Linux 服务器上搭建有6个节点的 Redis集群。

2、创建集群步骤

2.1、创建目录

        新建目录：mkdir /usr/local/redis-cluster

2.2、下载源码并解压编译

​wget http://download.redis.io/releases/redis-5.0.0.tar.gz
tar xzf redis-5.0.0.tar.gz
cd redis-5.0.0
make
make install PREFIX=/usr/local/redis

3、创建6个Redis配置文件

    6个配置文件不能在同一个目录，此处我们定义如下：

/root/software/redis/redis-cluster-conf/7001/redis.conf
/root/software/redis/redis-cluster-conf/7002/redis.conf
/root/software/redis/redis-cluster-conf/7003/redis.conf
/root/software/redis/redis-cluster-conf/7004/redis.conf
/root/software/redis/redis-cluster-conf/7005/redis.conf
/root/software/redis/redis-cluster-conf/7006/redis.conf

一些操作命令仅供参考：

cp redis.conf /usr/local/redis/bin
cd /usr/local/redis/
cp -r bin ../redis-cluster/redis01
cd /usr/local/redis-cluster/redis01
rm dump.rdb #删除快照
vim redis.conf 

配置文件的内容为：

port 7001  #端口
cluster-enabled yes #启用集群模式
cluster-config-file nodes.conf
cluster-node-timeout 5000 #超时时间
appendonly yes
daemonize yes #后台运行
protected-mode no #非保护模式
pidfile  /var/run/redis_7001.pid
bind 172.20.10.7 #127.0.0.1改为本机ip地址,可用ifconfig查看ip

其中 port 和 pidfile 需要随着 文件夹的不同调增。

创建剩余5个实例：

[root@master redis-cluster]# cp -r redis01/ redis02
[root@master redis-cluster]# cp -r redis01/ redis03
[root@master redis-cluster]# cp -r redis01/ redis04
[root@master redis-cluster]# cp -r redis01/ redis05
[root@master redis-cluster]# cp -r redis01/ redis06

分别修改redis02 ~ redis06 的 redis.conf下的port 和 pidfile

4、启动节点

分别进入redis01、redis02、...redis06目录，执行： ./redis-server ./redis.conf

创建一个批处理文件，同时启动着六个Redis

vim startall.sh

添加如下内容：


cd redis01
./redis-server redis.conf
cd ..
cd redis02
./redis-server redis.conf
cd ..
cd redis03
./redis-server redis.conf
cd ..
cd redis04
./redis-server redis.conf
cd ..
cd redis05
./redis-server redis.conf
cd ..
cd redis06
./redis-server redis.conf
cd ..

然后执行chmod u+x start-all.sh将start-all.sh变成可执行文件

在当前目录下启动： ./startall.sh

查看：ps aux|grep redis

5、启动集群

因为我们使用的5.0.0的版本的Redis搭建的集群只需要把编译后的redis目录中的这个redis-cli文件拷贝到redis-cluster目录过来即可。(Redis版本5.0以后都是用C语言直接启动)

/usr/local/redis-cluster/redis-cli --cluster create 172.20.10.7:7001 172.20.10.7:7002 172.20.10.7:7003 172.20.10.7:7004 172.20.10.7:7005 172.20.10.7:7006 --cluster-replicas 1

启动后，可看到成功信息，如下：


>>> Performing hash slots allocation on 6 nodes...
Master[0] -> Slots 0 - 5460
Master[1] -> Slots 5461 - 10922
Master[2] -> Slots 10923 - 16383
Adding replica 172.20.10.7:7004 to 172.20.10.7:7001
Adding replica 172.20.10.7:7005 to 172.20.10.7:7002
Adding replica 172.20.10.7:7006 to 172.20.10.7:7003
>>> Trying to optimize slaves allocation for anti-affinity
[WARNING] Some slaves are in the same host as their master
M: a4128b5e581c3722acd9b093c5f29f5056f680b0 172.20.10.7:7001
 slots:[0-5460] (5461 slots) master
M: d6fed6f21269b8469a3076ac5fb168bd20f70c26 172.20.10.7:7002
 slots:[5461-10922] (5462 slots) master
M: 51a0f62dacead745ce5351cdbe0bdbae553ce413 172.20.10.7:7003
 slots:[10923-16383] (5461 slots) master
S: 45cc35740ac67f7988bb75325871ba12d08a76e4 172.20.10.7:7004
 replicates a4128b5e581c3722acd9b093c5f29f5056f680b0
S: 668054fe16cdf8741152cae863f5c636ed18b803 172.20.10.7:7005
 replicates d6fed6f21269b8469a3076ac5fb168bd20f70c26
S: ae39b7db285703f8c08412d6b04998c60a634295 172.20.10.7:7006
 replicates 51a0f62dacead745ce5351cdbe0bdbae553ce413
Can I set the above configuration? (type 'yes' to accept):yes

输入yes回车

>>> Nodes configuration updated
>>> Assign a different config epoch to each node
>>> Sending CLUSTER MEET messages to join the cluster
Waiting for the cluster to join
......
>>> Performing Cluster Check (using node 172.20.10.7:7001)
M: a4128b5e581c3722acd9b093c5f29f5056f680b0 172.20.10.7:7001
 slots:[0-5460] (5461 slots) master
 1 additional replica(s)
M: d6fed6f21269b8469a3076ac5fb168bd20f70c26 172.20.10.7:7002
 slots:[5461-10922] (5462 slots) master
 1 additional replica(s)
S: 45cc35740ac67f7988bb75325871ba12d08a76e4 172.20.10.7:7004
 slots: (0 slots) slave
 replicates a4128b5e581c3722acd9b093c5f29f5056f680b0
M: 51a0f62dacead745ce5351cdbe0bdbae553ce413 172.20.10.7:7003
 slots:[10923-16383] (5461 slots) master
 1 additional replica(s)
S: 668054fe16cdf8741152cae863f5c636ed18b803 172.20.10.7:7005
 slots: (0 slots) slave
 replicates d6fed6f21269b8469a3076ac5fb168bd20f70c26
S: ae39b7db285703f8c08412d6b04998c60a634295 172.20.10.7:7006
 slots: (0 slots) slave
 replicates 51a0f62dacead745ce5351cdbe0bdbae553ce413
[OK] All nodes agree about slots configuration.
>>> Check for open slots...
>>> Check slots coverage...
[OK] All 16384 slots covered.

至此，Reids5 集群搭建完成。

6、集群的操作

6.1、关闭集群

方法一：

  redis5 提供了关闭集群的工具，在如下目录：

/root/redis-5.0.0/utils/create-cluster

打开此文件修改端口为我们自己的，如下所示：

端口PROT设置为7000，NODES为6，工具会自动累加1 生成 7001-7006 六个节点 用于操作。

往下看再修改路径 和 添加 ip地址，如果不加会默认本地127.0.0.1

修改后，执行如下命令关闭集群：

/root/redis-5.0.0/utils/create-cluster/create-cluster stop

方法二：
create-cluster目录下编写脚本文件：vim shutdown.sh
内容如下：

/usr/local/redis-cluster/redis-cli -c -h 172.20.10.7 -p 7001 shutdown
/usr/local/redis-cluster/redis-cli -c -h 172.20.10.7 -p 7002 shutdown
/usr/local/redis-cluster/redis-cli -c -h 172.20.10.7 -p 7003 shutdown
/usr/local/redis-cluster/redis-cli -c -h 172.20.10.7 -p 7004 shutdown
/usr/local/redis-cluster/redis-cli -c -h 172.20.10.7 -p 7005 shutdown
/usr/local/redis-cluster/redis-cli -c -h 172.20.10.7 -p 7006 shutdown

然后执行chmod u+x shutdown.sh将shutdown.sh变成可执行文件

在当前目录下启动： ./shutdown.sh

查看：ps aux|grep redis

官方：/usr/local/redis-cluster/redis-cli -a xxx -c -h 192.168.5.100 -p 8001

提示：-a访问服务端密码，-c表示集群模式，-h指定ip地址，-p指定端口号

6.2、重新启动集群

/root/redis-5.0.0/utils/create-cluster/create-cluster start

6.3、使用脚本文件启动集群

vim startall.sh 追加如下内容：（记得改自己ip地址）

/usr/local/redis-cluster/redis-cli --cluster create 172.20.10.7:7001 172.20.10.7:7002 172.20.10.7:7003 172.20.10.7:7004 172.20.10.7:7005 172.20.10.7:7006 --cluster-replicas 1

 启动：./startall.sh

7、测试集群

redis-cluster目录下执行

redis01/redis-cli -h 192.168.25.153 -p 7002 -c

其中-c表示以集群方式连接redis，-h指定ip地址，-p指定端口号

cluster nodes 查询集群结点信息

cluster info 查询集群状态信息

8、测试代码

    @Test
    public void testJedisCluster() {
        //集群结点
        HashSet<HostAndPort> nodes = new HashSet<>();
        nodes.add(new HostAndPort("172.20.10.7", 7001));
        nodes.add(new HostAndPort("172.20.10.7", 7002));
        nodes.add(new HostAndPort("172.20.10.7", 7003));
        nodes.add(new HostAndPort("172.20.10.7", 7004));
        nodes.add(new HostAndPort("172.20.10.7", 7005));
        nodes.add(new HostAndPort("172.20.10.7", 7006));

                JedisCluster cluster = new JedisCluster(nodes);

                cluster.set("name", "zhangsan");
        String str = cluster.get("name");
        System.out.println(str);

                cluster.close();
    }
