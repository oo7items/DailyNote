## 为什么要发明JavaScript
1. 1995年前，验证表单都是服务器端做的事情，假设使用调制解调器28.8kbit/s上网时，验证需要时间会很长，也有可能返回验证失败需要重试，因此在复杂的网页中，这是非常不利的
2. 1995年，Brendan Eich发布了JavaScript客户端脚本语言，解决一些基本数据验证

## JavaScript实现
1. 核心（ECMAScript）
2. 文档对象模型 （DOM）
3. 浏览器对象模型 （BOM）

### 核心（ECMAScript）
1. ECMAScript，即**ECMA-262**定义的语言，并不局限于Web浏览器，Web浏览器只是ECMAScript实现可能存在的一种**宿主环境**（host environment）
2. 宿主环境提供ECMAScript的**基准实现**和**环境自身交互必须的扩展**，扩展（比如DOM）使用ECMAScript核心类型和语法，提供特定于环境的额外功能
3. 如果不涉及浏览器，ECMA-262到底定义了什么?
* 语法（一套规则，定义了JavaScript的语言结构，如何声明变量，赋值，计算值）
* 类型（原始值(基本类型)，对象）
* 语句 （向浏览器发出的命令，告诉浏览器要做什么）
* 关键字 
* 保留字 
* 操作符 （逻辑操作符 与 位操作符）
* 全局对象 （Global scope, js没有专门为后台任务启动的任何代码都将window作为其全局对象，比如Web Worker）
**web worker**：一个 worker 是使用一个构造函数创建的一个对象（例如 Worker()）运行一个命名的 JavaScript 文件——这个文件包含将在 worker 线程中运行的代码; **worker 运行在另一个全局上下文中，不同于当前的window**。因此，在 Worker 内通过 window 获取全局作用域（而不是self）将返回错误。
**保留字和关键字的区别**：
1. 关键字是JavaScript编程语言中的预定义标识符，用于表示**语言的结构和功能**。这些关键字具有固定的含义，不能被用作标识符（变量名、函数名等）。
2. 保留字是被保留的单词，但目前没有被用作关键字。它们没有特定的功能或含义，因此可以用作标识符。然而，由于将来可能会被JavaScript引入新的功能和语法，为了避免与可能的关键字冲突，最好不要将保留字用作标识符。

## ECMAScript版本
1. 第一版，删除所有浏览器特定的代码，外加少量细微的修改，支持Unicode标准(支持多语言)，**对象不得依赖平台**，这是修改的关键内容
2. 第二版，做了一些编校工作，主要是为了更新之后严格符合 ISO/IEC-16262的要求，并没有增减或改变任何特性
3. 第三版，更新了**字符串处理**、**错误定义**和**数值输出**，增加了对**正则表达式**、**新的控制语句**、**try/catch异步处理**的支持，更好的标准国家化做的少量修改，这版本意味着编程语言的时代到来
4. 第四版，在第三版基础上完全定义了一门新语言，包括**类型变量**、**新语句和数据结构**、**真正的类**和**经典的继承**，以及**操作数据**的手段，TC39委员会子委员提出跳度太大，因此在正式发布前被放弃，转而在第五版中发布
5. 第五版，厘清第三版存在的歧义，增加新功能，新功能包括**原生的解析**和**序列化JSON数据**、**方便继承**和**高级属性定义**的方法，增强ECMAScript引擎和解释和执行代码能力的**严格模式**
（厘是极小的数量，清是清楚，两者合起来表示从最细小的方面都搞得条条有序清清楚楚了）

6. 第六版，包含了大概这个规范有史以来最重要的一批增强特性，ES6正式支持了**类、模块、迭代器、生成器、箭头函数、期约、反射、代理**和众多新的数据类型

7. 第七版，包含少量语法层面的增强，如Array.prototype.includes和指数操作符

8. 第八版2017.6，主要增加了**异步函数**（async/await）、SharedArrayBuffer及Atomics API，以及Object.values() / Object.entries() / Object.getOwnPropertyDescriptions() 和字符串填充方法，另外明确支持对象字面量最后的逗号。

