# CSS Basic

[TOC]

##  更改文本的颜色
现在让我们来修改文本的颜色。

我们通过修改 h2 元素的 style 属性来改变文本颜色。

我们需要修改 color 属性值。

以下是将 h2 元素设置为蓝色的方法：

```html
<h2 style="color: blue;">CatPhotoApp</h2>
```

请注意，需要在内联 style 声明末尾加上 ;。

## 使用 class 选择器设置单个元素的样式
CSS 的 class 具有可重用性，可应用于各种 HTML 元素。

一个 CSS class 声明示例如下所示：
```html
<style>
  .blue-text {
    color: blue;
  }
</style>


可以看到，我们在 <style> 样式声明区域里，创建了一个名为 blue-text 的 class 选择器。 你可以这样将 class 应用于 HTML 元素：<h2 class="blue-text">CatPhotoApp</h2>。 注意在 CSS style 元素里，class 名以一个句点开头。 在 HTML 元素的 class 属性中，class 名的开头没有句点。
```

## 更改元素的字体大小
字体大小由 font-size 属性控制，如下所示：

```html
<style>
h1 {
  font-size: 30px;
}
</style>
```

## 设置元素的字体族名
通过 font-family 属性，我们可以设置元素里的字体族名。

如果你想将 h2 元素的字体设置为 sans-serif，可以这样写：

```html
h2 {
  font-family: sans-serif;
}
```


