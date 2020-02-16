# 一、标题

## 1.使用 # 号标记



```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

# 二、段落

> 段落的换行是使用两个以上空格加上回车。

## 1.字体



```markdown
*斜体文本*

**粗体文本**

***粗斜体文本***
```

## 2.分割线

> 在一行中用三个以上的星号、减号、底线来建立一个分隔线。



```markdown
***

---

___
```

## 3.删除线

> 在文字的两端加上两个波浪线 **~~**



```markdown
~~BAIDU.COM~~
```

## 4.下划线

> 可以通过 HTML 的 **<u>** 标签来实现



```markdown
<u>带下划线的内容</u>
```

<u>带下划线的内容</u>

## 5.脚注

> 脚注是对文本的补充说明



```markdown
格式： [^要注明的文本]
例：
    需要注明的文本 [^MarkDown]。
    [^MarkDown]:Markdown 是一种轻量级标记语言。
```

需要注明的文本 [[1\]](#fn1)。

# 三、列表

> MarkDown 支持有序列表 和 无序列表

## 1.无序列表

> 无序列表使用星号(*****)、加号(**+**)或是减号(**-**)作为列表标记



```markdown
* 星号
+ 加号
- 减号
```

- 星号

- 加号

- 减号

## 2.有序列表

> 有序列表使用数字并加上 **.** 号来表示



```markdown
1. 第一项
2. 第二项
```

1. 第一项
2. 第二项

## 3.列表嵌套

> 列表嵌套只需在子列表中的选项添加四个空格即可



```markdown
1.parent1
    +p1-child1
    +p1-child2
2.parent2
    -p2-child1
    -p2-child2
```

1. parent1 
   - p1-child1
   - p1-child2
2. parent2 
   - p2-child1
   - p2-child2

# 四、区块

## 1.简单使用

> 1.在段落开头使用 **>** 符号 ，然后后面紧跟一个**空格**符号
>
> 2.区块是可以嵌套的



```markdown
> MarkDown

>> MarkDown
```

> MarkDown

> > MarkDown

## 2.区块与列表结合

> 1.区块中使用列表
>
> 2.列表中使用区块



```markdown
> 区块中使用列表
> 1. 有序
> + 无序
> 2. 有序
> - 无序

1. 列表中使用区块
    > 区块内容
    >> 区块内容
2. 列表中使用区块
```

> 区块中使用列表
>
> 1. 有序
>
> - 无序
>
> 1. 有序
>
> - 无序

1. 列表中使用区块

   > 区块内容
   >
   > > 区块内容

2. 列表中使用区块

# 五、代码

## 1.段落中的代码

> 用反引号把它包起来（**`**）



```markdown
`Markdown` 是一种轻量级标记语言。
```

`Markdown` 是一种轻量级标记语言。

## 2.代码块

> 1.使用 **4 个空格**或者一个**制表符（Tab 键）**
>
> 2.用 **```** 包裹一段代码，并指定一种语言（也可以不指定）



~~~markdown
```markdown
Markdown是一种轻量级标记语言。
```
~~~

显示：



```markdown
Markdown是一种轻量级标记语言。
```

# 六、链接

## 1.简单使用



```markdown
[链接名称](链接地址)
或者
<链接地址>

// 例：
[百度](www.baidu.com)
<www.baidu.com>
```

[百度](https://links.jianshu.com/go?to=www.baidu.com)

<[www.baidu.com](https://links.jianshu.com/go?to=http%3A%2F%2Fwww.baidu.com)>

## 2.高级链接

> 链接也可以用变量来代替，文档末尾附带变量地址



```markdown
百度[百度][1]
教育宝[教育宝][jyb]

[1]:www.baidu.con
[jyb]:https://www.jiaoyubao.cn/
```

百度[百度](https://links.jianshu.com/go?to=www.baidu.con)
 教育宝[教育宝](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.jiaoyubao.cn%2F)

# 七、图片

## 1.简单使用



```javascript
// 注：使用时去掉括号“()”前面的空格
![alt 属性文本]  (图片地址)
![alt 属性文本]  (图片地址 "可选标题")
```