9. 第九版2018.6，这次修订包括异步迭代、剩余和扩展属性、一组新的正则表达式特性、Promise finally()，以及模板字面量修订
10. 第10版2019.6，增加了Array.prototype.flat() / flatMap() 、 String.prototype.trimStart() / trimEnd() 、 Object.fromEntries() 方法，以及Symbol.prototype.description属性，明确定义了Function.prototype.toString()的返回值固定了Array.prototype.sort()顺序，解决JSON字符串兼容的问题，定义了catch子句的可选绑定

#### 什么是unicode
1. 统一码（Unicode），也叫万国码、单一码，由统一码联盟开发，是计算机科学领域里的一项业界标准，包括字符集、编码方案等
2. 统一码是为了解决传统的字符编码方案的局限而产生的，它为每种语言中的每个字符设定了统一并且唯一的二进制编码，以满足**跨语言**、**跨平台**进行**文本转换**、处理的要求

## ECMAScript符合性是什么意思?
支持ECMA-262阐述了什么是ECMAScript符合性。要成为ECMAScript实现，必须满足下列条件
1. 支持ECMA=262中描述的所有，类型、值、对象、属性、函数、程序语法与语义
2. 支持Unicode字符标准
3. 增加ECMA-262中未提及的，额外的类型、值、对象、属性和函数，这些额外的内容指的是规范中未给出的新对象和对象的新属性
4. 支持ECMA-262中没有定义的程序和正则表达式语法（允许修改和扩展内置的正则表达式特性）  

以上条件为实现开发者基于ECMAScript开发语言提供了**极大的权限和灵活度**，也是其广受欢迎的原因之一

## DOM
1. 文档对象模型（DOM，Document Object Model）是一个应用程序接口（API），用于在HTML中使用扩展的XML。DOM将整个页面抽象为一组分层节点。HTML或XML页面的每个组成部分都是一种节点，包含不同数据。  
2. DOM通过创建表示文档的树，让开发者可以随心所欲地控制网页的内容和结构。使用DOM API，可以轻松地删除、添加、替换、修改节点。

### 为什么 DOM是必须的?
1. 开发者可以做到**不刷新页面而修改页面外观和内容**，代表了web技术的一个巨大进步，但也暴露了很大的问题。由于网景(netSpace)和微软采用不同思路开发DHTML，**开发者写一个HTML页面就可在任何浏览器中运行的好日子就此结束**。
2. 为了保持web跨平台的本性，必须要做点什么，不然会导致web四分五裂，开发者面相浏览器开发页面，这非常糟糕，这时W3C万维网联盟开始了指定DOM标准的进程

### DOM级别
1. 1998.10，DOM Level1 成为W3C的推荐标准，这个规范由两个模块组成：DOM Core 和 DOM HTML，前者提供了一种映射XML文档，从而方便访问和操作文档任意部分的方式；后者扩展了前者，并增加了特定于HTML的对象和方法。
注意，**DOM并非只能通过JavaScript访问**，而且确实被其他很多语言实现了。不过**对于浏览器来说，DOM就是使用ECMAScript实现的**，如今已经成为JavaScript语言的一大组成部分。

2. DOM Level1的目标是映射文档结构，而DOM Level2的目标则宽泛得多。这个对最初DOM的扩展增加了对**鼠标和用户界面事件、范围、遍历（迭代DOM节点的方法）**的支持，而且通过对象接口支持了层叠样式表（CSS）。DOM Level1中的DOM Core也被扩展以包含对XML命名空间的支持。

DOM Level2新增了以下模块，以支持新的接口
1. DOM视图：描述追踪文档不同视图（入应用CSS样式前后的文档）的接口。
2. DOM事件：描述事件及事件处理的接口
3. DOM样式：描述处理元素CSS样式的接口
4. DOM遍历和范围：描述遍历和操作DOM树的接口

