## 1. h1,h2-head

```Html
<h1></h1>
```

##  2. p-paragraph

## 3. 注释

```Html
<!-->-->
```

## 4. El元素

main

img

```Html
<img src="https://www.freecatphotoapp.com/your-image.jpg" alt="A business cat wearing a necktie.">
```
header

footer

nav

video

article

section

## 5. 用 a 实现网页间的跳转

你可以用 a（Anchor，简写为 a）来实现网页间的跳转。

a 需要一个 href 属性指向跳转的目的地。 同时，它还应有内容。 例如：

```Html
<a href="https://www.freecodecamp.org">this links to freecodecamp.org</a>
```


用 a 实现网页内部跳转
a（anchor）元素也可以用于创建内部链接，跳转到网页内的各个不同部分。

要创建内部链接，你需要将链接的 href 属性值设置为一个哈希符号 # 加上你想内部链接到的元素的 id，通常是在网页下方的元素。 然后你需要将相同的 id 属性添加到你链接到的元素中。 id 是描述网页元素的一个属性，它的值在整个页面中唯一。

当用户点击了 Contacts 链接，页面就会跳转到网页的 Contacts 区域。

```Html
<a href="#contacts-header">Contacts</a>
...
<h2 id="contacts-header">Contacts</h2>
```

当用户点击 Contacts 链接，可以访问网页中带有 Contacts 标题元素的部分。

从锚点标签中删除 target="_blank" 属性，因为这会导致链接文档在新窗口标签中打开。

## 6. 用 # 号来创建链接占位符
有时你想为网站添加一个 a 元素，但还不确定要将它链接到哪里。

当你使用 JavaScript 更改链接的指向时，这也很方便，我们将在后面的课程中介绍。

href 属性的当前值是指向 “https://www.freecatphotoapp.com”。 请将 href 属性的值替换为#，以此来创建链接占位符。

例如: href="#"
## 给图片添加链接

你可以通过把元素嵌套进 a 里使其变成一个链接。

如果我们要把图片嵌套进 a 元素， 可以这样写：

<a href="#"><img src="https://www.bit.ly/fcc-running-cats" alt="Three kittens running towards the camera."></a>
如果把 a 的 href 属性值设置为 #，创建的是一个死链接（不跳转到其他画面）。

### 创建一个无序列表

HTML 有一个特定的元素用于创建无序列表。

无序列表以 <ul> 开始，中间包含一个或多个 <li> 元素， 最后以 </ul> 结束。

例如:
```html
<ul>
  <li>milk</li>
  <li>cheese</li>
</ul>
```
会创建一个要点列表，包括 milk 和 cheese。

### 创建一个有序列表
HTML 中有用于创建有序列表的特定元素。

有序列表以 <ol> 开始，中间包含一个或多个 <li> 元素。 最后以 </ol> 结束。

例如:
```html
<ol>
  <li>Garfield</li>
  <li>Sylvester</li>
</ol>
```
将创建一个包含 Garfield 和 Sylvester 的编号列表。

### 创建一个输入框
现在让我们来创建一个 Web 表单。

input 输入框可以让你轻松获得用户的输入。

你可以像这样创建一个文本输入框：
```html
<input type="text">
```
注意 input 输入框是没有结束标签的。

### 给输入框添加占位符文本
占位符文本用户在 input 输入框中输入任何东西前的预定义文本。

你可以像这样创建一个占位符：
```html
<input type="text" placeholder="this is placeholder text">
```
**注意：**别忘了 input 元素是 "自闭和标签"，即不需要结束标签。

### 创建一个表单
我们可以只通过 HTML 来实现发送数据给服务器的表单， 只需要给 form 元素添加 action 属性即可。

例如：
```html
<form action="/url-where-you-want-to-submit-form-data">
  <input>
</form>
```
把现有的 input 元素嵌套到一个表单 form 元素里，然后设置 form 元素的 action 属性值为 "https://www.freecatphotoapp.com/submit-cat-photo"。

### 给表单添加提交按钮通过
让我们来给表单添加一个 submit（提交）按钮。 点击提交按钮时，表单中的数据将会被发送到 action 属性指定的 URL 上。

例如：

<button type="submit">this button submits the form</button>
在 form 的底部创建一个按钮，按钮的类型为 submit，文本为 Submit。

### 给表单添加一个必填字段
当你设计表单时，你可以指定某些字段为必填项（required），只有当用户填写了该字段后，才可以提交表单。

如果你想把文本输入框设置为必填项，在 input 元素中加上 required 属性就可以了，例如：<input type="text" required>

请给 input 元素加上 required 属性，这样用户就必须先在输入框里填入内容，然后才可以提交表单。

然后尝试在不输入任何文本的情况下提交表单， 看看 HTML5 表单是如何通知你这个字段是必填的。

### 创建一组单选按钮
radio buttons（单选按钮）就好比单项选择题，正确答案只有一个。

单选按钮是 input 选择框的一种类型。

每一个单选按钮都应该嵌套在它自己的 label（标签）元素中。 这样，我们相当于给 input 元素和包裹它的 label 元素建立起了对应关系。

所有关联的单选按钮应该拥有相同的 name 属性。 创建一组单选按钮，选中其中一个按钮，其他按钮即显示为未选中，以确保用户只提供一个答案。

下面是一个单选按钮的例子：

<label> 
  <input type="radio" name="indoor-outdoor">Indoor 
