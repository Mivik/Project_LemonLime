# 比赛

在左上角选中 `试题` ，进入试题编辑。

对 Lemon 而言，一场比赛分为 2 个部分：题目，与选手。

## 创建比赛

假设你将创建一个叫 `contest` 的比赛。

去 `文件 > 新建比赛` ，在 `比赛标题` 写上你的比赛的名字，在 `保存文件名` 写上你想保存的位置（这个名字不一定和你的比赛标题相同，你也可以把你的 `比赛标题` 取名为 `奥里与彩虹摇滚重金属炫彩中二小王子的阿克之战`。）

`比赛目录` 默认在你的个人的主文件夹下。你也可以进行更改。可以点击 `...` 按钮来选择。

在你的 `比赛目录` 下，将会有 2 个文件夹产生： `data` 和 `source` 。

`data` 存放你的题目相关的文件。

`source` 存放你的选手相关的文件。

## 添加题目

假设你的 `contest` 有 3 道题： `题1` ，`题2` 和 `题3` ，选手提交的文件名字分别为 `t1` ，`t2` 和 `t3` 。它们分别是传统题，提交答案题和交互题。

### 开始

把 LemonLime 页面切换到 `试题` 页面（另一个是 `选手` 页面）。

右键 `概要` 下面的白色框，选择 `添加新试题` ，并为你的题目命名。

### 传统题配置

现在你配置的试题是 `题1` 。

添加题目之后，在右侧 `详情` 的 `试题类型` 勾选 `传统题` 。

在 `源文件名称` 写上 `t1` 。

根据你的需要选择是否 `在子文件夹内寻找` 。

`输入文件名` 和 `输出文件名` 会被自动填写，也可以根据你的需要进行改动。

选择你的题目的 `比较模式` 。

调整你的 `编译器设置` ，可以 启用/禁用 某种语言，或是 打开/关闭 优化。

#### 比较模式

LemonLime 内嵌了 3 种比较模式，还提供了 2 种扩展模式。

##### 逐行比较模式

对每一行进行比较。

可选 忽略/不忽略 行末回车 和 多余的空格。

##### 实数比较模式

比较单个实数。

对 `nan` 和 `inf` 作出识别。

##### 自定义校验器模式

参见文档 `specialjudge` 。

#### 添加测试点

右键 `概要` 下面的白色框，选择 `添加新测试点` 。

假设你的 `contest` 目录的结构是这样的：

```plain
contest
|	data
|	|	t1
|	|	|	t1_1.in
|	|	|	t1_1.ans
|	|	|	t1_2.in
|	|	|	t1_2.ans
|	|	t2
|	|	t3
|	source
```

而你此时想添加一组包含 `t1_1` 的测试点，那么在 `输入文件名` 输入 `t1/t1_1.in` ， 在 `输出文件名` 输入 `t1/t1_1.out` （如你所见，它们以 `data` 为根文件夹。），然后点击 `添加` 。

如果你把 `t1_2` 也加进去，那么它们将会构成一个 `subtask` 。

在下面设置你的这个测试点的 `分值`，`时间限制` 和 `空间限制`。

#### 批量添加多组测试点

在 `概要` 右键，点击 `添加多组测试点…`。

##### 如何写一个语法正确的正则表达式

下面是一个例子：

输入文件：`matrix/matrix<1>.in`

输出文件：`matrix/matrix<1>.out`

把`<1>`设为`\d*`。

> 提示：
> `\d` 表示匹配一个数字。
> 匹配任意数量的数字： `\d*`
> `.` 表示匹配任意一个字符。
> `*` 表示把之前的那个表达式重复 0 到无限大遍。

#### * 子任务依赖

对于一个测试点，你可以设置 `子任务依赖` ，具体效果就是只有当 `子任务依赖` 内的所有测试点都通过后才会测试这个测试点。

测试点的编号可以在左侧 `概要` 查看。

对于测试点 10 ，一个合法的 `子任务依赖` 为 `1,2,3,6,9` 。不能依赖之后的测试点，并且每个数字之间要以半角逗号隔开。

### 提交答案题配置

现在你配置的试题是 `题2` 。

添加题目之后，在右侧 `详情` 的 `试题类型` 勾选 `提交答案题` 。

所有的 `编译器设置` 被禁用。

编辑 `选手答案文件扩展名` 。