3. DOM Level3，进一步扩展了DOM，增加了以统一的方式**加载和保存文档**的方法（包含在一个叫DOM Load and Save的新模块中），还有**验证文档**的方法（DOM Validation）。在Level3中，DOM Core经过扩展支持了所有XML1.0的特性，包括XML Infoset、XPath 和 XML Base。  
目前W3C不再按照Level来维护DOM了，而是作为**DOM Living Standard**来维护，其快照称为DOM4。DOM4新增的内容包括替代**Mutation Events**的**Mutation Observers**。  
注意，在阅读关于DOM的资料时，你可能会看到DOM Level0的说法。注意，并没有一个标准叫"DOM Level 0"，这只是DOM历史中的一个参照点。**DOM Level0可以看作IE4和Netscape Navigator4中最初支持的DHTML**。

### 其他 DOM
除了DOM Core 和 DOM HTML接口，有些其他语言也发布了自己的DOM标准。下面列出的语言是基于XML的，每一种都增加了该语言独有的DOM方法和接口：
1. 可伸缩矢量图（SVG，Scalable Vector Graphics）
2. 数学标记语言（MathML，Mathematical Markup Language）
3. 同步多媒体集成语言（SMIL，Synchronized Multimedia Integration Language）
此外还有一些语言开发了自己的DOM实现，比如Mozilla的XML用户界面语言（XUL，XML User Interface Language）。不过，只有前面列表中的语言是W3C推荐标准


## BOM
IE3和Netscape Navigator3提供了浏览器对象模型（BOM）API，用于支持访问和操作浏览器的窗口。使用BOM，开发者可以操控浏览器显示页面之外的部分。而**BOM它是一个没有标准的JavaScript实现** 。HTML5改变了这个局面，这个版本的**HTML以正式规范的形式涵盖了尽可能多的BOM特性**。由于HTML5的出现，之前很多与BOM有关的问题都迎刃而解了。  
总体来说，BOM主要针对浏览器窗口和子窗口（frame），不过人们通常会把任何特定于浏览器的扩展都归在BOM的范畴内。比如，下面就是这样一些扩展：
1. 弹出新浏览器窗口的能力；
2. 移动、缩放和关闭浏览器窗口的能力
3. navigator 对象，提供关于浏览器的详尽信息；
4. location对象，提供浏览器加载页面的详尽信息；
5. screen对象，提供关于用户屏幕分辨率的详尽信息；
6. performance（性能）对象，提供浏览器内存占用、导航性行为和时间统计的详尽信息；
7. 对cookie的支持；
8. 其他自定义对象，如XMLHttpRequest 和 IE 的ActiveXObject  
因为很长时间内都没有标准，所以**每个浏览器都会给它们定义自己的属性和方法**。现在有了HTML5，BOM的实现细节应该会日趋一致。

## JavaScript版本
注意 Netscape/Mozilla仍然沿用这种版本方案。而IE的JScript有不同的版本号规则。这些JScript版本与上表提到的JavaScript版本并不对应。此外，**多数浏览器对JavaScript的支持，指的是实现ECMAScript和DOM的程度**。

## 小结
JavaScript是一门用来与网页交互的脚本语言，包含一下三个组成部分。
1. ECMAScript：由ECMA-262定义并提供核心功能。
2. 文档对象模型（DOM）：提供与网页内容交互的方法和接口。
3. 浏览器对象模型（BOM）：提供与浏览器交互的方法和接口。
JavaScript的这三个部分得到了五大Web浏览器（IE、Firefox、Chrome、Safari和Opera）不同程度的支持。浏览器对DOM的支持各不相同，但对Level3的支持日益趋于规范。HTML5中收录的BOM会因浏览器而异，不过开发者仍然可以假定存在很大一部分公共特性。

#### xml 和 html 的区别
1. html 是用来显示数据的； xml 是用来描述数据、存放数据的，可以作为持久化介质。
2. Html 将数据和显示结合在一起，在页面中把这数据显示出来；
3. xml 则将数据和显示分开。 XML 被设计用来描述数据，其焦点是数据的内容。 HTML 被设计用来显示数据，其焦点是数据的外观。




ECMA-SCRIPT 262 基准来定义
Web 浏览器 是ECMASCRIPT实现可能存在的一种宿主环境
ECMAScript的基准实现和与环境自身交互必须的扩展