关于CSS中display的32种写法
你知道回』字有四种写法，但你知道 display有 32种写法吗？今天我们一一道来，让你一次性完全掌握 display，从此再也不用对它发愁。

从大的分类来讲， display的 32种写法可以分为 6个大类，再加上 1个全局类，一共是 7大类：

外部值
内部值
列表值
属性值
显示值
混合值
全局值

外部值

所谓外部值，就是说这些值只会直接影响一个元素的外部表现，而不影响元素里面的儿子级孙子级元素的表现。

display: block;

这个值大家不陌生，我们最熟悉的

缺省就是这个值，最基本的块级元素，属于 css入门初学者都知道的概念，只要是容器类型的元素基本都是这个值。除之外，<div>之外，还有 <h1>到 <h6>， <p>， <form>， <header>， <footer>， <section>， <article>天生都是这个值。


display: inline;

这个值大家也不陌生，行内元素嘛，只要是个行内元素都是这个值，最典型的是 ，还有 ， ，以及古代 html语言当中的 ， 都属于这一类型。

display: run-in;

这个值有点奇怪，通常没人用它，但你可以知道它。因为除了 IE和 Opera支持它以外，其他所有主流浏览器包括 Chrome, Safari, Firefox全都对它置若罔闻。这东西说白了也没什么神秘，它的意思就是说如果我们命令一个元素 run-in，中文意思就是『 闯入』！那么这个元素就直接闯入下一行。比如说这样：

写起来大概就是这样：



aaa
bbb
.a {
font-size: 36px;
display: run-in;
}


这有什么用呢？我们拿 span设置 font-size一样可以实现这个效果，就让 IE自己跟自己玩去吧！说实话，在人力资源如此宝贵的今天， IE的产品经理不知脑子是不是进水了，不派工程师去实现那么多比这重要的多得多的特性，却花时间做这么个没用的玩意儿，难道工程师的时间不是金钱吗？难怪市场占有率连年下滑。

内部值

谈完了外部值，我们来看看内部值。这一组值比较有意思了，在 css3如火如荼的今天，你要玩不转这些值，怕是哪儿也找不到工作的。内部值主要是用来管束自己下属的儿子级元素的排布的，规定它们或者排成 S形，或者排成 B形这样的。

display: flow;

含义不清，实验室阶段产品， Chrome不支持。如果还不够说服你暂时不要碰它的话，试着理解以下英文原文：

If its outer display type is inline or run-in, and it is participating in a block or inline formatting context, then it generates an inline box. Otherwise it generates a block container box.display: flow-root;

不同于刚才谈到的 flow，现在用 flow-root的渐渐多起来了，因为它可以撑起被你 float掉的块级元素的高度。外容器本来是有高度的，就像这样：




<div class="container container1">
<div class="item"></div>
Example one
</div>
.container {
border: 2px solid #3bc9db;
border-radius: 5px;
background-color: #e3fafc;
width: 400px;
padding: 5px;
}
.item {
height: 100px;
width: 100px;
background-color: #1098ad;
border: 1px solid #0b7285;
border-radius: 5px;
} 结果因为你想让那一行字上去，于是你给 .item加了一个 float:left;结果就成这样了，外容器高度掉了，这不是很多人常犯的错误吗？


现在我们给 .container加上 display:flow-root;再看一下：


喏，外容器高度又回来了，这效果是不是杠杠的？

那位同学说，我们用 clear:both;不是一样可以达到这效果吗？


.container::after {
content: '';
clear: both;
display: table;
}


小明，请你出去！我们在讲 display:flow-root;，不是在讲 clear:both;！

display: table;

这一个属性，以及下面的另外 8个与 table相关的属性，都是用来控制如何把 div显示成 table样式的，因为我们不喜欢 这个标签嘛，所以我们想把所有的

标签都换成

标签。有什么好？无非就是能自动换行而已，但其实你完全可以做一个

标签，把它全都替换成 display:block;也可以自动折行，只不过略微麻烦而已。


关于 display:table;的详细用法，大家可以参考这篇文章，这里就不细说了。

display: flex;

敲黑板，划重点！作为新一代的前端工程师，这个属性你必须烂熟于胸衣中，哦，错了，是胸中。 display:flex;以及与它相关联的一系列属性： flex-direction, flex-wrap, flex-flow, justify-content, align-items, align-content，并且包括所有这些属性的取值，都是你需要反复研磨的。 2009年诞生的这个属性可以说是不亚于 css界一场蒸汽机诞生一样的工业革命，它的诞生标志着马车一样的 float被彻底抛进历史的垃圾堆。

关于它的详情，会中文的可以参考阮一峰的这篇文章，但我认为，格式编排的更好还是 csstrick上的这篇文章。没有一张图能完整地展现 flex的神韵，就放这张我比较喜欢的图片吧：


display: grid;

会 flex很吊吗？会 grid更吊哦！也许这就是下次前端面试的重点哦！


grid布局，中文翻译为 网格布局。学习 grid布局有两个重点：一个重点是 grid布局引入了一个全新的单位： fr，它是 fraction（ 分数）的缩写，所以从此以后，你的兵器库里除了 px, em, rem, 百分比这些常见兵器以及 vw, vh这些新式武器之外，又多了一样旁门暗器 fr，要想用好 grid，必须充分掌握 fr。另一个重点是 斜杠操作符，这可不是 分数哦。它表示的是 起始位置和 结束位置。比如说 3/4，这可不是 四分之三的意思，这是指一个元素从第 3行开始，到第 4行结束，但又不包括第 4行。