选手提交的文件名将为 `源文件名称` + `数据序号` + `.` + `选手答案文件扩展名` ， 比如对于 `题2` 的第 5 个测试点，选手应该提交 `t25.out` （当 `选手答案文件扩展名` 为 `out` ）。

### * 交互题配置

现在你配置的试题是 `题3` 。

添加题目之后，在右侧 `详情` 的 `试题类型` 勾选 `交互题` 。

选项和传统题的配置没有多大差别。

你需要提供你的 `交互库` 和 `接口` ，它们的路径以 `data` 文件夹为根进行填写。

假设你的 `contest` 目录的结构是这样的：

```plain
contest
|	data
|	|	t1
|	|	t2
|	|	t3
|	|	|	t3.h
|	|	|	t3.cpp
|	source
```

那么你应该这么填写：

`交互库路径` ： `t3/t3.h`

`交互库名称` ： `t3.h`

`接口实现(grader)路径` ： `t3/t3.cpp`

如果你真的要出一道交互题，那么应该知道 `grader` 是什么。

### 自动添加试题

当你的 `data` 存放方式符合一般规律，可以使用 `自动添加试题` 来快速添加试题。

去 `控制` > `自动添加试题` 。

## 选手

假设你有一位选手，名字为 `Mona` 。

`Mona` 很强，把你的题目阿克了。

假设 `Mona` 的选手目录是这样的：

```plain
Mona
|	t1
|	|	t1.cpp
|	t2
|	|	t21.out
|	|	t22.out
|	t3
|	|	t3.cpp
|	t1.cpp
|	t21.out
|	t22.out
|	t3.cpp
```

当你的 3 个题目都使用了 `在子文件夹寻找` ，那么以下文件是有用的：

```plain
Mona
|	t1
|	|	t1.cpp		<<<
|	t2
|	|	t21.out		<<<
|	|	t22.out		<<<
|	t3
|	|	t3.cpp		<<<
|	t1.cpp
|	t21.out
|	t22.out
|	t3.cpp
```

否则的话，以下文件是有用的：

```plain
Mona
|	t1
|	|	t1.cpp
|	t2
|	|	t21.out
|	|	t22.out
|	t3
|	|	t3.cpp
|	t1.cpp			<<<
|	t21.out			<<<
|	t22.out			<<<
|	t3.cpp			<<<
```

请把 `Mona` 放在 `source` 目录下。

```plain
contest
|	data
|	source
|	|	Mona
```

在左上角选中 `选手` 栏，点击 `刷新` ，`Mona` 将会出现在选手名单中。

### * 整理文件

> **！ 注意**
>
> 这个功能对于 `提交答案题` 的适应性还处于测试阶段。
>
> 如果子文件夹里面的文件有文件名和子文件夹外面的文件相同的，子文件夹**外面的文件会丢失**！
>
> 最好在整理文件之前备份一份，以防不测。

假设 `Mona` 的选手目录是这样的：

```plain
Mona
|	.vscode
|	|	extensions
|	|	|	...
|	t1
|	|	t1.cpp
|	|	t1.in
|	|	t1.exe
|	t2
|	|	t21.out
|	|	t22.out
|	ex_t1.cpp
|	t1.exe
|	t23.out
|	t3
|	t3.cpp
|	t4.cpp
|	notice.txt
|	xzy被阿视频.avi
|	三角符文 - Deltarune 绿色免安装硬盘版.zip
```

在左上角选中 `选手` ，点击 `整理文件` 。

`Mona` 就会变成这样：

```plain
Mona
|	t1
|	|	t1.cpp
|	|	t1.in
|	t2
|	|	t21.out
|	|	t22.out
|	|	t23.out
|	t3
|	|	t3.cpp
|	t1.cpp
|	t1.in
|	t21.out
|	t22.out
|	t23.out
|	t3.cpp
```

## 导出成绩

去 `控制` > `导出成绩` 。

它将导出一个 HTML 或 CSV （Windows 中还有 XLS） 文件，记录所有选手的成绩。

导出 HTML 有两种模式：完整版和压缩版。

完整版 HTML 有更多的颜色，支持题目跳转；

压缩版 HTML 体积更小，比原来的还要小 20% 到 50%。

使用后缀 `*.html` 的时候启用完整版，使用后缀 `*.htm` 的时候使用压缩版。