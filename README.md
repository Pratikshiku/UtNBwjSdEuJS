> [点我下载源码](https://www.notmaker.com/detail/cd64eee5b28a432596bd4ecda8e30364/ghp20250304) 


> 或查看我的个人简介下载源码。

> 支持定制、讲解、修改、远程调试


### 一、相关技术
`Java`、`JavaSwing`

### 二、相关软件（列出的软件其一均可运行）
- `IDEA`
- `Eclipse`
- `Visual Studio Code(VScode)`

![image.png](https://store.ptcc9.top/notmaker/user_upload/ba15bc64d0b24c178659372c9c4386bd/2024-02-28%2000:40:58_image.png)

程序分为两个页面，由两个JFrame组成，页面之间可以通过点击按钮来进行跳转。

欢迎界面：JLabel显示标题，JButton用来跳转到下一个界面。
操作界面：由一个JTextArea，数个JButton，组成。

用户可以通过点击相应的按钮，向公共变量text中添加字符串。
例如：
用户点击“1”按钮，则向text中追加一个数字1，若点击”+“按钮，则向text中追加一个+。
每次监听到用户的点击，不仅更新text，同时会把text中的字符串显示在textArea中。

若用户点击了”=“号按钮，则会把text中的内容拷贝到另一个公共字符串中即realFormula。
拷贝规则如下：
1. 数字不做改变。
2. 符号进行替换，即： + => !        - => @      * => #    / => %

替换字符串是因为，在java编程语言中。字符串的repleaceAll语句无法识别对应的加减乘除符号。
所以在后续的运算中，应该避免这些符号的出现。

替换结束后，调用Formula.java中的计算方法进行计算。
由于组合表达式存在优先级的问题。
我的做法是：
识别字符串中优先级更高的乘法和除法运算，将其抽离计算，直到不存在任何高优先级的运算简式，才计算优先级低的加减算式。

例如：
要计算   1 + 2 * 3 - 1
则首先识别算式中的 2 * 3 部分并抽离。
计算 2 * 3 的结果为 6。
随即，使用 6 替换原来 2 * 3 的位置。 
之后表达式会变为：   1 + 6 - 1
这时，算式中已没有乘法或除法运算。
则按照顺序计算加减法即可。