同样，与 grid相关联的也有一大堆旁门属性，是在学习 display:grid;的同时必须掌握的。包括 grid, grid-column-start, grid-column-end, grid-row-start, grid-row-end, grid-template, grid-template-columns, grid-template-rows, grid-template-areas, grid-gap, grid-column-gap, grid-row-gap, grid-auto-columns, grid-auto-rows, grid-auto-flow, grid-column, grid-row。不能详述，关于这个写起来又是一大篇文章。详情还是参考csstrick上这篇文章，讲得非常细致非常清楚。

display: ruby;

ruby这个取值对于我们亚洲人来说其实是非常有用的一个东西，但是目前除了 Firefox以外其它浏览器对它的支持都不太好。简而言之， display:ruby;的作用就是可以做出下面这样的东西：


很好的东西，对吧？如果可以用的话，对我国的小学教育可以有极大的促进。但可惜我们现在暂时还用不了。

ruby这个词在英语里的意思是 红宝石，但在日语里是 ルビ，翻译成中文是 旁注标记的意思，我们中文的旁注标记就是汉语拼音。可以想见，这个标准的制定者肯定是日本人，如果是我们中国人的话，那这个标签就不是 ruby，而是 pinyin了。还有一个 ruby语言，发明者也是一个日本人，和 html里这个 ruby是两码事，不要搞混了。

ruby的语法大致如下：


display: subgrid;

2015年 8月 6日， W3C的级联样式单（ CSS）工作组（ CascadingStyleSheetsWorkingGroup）发布了 CSS网格布局模块第一级（ CSSGridLayoutModuleLevel1）的工作草案。在这个草案里规定了上一节我们讲到的 display:grid;的方案。而 display:subgrid;是属于 2017年 11月 9日发布的非正式的CSS网格布局模块第二级的内容。所以这是一个非常新的草案，并且围绕它的争议从来也没有断过。

subgrid总的思想是说大网格里还可以套小网格，互相不影响。但如果 grid里可以再套 subgrid的话，那我 subgrid里还想再套 subgrid怎么办？ subsubgrid吗？况且，到底是 grid:subgrid;还是 display:subgrid;这个也没有达成共识，关于此一系列的争议，感兴趣的同学可以看看这篇文章，英语好的可以看这篇。

列表值

display: list-item;

display:list-item;和 display:table;一样，也是一帮痛恨各种 html标签，而希望只使用

来写遍一切 html的家伙搞出来的鬼东西，实际使用极少，效果就是这样：



看，你用

能实现的效果，他可以用实现出来，就是这个作用。


属性值

属性值一般是附属于主值的，比如主值里设置了 display:table;，就可以在子元素里使用 display:table-row-group;等等属性，不过并不绝对。关于它们的作用，主要参考主值就够了。

display: table-row-group;

详情参考display: table;。

display: table-header-group;

详情参考display: table;。

display: table-footer-group;

详情参考display: table;。

display: table-row;

详情参考display: table;。

display: table-cell;

详情参考display: table;。这个属性有必要详细说说，因为它完全可以单独应用，用在高度不固定元素的垂直居中上，详情请见张鑫旭的这篇文章。效果如下图所示：


display: table-column-group;

详情参考display: table;。

display: table-column;

详情参考display: table;。

display: table-caption;

详情参考display: table;。

display: ruby-base;

详情参考display: ruby;。

display: ruby-text;

详情参考display: ruby;。

display: ruby-base-container;

详情参考display: ruby;。

display: ruby-text-container;

详情参考display: ruby;。

显示值

MDN里把它叫做values（ 盒子值），我把它叫做 显示值，主要是为了便于理解。

display: contents;

这大概是 2018年年初最令人喜大普达的一件大事了：Chrome 65版本终于要支持display: contents;了！ Firefox早就支持了，而 Chrome直到现在才开始支持，这么重要的特性，它到底有什么功能呢？结果恐怕会令你大失所望。原来的布局是这样的：


你给中间那个 div加上 display:contents;之后，它就变成这样了：


这就是 display:contents;的作用，它让子元素拥有和父元素一样的布局方式，仅此而已。

display: none;

这么著名的值还用多说吗？

混合值

display: inline-block;

关于 display:inline-block;的作用恐怕只要做过 3天以上前端的工程师都应该知道。什么也不说了，上一张著名的图片作总结吧：


display: inline-table;

你要能理解 inline-block，你就能理解 inline-table。在行内显示一个表格，就像这样：


display: inline-flex;

这个就不用多说了吧？跟上面一样，在行内进行弹性布局，参考display: flex;。

display: inline-grid;

同上，在行内进行网格布局，参考display: grid;。

全局值

这些值不是 display属性的专利，几乎其它任意属性都可以用，列在这里凑个数。

display: inherit;

继承父元素的 display属性。

display: initial;

不管父元素怎么设定，恢复到浏览器最初始时的 display属性。

display: unset;

unset混合了 inherit和 initial。如果父元素设值了，就用父元素的设定，如果父元素没设值，就用浏览器的缺省设定。直接看图最明白：


总结

以上就是在 css里 display的 32种写法。谈了这么多，不知道你记住了多少呢？其实，单纯理解每一个 display属性的取值都不难，难的是融会贯通，在恰当的地方运用恰当的值，毕竟我们的目的是为了把代码写短，而不是把代码写长。如果你怕记不太清的话，就请你收藏这篇小文，也许将来的某一天，你会用得着。
