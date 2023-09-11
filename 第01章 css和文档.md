#  第01章 css和文档

## 1.2 元素

元素是文档结构的基础。在 HTML 中，最常见的元素很容易识别，如 `p`, `table`, `span`, `a`, 和 `div`。文档中的每个元素都在其表示中起作用。

虽然 CSS 依赖于元素，但并不是所有的元素都是平等创建的。例如，图像和段落不是同一类型的元素，`span` and `div` 也不是。在 CSS 中，元素通常有两种形式:替换和非替换。

1. **非替换元素**： 被替换的元素是那些元素的内容被文档内容没有直接表示的内容所替换的元素。最熟悉的 HTML 示例可能是 img 元素，它被文档本身外部的图像文件所取代。事实上，img 并没有实际的内容，你可以在这个简单的例子中看到:

   ```html
   <img src="howdy.gif" />
   ```

   

2. **替换元素**： 大多数 HTML 元素是不可替换的元素。这意味着它们的内容由用户代理(通常是浏览器)在元素本身生成的框中显示。例如，`<span>hi there</span>` 是一个不可替换的元素，文本“hi there”将由用户代理显示。这适用于 HTML 中的段落、标题、表格单元格、列表和几乎所有其他内容。

除了替换和非替换元素外，CSS 还使用了其他两种基本类型的元素:块级和行内级。还有更多的显示类型，但这些是最基本的，

1. 块级元素（block）：生成一个元素框，该元素框(默认情况下)填充其父元素的内容区域，并且不能在其两侧有其他元素。换句话说，它在元素框之前和之后生成“break”。HTML 中最常见的块元素是 p 和 div。被替换的元素可以是块级别的元素，但通常不是。

2. 行内元素（inline）：在一行文本中生成一个元素框，并且不会破坏该行的流。最好的内联元素示例是 HTML 中的 a 元素。这些元素不会在它们自己之前或之后生成“break”，因此它们可以出现在另一个元素的内容中，而不会中断它的显示。

   请注意，虽然“块”和“行内”的名称与 HTML 中的块级和内联级元素有很多相同之处，但它们之间有一个重要的区别。在 HTML 中，块级元素不能出现在行内元素中。但是 CSS不限制他们的显示方式，相互之间可以嵌套。

## 1.3 将 CSS 和 HTML 结合在一起 

我提到过 HTML 文档存在一个固有结构，这一点值得重复一下。实际上有个旧网页开发遗留的问题：我们太多人忘记了文档是应该有一个内在结构的，这与视觉上的结构是完全不同的。我们急于在 Web 上创建看起来最酷的网页，我们改造转换、修饰装点，全然忽视了页面应该包含具有一些结构意义的信息。

这种结构是 HTML 和 CSS 之间关系所固有的组成部分，没有它，关系就不会存在。为了更好地理解这种结构，我们把下面这个示例的 HTML 文档拆解来看：

```html
<html>
  <head>
    <title>Eric's World of Waffles</title>
    <meta http-equiv="content-type" content="text/html; charset=utf-8" />
    <link rel="stylesheet" type="text/css" href="sheet1.css" media="all" />
    <style type="text/css">
      /* These are my styles! Yay! */
      @import url(sheet2.css);
    </style>
  </head>
  <body>
    <h1>Waffles!</h1>
    <p style="color: gray;">
      The most wonderful of all breakfast foods is the waffle—a ridged and cratered slab of home-cooked, fluffy goodness
      that makes every child's heart soar with joy. And they're so easy to make! Just a simple waffle-maker and some
      batter, and you're ready for a morning of aromatic ecstasy!
    </p>
  </body>
</html>
```

### 1.3.1 link 标签

```html
<link rel="stylesheet" type="text/css" href="sheet1.css" media="all" />
```

### 1.3.2 style元素

style元素也是一种映入样式表的方式，直接写在文档中

```html
<style type="text/css">...</style>
```

### 1.3.3 #import指令

与link一样，web浏览器遇到@import指令时会加载外部样式表，使用其中的样式渲染html，二者的区别是 @import用在style元素内部，而且必须放在其他css规则前面，否则不起作用

```html
<style type="text/css">
@import url(styles.css) /* @import放在开头*/
    h1 {color:gray;}
</style>
```

