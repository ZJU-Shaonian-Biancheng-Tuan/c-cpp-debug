# 第零章 代码书写建议

整洁干净的代码意味着更清楚的逻辑，能有效降低错误出现的可能。


  
## 格式化代码

> 新手可能会有这样的想法：反正我不在乎代码的美观程度；计算机也不在乎；我也不想把自己的代码给别人看；那么为什么我要将代码格式化？  
> 因为格式化的代码增加了代码的可读性、可维护性。在程序的规模不断扩大的时候，代码的可读性非常重要。将代码写得更好懂一些，方便了其他人理解你的代码，这里的其他人也有可能是几个月后的你自己。

代码的格式包括缩进、括号风格，通常可以使用代码格式化工具一步调优。

比如 Visual Studio 就有这样的功能。

在其他的 MinGW IDE, 如 Dev-C++, C-Free 等，则可以运用 AStyle 这个工具来执行代码格式化。

在Linux下的编辑器, 如 Vim, Emacs 等 也可以配置 代码格式化插件。

**不过，最好还是养成良好的代码书写习惯。**

以下先给出一个反面教材

```c
int main()
{int i;
    for(i=0;i<10;i++)
    {
    printf("%d ",i);
    }printf("\n");
    return 0;
    }
```

笔者曾经看过不少新手编码的过程：

他们不会也不知道格式化代码

他们没有将输入光标定位到合适位置  
1. 他们可能知道要将局部变量定义到函数内部，但不知道将其放在何处  
2. 他们可能只是知道这条语句要放在哪两个花括号的内部，却从来不在意更具体的位置

很多新手在编程的时候发现一些地方要改的时候，笨拙地使用鼠标去定位，而且点不准

一则是慢，二则是会使得代码格式非常糟糕。

同样逻辑的代码，不同的人写起来的风格是不一样的。

以下是笔者的代码风格   
左花括号不换行，右花括号与左花括号所在行缩进一致。
```c
int main(){ //
    //do something
}

if (a > 10){ //
    //do something
}else{
    //else do something
}
```
也有人习惯大括号换行，比如这样
```c
int main()
{
    int a = 0;
    if(a > 10)
    {
        //do something
    }
    else
    {
        //do something
    }
    return 0;
}
```
一元以上运算符与其操作数之间有一个空格。
```c
a = a + 1; //这里要加空格
a = -a + 1; //-a不需要加空格
b = a > 0 ? 1 : 0;
```
函数参数列表中的逗号后面有一个空格，前面没有，分号后面如果不换行，那么有一个空格。
```c
for (int i = 0; i < 10; i++){
    printf("i = %d\n", i);
}
```
对于空格的要求也可以更苛刻，比如控制块 (if, for, switch) 的括号前要加空格，不换行的大括号前要加空格
```c
if (a > 10) { //注意左右括号旁的空格
```
最后的代码写起来就是这个样子的
```c
int main() {
    int i;
    for(i = 0; i < 10; i++) {
        printf("%d ", i);
    }
    printf("\n");
    return 0;
}
```
## 基本的代码格式化要求

* 缩进规范统一
* 大括号不换行/换行统一
* 空格统一

### 可供参考的常见代码格式化模板

* `while`
```c
while (i < 10) {
    printf("%d", i);
    i--;
}
```
* `do-while`
```c
do {
    printf("%d", i);
    i++;
} while(i < 10)
```
* `for`
```c
for (int i = 0; i < 10; i++) {
    printf("%d", i);
}
```
* `switch`
```c
switch (c) {
    case 'A': {
        printf("You got 90!");
        break;
    }
    case 'B': {
        printf("You got 80!");
        break;
    }
    default: {
        printf("You lose.");
    }
}
```

* `if-else`
```c
if (a < 0) {
    printf("less than 0");
} else if (a < 20) {
    printf("0 <= a < 20");
} else if (a < 90) {
    printf("20 <= a < 90");
} else {
    printf("a >= 90");
}
```

## 变量命名规则
### 常用的变量名规则
    
* `camelCase` - 驼峰式
    
    这种命名方式将单词首位相接，并首字母小写，其余首字母大写
    
    如：`numberOfDigits`, `longLongAgo`, `numberOfDaysInThisMonth`, `getNumberFromUser`

* `PascalCase` - 帕斯卡式
    
    这种命名方式因Pascal语言而得名，他与驼峰命名法的区别就是首字母也大写

    如：`ToString`, `GetNumber`, `CreateHttpRequest`

* `snake_case`

    这种命名方式中所有字母小写，使用下划线 `_` 连接

    如：`find_first_of`,  `unordered_map`, `from_chars`

* ansi C 命名法（不建议）

    这种命名方式常见于C标准库，主要是将单词中的元音字母尽量去除，来减少变量名的字数。

    如：`strlen`(`string length`)，`strcmp`(`string compare`), `stdio`(`standard IO`)

    这种做法主要是因为古老的C语言并不支持很长的变量名，以及古老的键盘打字很费力，降低字母数可以提高编码速度。因为会降低可读性，及现代的键盘已经十分轻便，所以现在已经不建议使用。

* 匈牙利命名（已弃用）

    匈牙利命名是由类型前缀后跟Pascal命名的变量构成，为了在不支持智能提示的编程环境中提醒程序员变量的类型，这种命名法常见于古老的 Win32 程序代码中，现在已经弃用

    如：`lpszWindowName`, `lParam`, `hInstance`。



### 使用有意义的名字做变量名

对于表示数量或多少的变量，尽量使用能代表他们的意义的名词或名词短语作为变量名，比如`numberOfBanana`, `age`, `year`等

对于表示状态的变量，应使用能代表这个短语命名，如`hasApple`, `hasHit`, `isHuman`，这样在写`if`语句的时候会使表述十分清楚，如`if (hasApple)`, `if (isHuman) `使表述十分清楚。

对于函数，一般使用动词或动词短语来命名，比如`getNumber`, `printDigit`,这样的目的也是为了使表述更加清楚，如`int number = getNumber()`, `printDigit(number)`。

### 使用无歧义的名字做变量名

例如，当你需要一个表时间的变量时，一个可选的变量名是`now`，但是，一个更好的名字可能是`nowMs`来表示这个时间的单位是毫秒。变量类型无法提供更多的信息时，这个任务便落在了变量名上。同理，一个把时间(`int`)转换到`Time`类型的函数，可以叫`TimeFromUnix`，但可选的更好的名字也许是`TimeFromUnixMs`。

另外，有一些常用的变量名其实并没有任何的实际含义，它们往往能使用在非常多的地方。例如：`data`, `state`, `value`, `object`, `instance`。
