[TOC]

## Bash 的输入和输出

### 输入

1、读取用户输入并且存储在变量里面

```bash
#!/bin/bash
echo "What's your name?"
read entered_name		# 读取用户输入
echo -e "\nwelcome to bash tutorial" $entered_name
```

2、从文件中读取

这将从input.txt里面读取每一行

```bash
while read line
do
        echo $line
done < input.txt
```

3、命令行读取

$1代表初始参数，$2代表第二个参数，依此类推

```bash
echo "Hello, $1!"
```

### 输出

1、打印到终端

echo

2、写入文件

```bash
echo "abc" > output.txt
```

3、追加到文件

```bash
echo "abcd" >> output.txt
```

4、重定向输出

```bash
ls > output.txt
```

5、格式化输出

```bash
printf "%-10s %-8s %-4s\n" 姓名 性别 体重kg  
```

## 常见的比较运算符

-eq  等于

-ne  不等于

-gt  大于

-lt  小于

-ge  大于或等于

-le  小于或等于

## 判断语句

### if语句

该有空格一定要有空格

```bash
#!/bin/bash
echo "输入一个数字"
read number

if [$number -gt 0]&&[$number -lt 10]; then
        echo "输入的数字在0到100之间"
else
        echo "数字不在0到100之间"
fi


$ sh e.sh
输入一个数字
2
输入的数字在0到100之间
```

### case

基础语法

```bash
case expression in
    pattern1)
        # code to execute if expression matches pattern1
        ;;
    pattern2)
        # code to execute if expression matches pattern2
        ;;
    pattern3)
        # code to execute if expression matches pattern3
        ;;
    *)
        # code to execute if none of the above patterns match expression
        ;;
esac
```

```bash
fruit="apple"

case $fruit in
        "apple")
                echo "This is a read fruit."
                ;;
        "banana")
                echo "This is a yellow fruit."
                ;;
        "orange")
                echo "This is an orange fruit."
                ;;
        *)
                echo "Unknown fruit."
                ;;
esac
```



## 循环

在 Bash 中，`(( ... ))` 和 `[[ ... ]]` 是用于不同目的的两种不同的括号语法。

### 1. `(( ... ))`

- **用途**: 用于算术运算。
- **示例**: `(( i += 1 ))` 用于增加变量 `i` 的值。这里的 `(( ... ))` 允许你执行算术运算，而不需要使用 `$` 来引用变量。例如，`i += 1` 相当于 `i = i + 1`。

### 2. `[[ ... ]]`

- **用途**: 用于条件测试，特别是更复杂的条件。
- **示例**: `[[ $i -le 10 ]]` 用于检查变量 `i` 是否小于或等于 10。`[[ ... ]]` 提供了比 `[ ... ]` 更强大的功能，例如支持模式匹配和逻辑运算。

### 总结

- `(( ... ))` 用于进行算术运算。
- `[[ ... ]]` 用于条件判断。

### while

```bash
#!/bin/bash
i=1
while [[ $i -le 10 ]] ; do
   echo "$i"
  (( i += 1 ))
done

$ sh a.sh
1
2
3
4
5
6
7
8
9
10

```

### for

```bash
#!/bin/bash

for i in {1..5}
do
    echo $i
done


$ sh b.sh
1
2
3
4
5
```



## cron定时任务

`cron` 是 Unix 和类 Unix 操作系统中用于定期执行任务的守护进程。它允许用户在指定的时间间隔内自动运行脚本或命令。使用 `cron` 可以实现定时备份、定期清理、定时发送邮件等功能。

|     安排     |                  描述                   |       示例        |
| :----------: | :-------------------------------------: | :---------------: |
|  0 0 * * *   |          每天午夜运行一个脚本           |  0 0 * * * a.sh   |
| * /5 * * * * |           每5分钟运行一个脚本           | * /5 * * * * a.sh |
| 0 6 * * 1-5  | 从星期一到星期五每天早上6点运行一个脚本 | 0 6 * * 1-5 a.sh  |
| 0 0 1-7 * *  |       每个月的前七天运行一个脚本        | 0 0 1-7 * * a.sh  |
|  0 12 1 * *  |   每个月的第一天中午12点运行一个脚本    |  0 12 1 * * a.sh  |

**使用crontab**

crontab 工具用于添加和编辑cron作业

crontab -l 列出特定用户已经安排好的脚本

你可以通过crontab -e 添加和编辑cron

