---
layout  : post
title   : 学习 VI 编辑器
---

vim 常用的有两种模式：Normal 和 Insert ，打开文件，默认进入的是 Normal 模式

键盘组合命令何其多，使用多时，还是停留在 h, j, k, l 的程度，翻出旧文，发现好多命令如同初见。记下，勉励之

## 移动光标

### 上下移动

	j           向下移动，一行，光标不会发生左右移动
	+ or enter  向下移动，光标会移动到下一行的行首
	k           向上移动，一行，光标不会发生左右移动
	-           向上移动，光标会移动到上一行的行首
	H           移动光标到当前屏幕的第一行
	L           移动光标到当前屏幕的最后一行
	M           移动光标到当前屏幕的中间行
	nH          移动光标到当前屏幕的第一行的后n行
	nL          移动光标到当前屏幕的最后一行的前n行
	gg          移动到当前文档的第一行
	G           移动到当前文档的最后一行
	nG          移动到当前文档的第n行
	h, j, k, l  前面可以跟阿拉伯数字，用以移动多行或多个字符
	(           移动到当前句子的开始
	)           移动到下一句的开始
	{           移动到当前段落的开始
	}           移动到下一个段落的开始


### 左右移动


	h           向左移动 
	l           向右移动
	0           数字0 移动光标所在行的行首
	^           移动光标到当前行的第一个非空字符上
	n|          移动光标到当前行的第n列
	$           移动光标所在行的行尾
	b           向后移动，一次移动一个英文单词或英文符号，
	B           向后移动，一次移动一个英文单词，跳过英文符号
	e
	w           向前移动，一次移动一个英文单词或英文符号
	E
	W           向前移动，一次移动一个英文单词，跳过英文符号
	e, E        光标落在单词最后一个字符上
	b, B, w, W  光标落在单词第一个字符上


## 进入插入模式


	i           光标所在字符的前面插入 (insert)
	a           光标所在字符的后面插入 (append)
	o           小写的 o 激活光标所在行的下一行
	O           大写的 o 激活光标所在行的前一行


## 删除

	s           删除光标所在位置的后一个字符，并进入插入模式
	S, cc       删除整行,进入插入模式
	dd          删除一行
	2dd         删除两行
	x           删除光标所在位置之后的字符
	X           删除光标所在位置之前的字符
	dw          删除光标所在位置的到下一个空格之间的字符包括该空格 
	            如果想保留空格使用 dE            
	cw          删除光标所在位置的后一个单词，并且激活插入模式
	cb          删除光标所在位置的前一个单词，并且激活插入模式
	              如果是中文，则会删除到标点符号前的所有单词。
	c0          删除从光标到该行的开始
	c$          删除从光标到该行的结束
	D           删除光标所在位置到该行的行尾
	c$, C       删除光标所在位置到该行的行尾，进入插入模式


## 替换操作

	r           替换单个字符
	R           进入替换模式，输入的字符会替换原有的字符，除非按ESC退出


## 拷贝和粘帖


	yy          拷贝一行，在命令模式下输入p，粘帖拷贝的文本
	            Y效果等同于yy
	yw          拷贝光标所在位置到下一个空格之间的字符
	y0          拷贝光标所在位置到行首之间的字符
	y$          拷贝光标所在位置到行尾之间的字符
	p           会将缓冲区的文本插入到光标所在位置的下一行中，
	            如果缓冲区为空，则插入空行
	P           插入文本到光标所在位置的前一行，单独一行


## 撤销操作


	u           撤销以前的操作
	ctrl + r    恢复撤销   


## 翻屏


	ctrl + F    scroll forward one screen
	            向下移动一屏           
	ctrl + B    scroll backward one screen
	            回退一屏
	ctrl + D    scroll forward half screen down
	            向下移动半屏
	ctrl + U    scroll backward half screen up
	            回退半屏
	z + Enter   Move current line to top of screen and scroll
	            移动当前行到屏幕的最顶端
	z.          Move current line to center of screen and scroll
	            移动当前行到屏幕的中央         
	z-          Move current line to bottom of screen and scroll
	            移动当前行到屏幕的最底部
	[line]z     z前面可以跟数字，移动光标到指定的行号


## 其它


	ctrl + ~    大写字符转换为小写，小写字符转换为大写
	ctrl + l    重绘、刷新当前屏幕
	.           重复上一次所执行的操作