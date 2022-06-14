# 引言

最近因建[网盘网站](https://pan.vrchat.yexca.xyz/)了解了一下 Markdown，发现这玩意非常好用，于是写一份学习笔记

可以通过[在线编辑器 ](https://markdown.com.cn/editor/)边看边学，也可下载一些[编辑器](https://markdown.com.cn/tools.html)

个人编写Markdown的工具为 [Typora](https://www.typora.io/)

复习可以去看官方的速查表 [Markdown 语法速查表](https://markdown.com.cn/cheat-sheet.html)

# 标题

创建一个标题，仅需`#`+`空格`+`标题文字`，一共有六级，对应 HTML 的 h1~h6

例如以下代码

```markdown
# 这是一级标题
## 这是二级标题
### 这是三级标题
······
###### 这是六级标题
```

效果如下

# 这是一级标题<!-- {docsify-ignore} -->

## 这是二级标题<!-- {docsify-ignore} -->

### 这是三级标题<!-- {docsify-ignore} -->

······

###### 这是六级标题<!-- {docsify-ignore} -->

# 换行

仅需在上一行末尾加上俩个以上空格后回车即可，有些编辑器可直接换行

例如以下代码

```bash
这是第一行  //这里有俩空格  
这是第二行
```

效果如下

这是第一行  //这里有俩空格

这是第二行

# 斜体 & 粗体

斜体为文本前后加一个`*`，粗体为文本前后加俩`**`

例如以下代码

```markdown
*这是斜体*  
**这是粗体**  
***这是斜体加粗体***
```

效果如下

*这是斜体*

**这是粗体**

***这是斜体加粗体***

# 引用

创建引用区块仅需在段首添加`>`+`空格`+`内容`

例如以下代码

```markdown
> 这是一级引用
>> 这是二级引用
>>> 这是三级引用 
```

效果如下

> 这是一级引用
>
> > 这是二级引用
> >
> > > 这是三级引用

# 列表

可以创建有序列表和无序列表

## 有序列表

在列表项前添加`数字`+`.`+`空格`+`内容`即可

例如以下代码

```markdown
1. 第一项
2. 第二项
3. 第三项
```

效果如下

1. 第一项
2. 第二项
3. 第三项

## 无序列表

使用`+`，`-`或`*`+`空格`+ `内容`即可，但请不要混用 ~~(为了兼容性)~~

子项可以使用`四个空格`或一个`TAB`然后用父项格式即可

例如以下代码

```markdown
* 第一项
    * 第一项子一项
    * 第一项子二项
        * 第一项子二项子一项
* 第二项
* 第三项
```

效果如下

- 第一项
  - 第一项子一项
  - 第一项子二项
    - 第一项子二项子一项
- 第二项
- 第三项

# 代码

## 单行

将要变为代码的内容放在"\`"中即可，如果代码中有"\`"，请使用"``"

例如以下代码

```markdown
`将此内容变为代码块`
``此内容中含有'`'哦~``
```

效果如下

`将此内容变为代码块`

``此内容中含有'`'哦~``

## 代码块

可以通过将每一行缩进四个空格或一个`TAB`

或者上下行"\`\`\`"包围，要使用高亮，请在上方"\`\`\`"后写上语言类型

例如以下代码

~~~markdown
// 这是使用缩进的C代码
    include<stdio.h>
    int main(void)
    {
        printf("Hello World");
    }
// 这是使用```的C代码
``` C
include<stdio.h>
int main(void)
{
    printf("Hello World");
}
```
~~~

效果如下

// 这是使用缩进的 C 代码

```
include<stdio.h>
int main(void)
{
    printf("Hello World");
}
```

// 这是使用"\`\`\`"的 C 代码

```c
include<stdio.h>
int main(void)
{
    printf("Hello World");
}
```

注：第一种(缩进)部分Markdown编辑器不支持

# 分割线

在单独一行使用三个及以上的`*`，`-`或`_`即可

例如以下代码

```markdown
***
--------
_____
```

效果如下

------

------

------

# 链接

## 简易链接

直接将链接或邮箱地址使用` <>` 括起来即可

例如以下代码

```markdown
<https://yexca.xyz>  
<yexcano@gmail.com>
```

效果如下

<https://yexca.xyz>

<yexcano@gmail.com>

## 自定义文字的链接

`[超链接显示名](超链接地址 "超链接title")`，其中 `"超链接title"` 可以不填

例如以下代码

```markdown
[yexca的博客](https://yexca.xyz)
[yexca的博客](https://yexca.xyz "其实是yexca和Hiyoung的博客")
```

效果如下

[yexca 的博客](https://yexca.xyz/)

[yexca的博客](https://yexca.xyz "其实是yexca和Hiyoung的博客")

## 引用类型链接

例如以下代码

```markdown
[blog]: https://yexca.xyz
[contact]: https://t.me/yexca

这是我的[个人博客][blog]，有问题可以[联系我][contact]
```

效果如下

[blog]: https://yexca.xyz
[contact]: https://t.me/yexca

这是我的[个人博客][blog]，有问题可以[联系我][contact]

# 图片

## 插入图片

`![图片alt](图片链接 "图片title")`，其中‘图片 alt’为当图片加载失败时显示的内容，‘图片 title’为鼠标放图片上显示的内容

注意：部分Markdwon编辑器不支持`图片title`

例如以下代码

```markdown
![图片](https://yexca.xyz/wp-content/uploads/2022/01/1636215131487-1024x560.jpg)
```

效果如下

![图片](https://yexca.xyz/wp-content/uploads/2022/01/1636215131487-1024x560.jpg)

## 图片包含链接

使用链接的语法，将图片放在‘[]’里即可

例如以下代码

```markdown
[![图片](https://yexca.xyz/wp-content/uploads/2022/01/1636215131487-1024x560.jpg)](https://www.pixiv.net/artworks/82542737)
```

效果如下

[![图片](https://yexca.xyz/wp-content/uploads/2022/01/1636215131487-1024x560.jpg)](https://www.pixiv.net/artworks/82542737)

# 转义字符

如果有不想被 Markdown 格式化的字符，只需要在前方加上‘\’即可

例如以下代码

```markdown
我想打出*但这会被斜体*  
加上转移符\*后面就不会斜体\*而且可以显示
```

效果如下

我想打出*但这会被斜体*

加上转移符 * 后面就不会斜体 * 而且可以显示

# 内嵌 HTML

直接使用即可，以缩略标签为例

例如以下代码

```markdown
<details>
    <summary>
        点我试试
    </summary>
被发现啦
</details>
我可以用Markdown**变粗**，也可以同时用HTML*变斜*
```

效果如下

<details>
    <summary>
        点我试试
    </summary>
被发现啦
</details>

我可以用Markdown**变粗**，也可以同时用HTML*变斜*

# 表格

使用三个或多个`-`创建每列标题，使用`|`分割每列，使用`:`以左，右或居中对齐 (非必须)

例如以下代码

```markdown
|标题|内容|备注|
|:---|:---:|---:|
|左对齐|居中|右对齐|
```

效果如下

| 标题   | 内容 |   备注 |
| :----- | :--: | -----: |
| 左对齐 | 居中 | 右对齐 |

**注意**：不可以在表格中添加标题，引用，列表，图像或 HTML 标签等

# 删除线

在要删除的内容前后添加`~~`

例如以下代码

```markdown
我永远喜欢~~战争文学博士~~Warma
```

效果如下

我永远喜欢~~战争文学博士~~ Warma

# 任务列表

使用`-`+`空格`+`[ ]`或`[x]`+`空格`+`内容`

例如以下代码

```markdown
- [ ] 这个没完成呢
- [x] 这个完成啦 
```

效果如下

- [ ] 这个没完成呢
- [x] 这个完成啦 

# 使用 Emoji 表情

## 复制粘贴

多数情况可直接复制 [Emojipedia](https://emojipedia.org/) 上的表情直接粘贴，请确保网页编码为’UTF-8‘

## 使用表情符号简码

这个需要 Markdown 应用程序支持，以冒号`:`开头和结尾

可以通过[表情符号简码列表](https://gist.github.com/rxaviers/7360908)查询

例如以下代码

```markdown
:blush:,:smiley:
```

效果如下

😊,😃

# 脚注

例如以下代码

```markdown
这里引用了维基百科[^1]，这里引用了Github[^2]。
也可以使用英文，但不能用空格或TAB[^yexca]

[^1]: 这里可以使用文字，然后会在上方相应位置出现
[^2]: 或者使用链接[Github](https://github.com)
[^yexca]: [个人主页](https://git.yexca.xyz)
```

这里引用了维基百科[^1]，这里引用了Github[^2]。
也可以使用英文，但不能用空格或TAB[^yexca]

[^1]: 这里可以使用文字，然后会在上方相应位置出现
[^2]: 或者使用链接[Github](https://github.com)
[^yexca]: [个人主页](https://git.yexca.xyz)

**注意**：部分编辑器不支持

# 参考文章

[Markdown 官方教程](https://markdown.com.cn/)

[Markdown 学习](https://liangjunrong.github.io/other-library/Markdown-Websites/Markdown/Markdown-study.html)