</label>
最佳实践是在 label 元素上设置 for 属性，让其值与相关联的 input 单选按钮的 id 属性值相同。 这使得辅助技术能够在标签和相关的 input 元素之间建立关联关系。 例如：

<input id="indoor" type="radio" name="indoor-outdoor">
<label for="indoor">Indoor</label>
我们也可以在 label 标签中嵌入 input 元素：

<label for="indoor"> 
  <input id="indoor" type="radio" name="indoor-outdoor">Indoor 
</label>
在表格中添加一对单选按钮，每个按钮嵌套在自己的 label 元素中。 一个选项应该是 indoor ，另一个选项应该是 outdoor。 两个按钮的 name 属性都是 indoor-outdoor，以创建一组单选按钮。

### 创建一组复选框
checkboxes（复选框）就好比多项选择题，正确答案有多个。

复选框是 input 选择框的一种类型。

每一个复选框都应该嵌套在它自己的 label（标签）元素中。 这样，我们相当于给 input 元素和包裹它的 label 元素建立起了对应关系。

所有关联的复选框应该拥有相同的 name 属性。

使得 input 与 label 关联的最佳实践是在 label 元素上设置 for 属性，让其值与相关联的 input 复选框的 id 属性值相同。

下面是一个复选框的例子：

<label for="loving"><input id="loving" type="checkbox" name="personality"> Loving</label>
请给表单添加三个复选框， 每个复选框都被嵌套进 label 元素中。 并且它们的 name 属性均为 personality。

### 使用单选框和复选框的 value 属性通过
提交表单时，所选项的值会发送给服务端。 radio 和 checkbox 的 value 属性值决定了发送到服务端的实际内容。

例如：

<label for="indoor">
  <input id="indoor" value="indoor" type="radio" name="indoor-outdoor">Indoor
</label>
<label for="outdoor">
  <input id="outdoor" value="outdoor" type="radio" name="indoor-outdoor">Outdoor
</label>
这里有两个 radio 单选框。 当用户提交表单时，如果 indoor 选项被选中，表单数据会包含：indoor-outdoor=indoor。 也就是所选项的 name 和 value 属性值。

如果没有指明 value 属性值，则会使用默认值做为表单数据提交，也就是 on。 在这种情况下，如果用户选中 "indoor" 选项然后提交表单，表单数据则会包含 indoor-outdoor=on。 这样的表单数据看起来不够直观，因此最好将 value 属性值设置为一些有意义的内容。

给每一个 radio 和 checkbox 输入框添加 value 属性。 使用输入标签的文本，小写形式，作为属性的值。

### 给单选按钮和复选框添加默认选中项
用 checked 属性把第一个复选框和单选按钮都设置为默认选中。

在一个 input 元素里面添加 checked 这个词，即可实现。 例如:

<input type="radio" name="test-name" checked>
把第一个单选按钮和第一个复选框都设置为默认选中。

### 元素嵌套
div 元素也叫内容划分元素，是一个包裹其他元素的通用容器。

它也是 HTML 中出现频率最高的元素。

和其他普通元素一样，你可以用 <div> 来标记一个 div 元素的开始，用 </div> 来标记一个 div 元素的结束。

将你的列表“猫喜欢的三件事”和“猫最讨厌的三件事”放入同一个 div 元素中。

提示：你可以在第一个 <p> 之前插入 div 开始标记，在 </ol> 之后插入 div 结束标签。 这样，所有的列表都会位于 div 之内。

### 声明 HTML 的文档类型
之前的挑战涵盖了一些 HTML 元素和它们的用法。 另外有些元素为页面提供了整体结构，每个 HTML 文档中都应该有这些元素。

在文档的顶部，我们需要告诉浏览器网页所使用的 HTML 的版本。 HTML 是一个在不停发展的语言，大部分浏览器都支持 HTML 的最新标准，也就是 HTML5。 大部分主流浏览器都支持最新的 HTML5 规范。 但是一些陈旧的网页可能使用的是老版本的 HTML。

你可以通过 <!DOCTYPE ...> 来告诉浏览器页面上使用的 HTML 版本，"..." 部分就是版本号。 <!DOCTYPE html> 对应的就是 HTML5。

! 和大写的 DOCTYPE 是很重要的，尤其是对那些老的浏览器。 但 html 无论大写小写都可以。

所有的 HTML 代码都必须位于 html 标签中。 其中 <html> 位于 <!DOCTYPE html> 之后，</html> 位于网页的结尾。

这是一个网页结构的列子。 你的 HTML 代码会在两个 html 标签之间。

<!DOCTYPE html>
<html>

</html>
请在代码编辑器的顶部添加一个 DOCTYPE 为 HTML5 的声明。 在它下面添加 html 开始和结束标签，其中包裹一个 h1 元素。 标题可以包括任何文本。

### 定义 HTML 文档的 head 和 body
html 的结构主要分为两大部分：head 和 body。 网页的描述应放入 head 标签， 网页的内容（向用户展示的）则应放入 body 标签。

比如 link、meta、title 和 style 都应放入 head 标签。

这是网页布局的一个例子：

<!DOCTYPE html>
<html>
  <head>
    <meta />
  </head>
  <body>
    <div>
    </div>
  </body>
</html>
标记文本的结构主要分为两大部分：head 和 body。 head 元素应只包含 title，body 元素应该包含 h1 和 p。