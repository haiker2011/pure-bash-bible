<p align="center"><img src="https://raw.githubusercontent.com/odb/official-bash-logo/master/assets/Logos/Icons/PNG/512x512.png" width="200px"></p>
<h1 align="center">pure bash bible</h1> <p
align="center">A collection of pure bash alternatives to external
processes.</p>

<p align="center"> <a
href="https://travis-ci.com/dylanaraps/pure-bash-bible"><img
src="https://travis-ci.com/dylanaraps/pure-bash-bible.svg?branch=master"></a>
<a href="https://discord.gg/yfa5BDw"><img src="https://img.shields.io/discord/440354555197128704.svg"></a>
<a href="./LICENSE.md"><img
src="https://img.shields.io/badge/license-MIT-blue.svg"></a>
</p>

<br>

<a href="https://leanpub.com/bash/">
<img src="https://s3.amazonaws.com/titlepages.leanpub.com/bash/hero" width="40%" align="right">
</a>

这本书的目的是记录常用和不太常用的方法，只使用内置的 `bash` 特性来完成各种任务。使用 bible 中的片段有助于从脚本中删除不必要的依赖项，在大多数情况下，使y用它们性能更好。我在开发 [NeoFetch](https://github.com/dylanaraps/neoFetch) ，[pxltrm](https://github.com/dylanaraps/pxltrm) 和其他小的项目时发现了这些技巧。

下面的代码片段是使用 `shellcheck` 进行代码检查，并在适用的情况下编写了测试。想贡献您的一份力量？ 阅读[CONTRIBUTING.md](https://github.com/dylanaraps/pure-bash-bible/blob/master/CONTRIBUTING.md)。它概述了单元测试是如何工作的，以及向 bible 中添加代码片段时需要什么。

发现不正确的描述、bug 或者错误？新建一个 issue 或者向我们发 PR。如果发现 bible 缺少了一些东西，可以新建一个 issue，你应该会得到答复。

<br>
<p align="center"><b>这本书可以在 leanpub 上进行购买。 https://leanpub.com/bash</b></p>
<p align="center"><b>或者你也可以打赏作者。</b>
<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=V7QNJNKS3WYVS"><img src="https://img.shields.io/badge/don-paypal-yellow.svg"></a> <a href="https://www.patreon.com/dyla"><img src="https://img.shields.io/badge/don-patreon-yellow.svg"> </a><a href="https://liberapay.com/2211/"><img src="https://img.shields.io/badge/don-liberapay-yellow.svg"></a>
</p>

<br>

# 目录

<!-- vim-markdown-toc GFM -->

* [前言](#前言)
* [字符串](#字符串)
    * [字符串去掉前导空格和尾随空格](#字符串去掉前导空格和尾随空格)
    * [去掉字符串所有空格和截断空格](#去掉字符串所有空格和截断空格)
    * [对字符串使用正则表达式](#对字符串使用正则表达式)
    * [在分隔符上拆分字符串](#在分隔符上拆分字符串)
    * [将字符串改为小写](#将字符串改为小写)
    * [将字符串改为大写](#将字符串改为大写)
    * [去掉字符串中引号](#去掉字符串中引号)
    * [从字符串中去掉匹配模式的所有实例](#从字符串中去掉匹配模式的所有实例)
    * [从字符串中去掉第一个匹配的模式](#从字符串中去掉第一个匹配的模式)
    * [从字符串开始去掉匹配模式](#从字符串开始去掉匹配模式)
    * [从字符串结尾去掉匹配模式](#从字符串结尾去掉匹配模式)
    * [字符串中“/”编码](#字符串中“/”编码)
    * [字符串中“/”解码](#字符串中“/”解码)
    * [检查字符串是否包含某个子串](#检查字符串是否包含某个子串)
    * [检查字符串是否以某子串开始](#检查字符串是否以某子串开始)
    * [检查字符串是否以某子串结束](#检查字符串是否以某子串结束)
* [数组](#数组)
    * [反转数组](#反转数组)
    * [去除数组中重复元素](#去除数组中重复元素)
    * [随机输出数组中的一个元素](#随机输出数组中的一个元素)
    * [循环数组](#循环数组)
    * [在两个值之间切换](#在两个值之间切换)
* [循环](#循环)
    * [循环遍历一系列数字](#循环遍历一系列数字)
    * [循环遍历一个从0到变量的数字](#循环遍历一个从0到变量的数字)
    * [循环遍历数组](#循环遍历数组)
    * [通过索引循环遍历数组内容](#通过索引循环遍历数组内容)
    * [循环遍历文件内容](#循环遍历文件内容)
    * [循环遍历文件和目录](#循环遍历文件和目录)
* [文件处理](#文件处理)
    * [文件读入到字符串](#文件读入到字符串)
    * [文件读入到数组 (*按行*)](#文件读入到数组-(*按行*))
    * [获取文件的前N行](#获取文件的前N行)
    * [获取文件最后N行](#获取文件最后N行)
    * [获取文件行数](#获取文件行数)
    * [对目录中的文件或目录进行计数](#对目录中的文件或目录进行计数)
    * [创建空文件](#创建空文件)
    * [提取两个标记之间的行](#提取两个标记之间的行)
* [FILE PATHS](#file-paths)
    * [Get the directory name of a file path](#get-the-directory-name-of-a-file-path)
    * [Get the base-name of a file path](#get-the-base-name-of-a-file-path)
* [VARIABLES](#variables)
    * [Assign and access a variable using a variable](#assign-and-access-a-variable-using-a-variable)
    * [Name a variable based on another variable](#name-a-variable-based-on-another-variable)
* [ESCAPE SEQUENCES](#escape-sequences)
    * [Text Colors](#text-colors)
    * [Text Attributes](#text-attributes)
    * [Cursor Movement](#cursor-movement)
    * [Erasing Text](#erasing-text)
* [PARAMETER EXPANSION](#parameter-expansion)
    * [Indirection](#indirection)
    * [Replacement](#replacement)
    * [Length](#length)
    * [Expansion](#expansion)
    * [Case Modification](#case-modification)
    * [Default Value](#default-value)
* [BRACE EXPANSION](#brace-expansion)
    * [Ranges](#ranges)
    * [String Lists](#string-lists)
* [CONDITIONAL EXPRESSIONS](#conditional-expressions)
    * [File Conditionals](#file-conditionals)
    * [File Comparisons](#file-comparisons)
    * [Variable Conditionals](#variable-conditionals)
    * [Variable Comparisons](#variable-comparisons)
* [ARITHMETIC OPERATORS](#arithmetic-operators)
    * [Assignment](#assignment)
    * [Arithmetic](#arithmetic)
    * [Bitwise](#bitwise)
    * [Logical](#logical)
    * [Miscellaneous](#miscellaneous)
* [ARITHMETIC](#arithmetic-1)
    * [Simpler syntax to set variables](#simpler-syntax-to-set-variables)
    * [Ternary Tests](#ternary-tests)
* [TRAPS](#traps)
    * [Do something on script exit](#do-something-on-script-exit)
    * [Ignore terminal interrupt (CTRL+C, SIGINT)](#ignore-terminal-interrupt-ctrlc-sigint)
    * [React to window resize](#react-to-window-resize)
    * [Do something before every command](#do-something-before-every-command)
    * [Do something when a shell function or a sourced file finishes executing](#do-something-when-a-shell-function-or-a-sourced-file-finishes-executing)
* [PERFORMANCE](#performance)
    * [Disable Unicode](#disable-unicode)
* [OBSOLETE SYNTAX](#obsolete-syntax)
    * [Shebang](#shebang)
    * [Command Substitution](#command-substitution)
    * [Function Declaration](#function-declaration)
* [INTERNAL VARIABLES](#internal-variables)
    * [Get the location to the `bash` binary](#get-the-location-to-the-bash-binary)
    * [Get the version of the current running `bash` process](#get-the-version-of-the-current-running-bash-process)
    * [Open the user's preferred text editor](#open-the-users-preferred-text-editor)
    * [Get the name of the current function](#get-the-name-of-the-current-function)
    * [Get the host-name of the system](#get-the-host-name-of-the-system)
    * [Get the architecture of the Operating System](#get-the-architecture-of-the-operating-system)
    * [Get the name of the Operating System / Kernel](#get-the-name-of-the-operating-system--kernel)
    * [Get the current working directory](#get-the-current-working-directory)
    * [Get the number of seconds the script has been running](#get-the-number-of-seconds-the-script-has-been-running)
    * [Get a pseudorandom integer](#get-a-pseudorandom-integer)
* [INFORMATION ABOUT THE TERMINAL](#information-about-the-terminal)
    * [Get the terminal size in lines and columns (*from a script*)](#get-the-terminal-size-in-lines-and-columns-from-a-script)
    * [Get the terminal size in pixels](#get-the-terminal-size-in-pixels)
    * [Get the current cursor position](#get-the-current-cursor-position)
* [CONVERSION](#conversion)
    * [Convert a hex color to RGB](#convert-a-hex-color-to-rgb)
    * [Convert an RGB color to hex](#convert-an-rgb-color-to-hex)
* [CODE GOLF](#code-golf)
    * [Shorter `for` loop syntax](#shorter-for-loop-syntax)
    * [Shorter infinite loops](#shorter-infinite-loops)
    * [Shorter function declaration](#shorter-function-declaration)
    * [Shorter `if` syntax](#shorter-if-syntax)
    * [Simpler `case` statement to set variable](#simpler-case-statement-to-set-variable)
* [OTHER](#other)
    * [Use `read` as an alternative to the `sleep` command](#use-read-as-an-alternative-to-the-sleep-command)
    * [Check if a program is in the user's PATH](#check-if-a-program-is-in-the-users-path)
    * [Get the current date using `strftime`](#get-the-current-date-using-strftime)
    * [Get the username of the current user](#get-the-username-of-the-current-user)
    * [Generate a UUID V4](#generate-a-uuid-v4)
    * [Progress bars](#progress-bars)
    * [Get the list of functions in a script](#get-the-list-of-functions-in-a-script)
    * [Bypass shell aliases](#bypass-shell-aliases)
    * [Bypass shell functions](#bypass-shell-functions)
    * [Run a command in the background](#run-a-command-in-the-background)
* [AFTERWORD](#afterword)

<!-- vim-markdown-toc -->

<br>

<!-- CHAPTER START -->
# 前言

纯 `bash` 替代外部进程和程序的集合。`bash` 脚本语言比人们意识到的更强大，而且大多数任务都可以在不依赖外部程序的情况下完成。

在 `bash` 中调用一个外部进程是昂贵的，过度使用会导致明显的速度减慢。使用内置方法（*如果适用*）编写的脚本和程序将更快，需要的依赖性更少，并且能够更好地理解语言本身。

本书的内容为解决在 `bash` 中编写程序和脚本时遇到的问题提供了参考。示例以函数格式显示如何将这些解决方案合并到代码中。

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 字符串

## 字符串去掉前导空格和尾随空格

这是 `sed`、`awk`、`perl` 和其他工具的替代方案。下面的函数通过查找所有前导空格和尾随空格以及从字符串的开始和结束处删除它。使用 `:` 内置变量代替临时变量。

**示例函数：**

```sh
trim_string() {
    # Usage: trim_string "   example   string    "
    : "${1#"${1%%[![:space:]]*}"}"
    : "${_%"${_##*[![:space:]]}"}"
    printf '%s\n' "$_"
}
```

**示例用法：**

```shell
$ trim_string "    Hello,  World    "
Hello,  World

$ name="   John Black  "
$ trim_string "$name"
John Black
```


## 去掉字符串所有空格和截断空格

This is an alternative to `sed`, `awk`, `perl` and other tools. The
function below works by abusing word splitting to create a new string
without leading/trailing white-space and with truncated spaces.

这是 `sed`、`awk`、`perl` 和其他工具的替代方案。下面的函数通过滥用单词分隔符来创建新字符串没有前导/尾随空格和截断空格。

**示例函数：**

```sh
# shellcheck disable=SC2086,SC2048
trim_all() {
    # Usage: trim_all "   example   string    "
    set -f
    set -- $*
    printf '%s\n' "$*"
    set +f
}
```

**示例用法：**

```shell
$ trim_all "    Hello,    World    "
Hello, World

$ name="   John   Black  is     my    name.    "
$ trim_all "$name"
John Black is my name.
```

## 对字符串使用正则表达式

`bash` 的正则表达式匹配结果可用于替换 `sed` 大部分的使用场景。

**警告**：这是少数几个依赖于平台的 `bash` 功能之一。`bash` 将使用用户系统上安装的任何正则表达式引擎。如果目标是兼容性，请坚持使用 POSIX 正则表达式功能。

**警告**：此示例仅打印第一个匹配组。当使用多个捕获组时需要进行一些修改。

**示例函数：**

```sh
regex() {
    # Usage: regex "string" "regex"
    [[ $1 =~ $2 ]] && printf '%s\n' "${BASH_REMATCH[1]}"
}
```

**示例用法：**

```shell
$ # Trim leading white-space.
$ regex '    hello' '^\s*(.*)'
hello

$ # Validate a hex color.
$ regex "#FFFFFF" '^(#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$'
#FFFFFF

$ # Validate a hex color (invalid).
$ regex "red" '^(#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$'
# no output (invalid)
```

**脚本中的示例用法：**

```shell
is_hex_color() {
    if [[ $1 =~ ^(#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$ ]]; then
        printf '%s\n' "${BASH_REMATCH[1]}"
    else
        printf '%s\n' "error: $1 is an invalid color."
        return 1
    fi
}

read -r color
is_hex_color "$color" || color="#FFFFFF"

# Do stuff.
```


## 在分隔符上拆分字符串

This is an alternative to `cut`, `awk` and other tools.

这是 `cut`、`awk` 和其他工具的替代方案。

**示例函数：**

```sh
split() {
   # Usage: split "string" "delimiter"
   IFS=$'\n' read -d "" -ra arr <<< "${1//$2/$'\n'}"
   printf '%s\n' "${arr[@]}"
}
```

**示例用法：**

```shell
$ split "apples,oranges,pears,grapes" ","
apples
oranges
pears
grapes

$ split "1, 2, 3, 4, 5" ", "
1
2
3
4
5

# Multi char delimiters work too!
$ split "hello---world---my---name---is---john" "---"
hello
world
my
name
is
john
```

## 将字符串改为小写

**警告：** 需要 `bash` 4+

**示例函数：**

```sh
lower() {
    # Usage: lower "string"
    printf '%s\n' "${1,,}"
}
```

**示例用法：**

```shell
$ lower "HELLO"
hello

$ lower "HeLlO"
hello

$ lower "hello"
hello
```

## 将字符串改为大写

**CAVEAT:** 需要 `bash` 4+

**示例函数：**

```sh
upper() {
    # Usage: upper "string"
    printf '%s\n' "${1^^}"
}
```

**示例用法：**

```shell
$ upper "hello"
HELLO

$ upper "HeLlO"
HELLO

$ upper "HELLO"
HELLO
```

## 去掉字符串中引号

**示例函数：**

```sh
trim_quotes() {
    # Usage: trim_quotes "string"
    : "${1//\'}"
    printf '%s\n' "${_//\"}"
}
```

**示例用法：**

```shell
$ var="'Hello', \"World\""
$ trim_quotes "$var"
Hello, World
```

## 从字符串中去掉匹配模式的所有实例

**示例函数：**

```sh
strip_all() {
    # Usage: strip_all "string" "pattern"
    printf '%s\n' "${1//$2}"
}
```

**示例用法：**

```shell
$ strip_all "The Quick Brown Fox" "[aeiou]"
Th Qck Brwn Fx

$ strip_all "The Quick Brown Fox" "[[:space:]]"
TheQuickBrownFox

$ strip_all "The Quick Brown Fox" "Quick "
The Brown Fox
```

## 从字符串中去掉第一个匹配的模式

**示例函数：**

```sh
strip() {
    # Usage: strip "string" "pattern"
    printf '%s\n' "${1/$2}"
}
```

**示例用法：**

```shell
$ strip "The Quick Brown Fox" "[aeiou]"
Th Quick Brown Fox

$ strip "The Quick Brown Fox" "[[:space:]]"
TheQuick Brown Fox
```

## 从字符串开始去掉匹配模式

**示例函数：**

```sh
lstrip() {
    # Usage: lstrip "string" "pattern"
    printf '%s\n' "${1##$2}"
}
```

**示例用法：**

```shell
$ lstrip "The Quick Brown Fox" "The "
Quick Brown Fox
```

## 从字符串结尾去掉匹配模式

**示例函数：**

```sh
rstrip() {
    # Usage: rstrip "string" "pattern"
    printf '%s\n' "${1%%$2}"
}
```

**示例用法：**

```shell
$ rstrip "The Quick Brown Fox" " Fox"
The Quick Brown
```

## 字符串中“/”编码

**示例函数：**

```sh
urlencode() {
    # Usage: urlencode "string"
    local LC_ALL=C
    for (( i = 0; i < ${#1}; i++ )); do
        : "${1:i:1}"
        case "$_" in
            [a-zA-Z0-9.~_-])
                printf '%s' "$_"
            ;;

            *)
                printf '%%%02X' "'$_"
            ;;
        esac
    done
    printf '\n'
}
```

**示例用法：**

```shell
$ urlencode "https://github.com/dylanaraps/pure-bash-bible"
https%3A%2F%2Fgithub.com%2Fdylanaraps%2Fpure-bash-bible
```

## 字符串中“/”解码

**示例函数：**

```sh
urldecode() {
    # Usage: urldecode "string"
    : "${1//+/ }"
    printf '%b\n' "${_//%/\\x}"
}
```

**示例用法：**

```shell
$ urldecode "https%3A%2F%2Fgithub.com%2Fdylanaraps%2Fpure-bash-bible"
https://github.com/dylanaraps/pure-bash-bible
```

## 检查字符串是否包含某个子串

**使用 test：**

```shell
if [[ $var == *sub_string* ]]; then
    printf '%s\n' "sub_string is in var."
fi

# Inverse (substring not in string).
if [[ $var != *sub_string* ]]; then
    printf '%s\n' "sub_string is not in var."
fi

# This works for arrays too!
if [[ ${arr[*]} == *sub_string* ]]; then
    printf '%s\n' "sub_string is in array."
fi
```

**使用 case 声明：**

```shell
case "$var" in
    *sub_string*)
        # Do stuff
    ;;

    *sub_string2*)
        # Do more stuff
    ;;

    *)
        # Else
    ;;
esac
```

## 检查字符串是否以某子串开始

```shell
if [[ $var == sub_string* ]]; then
    printf '%s\n' "var starts with sub_string."
fi

# Inverse (var does not start with sub_string).
if [[ $var != sub_string* ]]; then
    printf '%s\n' "var does not start with sub_string."
fi
```

## 检查字符串是否以某子串结束

```shell
if [[ $var == *sub_string ]]; then
    printf '%s\n' "var ends with sub_string."
fi

# Inverse (var does not end with sub_string).
if [[ $var != *sub_string ]]; then
    printf '%s\n' "var does not end with sub_string."
fi
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 数组

## 反转数组

启用 `extdebug` 允许访问存储的 `BASH_ARGV` 数组反转当前函数的参数。

**示例函数：**

```sh
reverse_array() {
    # Usage: reverse_array "array"
    shopt -s extdebug
    f()(printf '%s\n' "${BASH_ARGV[@]}"); f "$@"
    shopt -u extdebug
}
```

**示例用法：**

```shell
$ reverse_array 1 2 3 4 5
5
4
3
2
1

$ arr=(red blue green)
$ reverse_array "${arr[@]}"
green
blue
red
```

## 去除数组中重复元素

创建一个临时的相关数组。设置的相关数组的值和赋值的值重复时，bash 会覆盖值。这样可以有效地删除数组中的重复项。

**警告：** 需要 `bash` 4+

**示例函数：**

```sh
remove_array_dups() {
    # Usage: remove_array_dups "array"
    declare -A tmp_array

    for i in "$@"; do
        [[ $i ]] && IFS=" " tmp_array["${i:- }"]=1
    done

    printf '%s\n' "${!tmp_array[@]}"
}
```

**示例用法：**

```shell
$ remove_array_dups 1 1 2 2 3 3 3 3 3 4 4 4 4 4 5 5 5 5 5 5
1
2
3
4
5

$ arr=(red red green blue blue)
$ remove_array_dups "${arr[@]}"
red
green
blue
```

## 随机输出数组中的一个元素

**示例函数：**

```sh
random_array_element() {
    # Usage: random_array_element "array"
    local arr=("$@")
    printf '%s\n' "${arr[RANDOM % $#]}"
}
```

**示例用法：**

```shell
$ array=(red green blue yellow brown)
$ random_array_element "${array[@]}"
yellow

# Multiple arguments can also be passed.
$ random_array_element 1 2 3 4 5 6 7
3
```

## 循环数组

Each time the `printf` is called, the next array element is printed. When
the print hits the last array element it starts from the first element
again.

每次调用 `printf` 时，都会打印下一个数组元素。当 print 命中数组的最后一个元素后，它从第一个元素开始再打印以此。

```sh
arr=(a b c d)

cycle() {
    printf '%s ' "${arr[${i:=0}]}"
    ((i=i>=${#arr[@]}-1?0:++i))
}
```


## 在两个值之间切换

这个和上面一个工作原理相同，只是不同的使用场景。

```sh
arr=(true false)

cycle() {
    printf '%s ' "${arr[${i:=0}]}"
    ((i=i>=${#arr[@]}-1?0:++i))
}
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 循环

## 循环遍历一系列数字

替换 `seq`.

```shell
# Loop from 0-100 (no variable support).
for i in {0..100}; do
    printf '%s\n' "$i"
done
```

## 循环遍历一个从0到变量的数字

替换 `seq`.

```shell
# Loop from 0-VAR.
VAR=50
for ((i=0;i<=VAR;i++)); do
    printf '%s\n' "$i"
done
```

## 循环遍历数组

```shell
arr=(apples oranges tomatoes)

# Just elements.
for element in "${arr[@]}"; do
    printf '%s\n' "$element"
done
```

## 通过索引循环遍历数组内容

```shell
arr=(apples oranges tomatoes)

# Elements and index.
for i in "${!arr[@]}"; do
    printf '%s\n' "${arr[i]}"
done

# Alternative method.
for ((i=0;i<${#arr[@]};i++)); do
    printf '%s\n' "${arr[i]}"
done
```

## 循环遍历文件内容

```shell
while read -r line; do
    printf '%s\n' "$line"
done < "file"
```

## 循环遍历文件和目录

不使用 `ls`.

```shell
# Greedy example.
for file in *; do
    printf '%s\n' "$file"
done

# PNG files in dir.
for file in ~/Pictures/*.png; do
    printf '%s\n' "$file"
done

# Iterate over directories.
for dir in ~/Downloads/*/; do
    printf '%s\n' "$dir"
done

# Brace Expansion.
for file in /path/to/parentdir/{file1,file2,subdir/file3}; do
    printf '%s\n' "$file"
done

# Iterate recursively.
shopt -s globstar
for file in ~/Pictures/**/*; do
    printf '%s\n' "$file"
done
shopt -u globstar
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 文件处理

**警告：** `bash` 在 `< 4.4` 版本中不能正确处理二进制数据。

## 文件读入到字符串

替代 `cat` 命令。

```shell
file_data="$(<"file")"
```

## 文件读入到数组 (*按行*)

替代 `cat` 命令。

```shell
# Bash <4
IFS=$'\n' read -d "" -ra file_data < "file"

# Bash 4+
mapfile -t file_data < "file"
```

## 获取文件的前N行

替代 `head` 命令

**CAVEAT:** Requires `bash` 4+

**示例函数：**

```sh
head() {
    # Usage: head "n" "file"
    mapfile -tn "$1" line < "$2"
    printf '%s\n' "${line[@]}"
}
```

**示例用法：**

```shell
$ head 2 ~/.bashrc
# Prompt
PS1='➜ '

$ head 1 ~/.bashrc
# Prompt
```

## 获取文件最后N行

替代 `tail` 命令。

**警告：** 需要 `bash` 4+

**示例函数：**

```sh
tail() {
    # Usage: tail "n" "file"
    mapfile -tn 0 line < "$2"
    printf '%s\n' "${line[@]: -$1}"
}
```

**示例用法：**

```shell
$ tail 2 ~/.bashrc
# Enable tmux.
# [[ -z "$TMUX"  ]] && exec tmux

$ tail 1 ~/.bashrc
# [[ -z "$TMUX"  ]] && exec tmux
```

## 获取文件行数

替代 `wc -l`.

**示例函数 (bash 4)：**

```sh
lines() {
    # Usage: lines "file"
    mapfile -tn 0 lines < "$1"
    printf '%s\n' "${#lines[@]}"
}
```

**示例函数 (bash 3)：**

This method uses less memory than the `mapfile` method and works in `bash` 3 but it is slower for bigger files.

```sh
lines_loop() {
    # Usage: lines_loop "file"
    count=0
    while IFS= read -r _; do
        ((count++))
    done < "$1"
    printf '%s\n' "$count"
}
```

**示例用法：**

```shell
$ lines ~/.bashrc
48

$ lines_loop ~/.bashrc
48
```

## 对目录中的文件或目录进行计数

它的工作原理是将glob的输出传递给函数，然后计算参数的数量。

**示例函数：**

```sh
count() {
    # Usage: count /path/to/dir/*
    #        count /path/to/dir/*/
    printf '%s\n' "$#"
}
```

**示例用法：**

```shell
# Count all files in dir.
$ count ~/Downloads/*
232

# Count all dirs in dir.
$ count ~/Downloads/*/
45

# Count all jpg files in dir.
$ count ~/Pictures/*.jpg
64
```

## 创建空文件

替代 `touch`.

```shell
# Shortest.
>file

# Longer alternatives:
:>file
echo -n >file
printf '' >file
```

## 提取两个标记之间的行

**示例函数：**

```sh
extract() {
    # Usage: extract file "opening marker" "closing marker"
    while IFS=$'\n' read -r line; do
        [[ $extract && $line != "$3" ]] &&
            printf '%s\n' "$line"

        [[ $line == "$2" ]] && extract=1
        [[ $line == "$3" ]] && extract=
    done < "$1"
}
```

**示例用法：**

```shell
# Extract code blocks from MarkDown file.
$ extract ~/projects/pure-bash/README.md '```sh' '```'
# Output here...
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# FILE PATHS

## Get the directory name of a file path

Alternative to the `dirname` command.

**Example Function:**

```sh
dirname() {
    # Usage: dirname "path"
    printf '%s\n' "${1%/*}/"
}
```

**Example Usage:**

```shell
$ dirname ~/Pictures/Wallpapers/1.jpg
/home/black/Pictures/Wallpapers/

$ dirname ~/Pictures/Downloads/
/home/black/Pictures/
```

## Get the base-name of a file path

Alternative to the `basename` command.

**Example Function:**

```sh
basename() {
    # Usage: basename "path"
    : "${1%/}"
    printf '%s\n' "${_##*/}"
}
```

**Example Usage:**

```shell
$ basename ~/Pictures/Wallpapers/1.jpg
1.jpg

$ basename ~/Pictures/Downloads/
Downloads
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# VARIABLES

## Assign and access a variable using a variable

```shell
$ hello_world="value"

# Create the variable name.
$ var="world"
$ ref="hello_$var"

# Print the value of the variable name stored in 'hello_$var'.
$ printf '%s\n' "${!ref}"
value
```

Alternatively, on `bash` 4.3+:

```shell
$ hello_world="value"
$ var="world"

# Declare a nameref.
$ declare -n ref=hello_$var

$ printf '%s\n' "$ref"
value
```

## Name a variable based on another variable

```shell
$ var="world"
$ declare "hello_$var=value"
$ printf '%s\n' "$hello_world"
value
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# ESCAPE SEQUENCES

Contrary to popular belief, there is no issue in utilizing raw escape sequences. Using `tput` abstracts the same ANSI sequences as if printed manually. Worse still, `tput` is not actually portable. There are a number of `tput` variants each with different commands and syntaxes (*try `tput setaf 3` on a FreeBSD system*). Raw sequences are fine.

## Text Colors

**NOTE:** Sequences requiring RGB values only work in True-Color Terminal Emulators.

| Sequence | What does it do? | Value |
| -------- | ---------------- | ----- |
| `\e[38;5;<NUM>m` | Set text foreground color. | `0-255`
| `\e[48;5;<NUM>m` | Set text background color. | `0-255`
| `\e[38;2;<R>;<G>;<B>m` | Set text foreground color to RGB color. | `R`, `G`, `B`
| `\e[48;2;<R>;<G>;<B>m` | Set text background color to RGB color. | `R`, `G`, `B`

## Text Attributes

| Sequence | What does it do? |
| -------- | ---------------- |
| `\e[m`  | Reset text formatting and colors.
| `\e[1m` | Bold text. |
| `\e[2m` | Faint text. |
| `\e[3m` | Italic text. |
| `\e[4m` | Underline text. |
| `\e[5m` | Slow blink. |
| `\e[7m` | Swap foreground and background colors. |


## Cursor Movement

| Sequence | What does it do? | Value |
| -------- | ---------------- | ----- |
| `\e[<LINE>;<COLUMN>H` | Move cursor to absolute position. | `line`, `column`
| `\e[H` | Move cursor to home position (`0,0`). |
| `\e[<NUM>A` | Move cursor up N lines. | `num`
| `\e[<NUM>B` | Move cursor down N lines. | `num`
| `\e[<NUM>C` | Move cursor right N columns. | `num`
| `\e[<NUM>D` | Move cursor left N columns. | `num`
| `\e[s` | Save cursor position. |
| `\e[u` | Restore cursor position. |


## Erasing Text

| Sequence | What does it do? |
| -------- | ---------------- |
| `\e[K` | Erase from cursor position to end of line.
| `\e[1K` | Erase from cursor position to start of line.
| `\e[2K` | Erase the entire current line.
| `\e[J` | Erase from the current line to the bottom of the screen.
| `\e[1J` | Erase from the current line to the top of the screen.
| `\e[2J` | Clear the screen.
| `\e[2J\e[H` | Clear the screen and move cursor to `0,0`.


<!-- CHAPTER END -->

<!-- CHAPTER START -->
# PARAMETER EXPANSION

## Indirection

| Parameter | What does it do? |
| --------- | ---------------- |
| `${!VAR}` | Access a variable based on the value of `VAR`.
| `${!VAR*}` | Expand to `IFS` separated list of variable names starting with `VAR`. |
| `${!VAR@}` | Expand to `IFS` separated list of variable names starting with `VAR`. If double-quoted, each variable name expands to a separate word. |


## Replacement

| Parameter | What does it do? |
| --------- | ---------------- |
| `${VAR#PATTERN}` | Remove shortest match of pattern from start of string. |
| `${VAR##PATTERN}` | Remove longest match of pattern from start of string. |
| `${VAR%PATTERN}` | Remove shortest match of pattern from end of string. |
| `${VAR%%PATTERN}` | Remove longest match of pattern from end of string. |
| `${VAR/PATTERN/REPLACE}` | Replace first match with string.
| `${VAR//PATTERN/REPLACE}` | Replace all matches with string.
| `${VAR/PATTERN}` | Remove first match.
| `${VAR//PATTERN}` | Remove all matches.

## Length

| Parameter | What does it do? |
| --------- | ---------------- |
| `${#VAR}` | Length of var in characters.
| `${#ARR[@]}` | Length of array in elements.

## Expansion

| Parameter | What does it do? |
| --------- | ---------------- |
| `${VAR:OFFSET}` | Remove first `N` chars from variable.
| `${VAR:OFFSET:LENGTH}` | Get substring from `N` character to `N` character. <br> (`${VAR:10:10}`: Get sub-string from char `10` to char `20`)
| `${VAR:: OFFSET}` | Get first `N` chars from variable.
| `${VAR:: -OFFSET}` | Remove last `N` chars from variable.
| `${VAR: -OFFSET}` | Get last `N` chars from variable.
| `${VAR:OFFSET:-OFFSET}` | Cut first `N` chars and last `N` chars. | `bash 4.2+` |

## Case Modification

| Parameter | What does it do? | CAVEAT |
| --------- | ---------------- | ------ |
| `${VAR^}` | Uppercase first character. | `bash 4+` |
| `${VAR^^}` | Uppercase all characters. | `bash 4+` |
| `${VAR,}` | Lowercase first character. | `bash 4+` |
| `${VAR,,}` | Lowercase all characters. | `bash 4+` |


## Default Value

| Parameter | What does it do? |
| --------- | ---------------- |
| `${VAR:-STRING}` | If `VAR` is empty or unset, use `STRING` as its value.
| `${VAR-STRING}` | If `VAR` is unset, use `STRING` as its value.
| `${VAR:=STRING}` | If `VAR` is empty or unset, set the value of `VAR` to `STRING`.
| `${VAR=STRING}` | If `VAR` is unset, set the value of `VAR` to `STRING`.
| `${VAR:+STRING}` | If `VAR` is not empty, use `STRING` as its value.
| `${VAR+STRING}` | If `VAR` is set, use `STRING` as its value.
| `${VAR:?STRING}` | Display an error if empty or unset.
| `${VAR?STRING}` | Display an error if unset.


<!-- CHAPTER END -->

<!-- CHAPTER START -->
# BRACE EXPANSION

## Ranges

```shell
# Syntax: {<START>..<END>}

# Print numbers 1-100.
echo {1..100}

# Print range of floats.
echo 1.{1..9}

# Print chars a-z.
echo {a..z}
echo {A..Z}

# Nesting.
echo {A..Z}{0..9}

# Print zero-padded numbers.
# CAVEAT: bash 4+
echo {01..100}

# Change increment amount.
# Syntax: {<START>..<END>..<INCREMENT>}
# CAVEAT: bash 4+
echo {1..10..2} # Increment by 2.
```

## String Lists

```shell
echo {apples,oranges,pears,grapes}

# Example Usage:
# Remove dirs Movies, Music and ISOS from ~/Downloads/.
rm -rf ~/Downloads/{Movies,Music,ISOS}
```

<!-- CHAPTER END -->


<!-- CHAPTER START -->

# CONDITIONAL EXPRESSIONS

## File Conditionals

| Expression | Value  | What does it do? |
| ---------- | ------ | ---------------- |
| `-a`       | `file` | If file exists.
| `-b`       | `file` | If file exists and is a block special file.
| `-c`       | `file` | If file exists and is a character special file.
| `-d`       | `file` | If file exists and is a directory.
| `-e`       | `file` | If file exists.
| `-f`       | `file` | If file exists and is a regular file.
| `-g`       | `file` | If file exists and its set-group-id bit is set.
| `-h`       | `file` | If file exists and is a symbolic link.
| `-k`       | `file` | If file exists and its sticky-bit is set
| `-p`       | `file` | If file exists and is a named pipe (*FIFO*).
| `-r`       | `file` | If file exists and is readable.
| `-s`       | `file` | If file exists and its size is greater than zero.
| `-t`       | `fd`   | If file descriptor is open and refers to a terminal.
| `-u`       | `file` | If file exists and its set-user-id bit is set.
| `-w`       | `file` | If file exists and is writable.
| `-x`       | `file` | If file exists and is executable.
| `-G`       | `file` | If file exists and is owned by the effective group ID.
| `-L`       | `file` | If file exists and is a symbolic link.
| `-N`       | `file` | If file exists and has been modified since last read.
| `-O`       | `file` | If file exists and is owned by the effective user ID.
| `-S`       | `file` | If file exists and is a socket.

## File Comparisons

| Expression | What does it do? |
| ---------- | ---------------- |
| `file -ef file2` | If both files refer to the same inode and device numbers.
| `file -nt file2` | If `file` is newer than `file2` (*uses modification time*) or `file` exists and `file2` does not.
| `file -ot file2` | If `file` is older than `file2` (*uses modification time*) or `file2` exists and `file` does not.

## Variable Conditionals

| Expression | Value | What does it do? |
| ---------- | ----- | ---------------- |
| `-o`       | `opt` | If shell option is enabled.
| `-v`       | `var` | If variable has a value assigned.
| `-R`       | `var` | If variable is a name reference.
| `-z`       | `var` | If the length of string is zero.
| `-n`       | `var` | If the length of string is non-zero.

## Variable Comparisons

| Expression | What does it do? |
| ---------- | ---------------- |
| `var = var2` | Equal to.
| `var == var2` | Equal to (*synonym for `=`*).
| `var != var2` | Not equal to.
| `var < var2` | Less than (*in ASCII alphabetical order.*)
| `var > var2` | Greater than (*in ASCII alphabetical order.*)

<!-- CHAPTER END -->

<!-- CHAPTER START -->

# ARITHMETIC OPERATORS

## Assignment

| Operators | What does it do? |
| --------- | ---------------- |
| `=`       | Initialize or change the value of a variable.

## Arithmetic

| Operators | What does it do? |
| --------- | ---------------- |
| `+` | Addition
| `-` | Subtraction
| `*` | Multiplication
| `/` | Division
| `**` | Exponentiation
| `%` | Modulo
| `+=` | Plus-Equal (*Increment a variable.*)
| `-=` | Minus-Equal (*Decrement a variable.*)
| `*=` | Times-Equal (*Multiply a variable.*)
| `/=` | Slash-Equal (*Divide a variable.*)
| `%=` | Mod-Equal (*Remainder of dividing a variable.*)

## Bitwise

| Operators | What does it do? |
| --------- | ---------------- |
| `<<` | Bitwise Left Shift
| `<<=` | Left-Shift-Equal
| `>>` | Bitwise Right Shift
| `>>=` | Right-Shift-Equal
| `&` | Bitwise AND
| `&=` | Bitwise AND-Equal
| `\|` | Bitwise OR
| `\|=` | Bitwise OR-Equal
| `~` | Bitwise NOT
| `^` | Bitwise XOR
| `^=` | Bitwise XOR-Equal

## Logical

| Operators | What does it do? |
| --------- | ---------------- |
| `!` | NOT
| `&&` | AND
| `\|\|` | OR

## Miscellaneous

| Operators | What does it do? | Example |
| --------- | ---------------- | ------- |
| `,` | Comma Separator | `((a=1,b=2,c=3))`


<!-- CHAPTER END -->

<!-- CHAPTER START -->
# ARITHMETIC

## Simpler syntax to set variables

```shell
# Simple math
((var=1+2))

# Decrement/Increment variable
((var++))
((var--))
((var+=1))
((var-=1))

# Using variables
((var=var2*arr[2]))
```

## Ternary Tests

```shell
# Set the value of var to var2 if var2 is greater than var.
# var: variable to set.
# var2>var: Condition to test.
# ?var2: If the test succeeds.
# :var: If the test fails.
((var=var2>var?var2:var))
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# TRAPS

Traps allow a script to execute code on various signals. In [pxltrm](https://github.com/dylanaraps/pxltrm) (*a pixel art editor written in bash*)  traps are used to redraw the user interface on window resize. Another use case is cleaning up temporary files on script exit.

Traps should be added near the start of scripts so any early errors are also caught.

**NOTE:** For a full list of signals, see `trap -l`.


## Do something on script exit

```shell
# Clear screen on script exit.
trap 'printf \\e[2J\\e[H\\e[m' EXIT
```

## Ignore terminal interrupt (CTRL+C, SIGINT)

```shell
trap '' INT
```

## React to window resize

```shell
# Call a function on window resize.
trap 'code_here' SIGWINCH
```

## Do something before every command

```shell
trap 'code_here' DEBUG
```

## Do something when a shell function or a sourced file finishes executing

```shell
trap 'code_here' RETURN
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# PERFORMANCE

## Disable Unicode

If unicode is not required, it can be disabled for a performance increase. Results may vary however there have been noticeable improvements in [neofetch](https://github.com/dylanaraps/neofetch) and other programs.

```shell
# Disable unicode.
LC_ALL=C
LANG=C
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# OBSOLETE SYNTAX

## Shebang

Use `#!/usr/bin/env bash` instead of `#!/bin/bash`.

- The former searches the user's `PATH` to find the `bash` binary.
- The latter assumes it is always installed to `/bin/` which can cause issues.

```shell
# Right:

    #!/usr/bin/env bash

# Wrong:

    #!/bin/bash
```

## Command Substitution

Use `$()` instead of `` ` ` ``.

```shell
# Right.
var="$(command)"

# Wrong.
var=`command`

# $() can easily be nested whereas `` cannot.
var="$(command "$(command)")"
```

## Function Declaration

Do not use the `function` keyword, it reduces compatibility with older versions of `bash`.

```shell
# Right.
do_something() {
    # ...
}

# Wrong.
function do_something() {
    # ...
}
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# INTERNAL VARIABLES

## Get the location to the `bash` binary

```shell
"$BASH"
```

## Get the version of the current running `bash` process

```shell
# As a string.
"$BASH_VERSION"

# As an array.
"${BASH_VERSINFO[@]}"
```

## Open the user's preferred text editor

```shell
"$EDITOR" "$file"

# NOTE: This variable may be empty, set a fallback value.
"${EDITOR:-vi}" "$file"
```

## Get the name of the current function

```shell
# Current function.
"${FUNCNAME[0]}"

# Parent function.
"${FUNCNAME[1]}"

# So on and so forth.
"${FUNCNAME[2]}"
"${FUNCNAME[3]}"

# All functions including parents.
"${FUNCNAME[@]}"
```

## Get the host-name of the system

```shell
"$HOSTNAME"

# NOTE: This variable may be empty.
# Optionally set a fallback to the hostname command.
"${HOSTNAME:-$(hostname)}"
```

## Get the architecture of the Operating System

```shell
"$HOSTTYPE"
```

## Get the name of the Operating System / Kernel

This can be used to add conditional support for different Operating
Systems without needing to call `uname`.

```shell
"$OSTYPE"
```

## Get the current working directory

This is an alternative to the `pwd` built-in.

```shell
"$PWD"
```

## Get the number of seconds the script has been running

```shell
"$SECONDS"
```

## Get a pseudorandom integer

Each time `$RANDOM` is used, a different integer between `0` and `32767` is returned. This variable should not be used for anything related to security (*this includes encryption keys etc*).


```shell
"$RANDOM"
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# INFORMATION ABOUT THE TERMINAL

## Get the terminal size in lines and columns (*from a script*)

This is handy when writing scripts in pure bash and `stty`/`tput` can’t be
called.

**Example Function:**

```sh
get_term_size() {
    # Usage: get_term_size

    # (:;:) is a micro sleep to ensure the variables are
    # exported immediately.
    shopt -s checkwinsize; (:;:)
    printf '%s\n' "$LINES $COLUMNS"
}
```

**Example Usage:**

```shell
# Output: LINES COLUMNS
$ get_term_size
15 55
```

## Get the terminal size in pixels

**CAVEAT**: This does not work in some terminal emulators.

**Example Function:**

```sh
get_window_size() {
    # Usage: get_window_size
    printf '%b' "${TMUX:+\\ePtmux;\\e}\\e[14t${TMUX:+\\e\\\\}"
    IFS=';t' read -d t -t 0.05 -sra term_size
    printf '%s\n' "${term_size[1]}x${term_size[2]}"
}
```

**Example Usage:**

```shell
# Output: WIDTHxHEIGHT
$ get_window_size
1200x800

# Output (fail):
$ get_window_size
x
```

## Get the current cursor position

This is useful when creating a TUI in pure bash.

**Example Function:**

```sh
get_cursor_pos() {
    # Usage: get_cursor_pos
    IFS='[;' read -p $'\e[6n' -d R -rs _ y x _
    printf '%s\n' "$x $y"
}
```

**Example Usage:**

```shell
# Output: X Y
$ get_cursor_pos
1 8
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# CONVERSION

## Convert a hex color to RGB

**Example Function:**

```sh
hex_to_rgb() {
    # Usage: hex_to_rgb "#FFFFFF"
    #        hex_to_rgb "000000"
    : "${1/\#}"
    ((r=16#${_:0:2},g=16#${_:2:2},b=16#${_:4:2}))
    printf '%s\n' "$r $g $b"
}
```

**Example Usage:**

```shell
$ hex_to_rgb "#FFFFFF"
255 255 255
```


## Convert an RGB color to hex

**Example Function:**

```sh
rgb_to_hex() {
    # Usage: rgb_to_hex "r" "g" "b"
    printf '#%02x%02x%02x\n' "$1" "$2" "$3"
}
```

**Example Usage:**

```shell
$ rgb_to_hex "255" "255" "255"
#FFFFFF
```


# CODE GOLF

## Shorter `for` loop syntax

```shell
# Tiny C Style.
for((;i++<10;)){ echo "$i";}

# Undocumented method.
for i in {1..10};{ echo "$i";}

# Expansion.
for i in {1..10}; do echo "$i"; done

# C Style.
for((i=0;i<=10;i++)); do echo "$i"; done
```

## Shorter infinite loops

```shell
# Normal method
while :; do echo hi; done

# Shorter
for((;;)){ echo hi;}
```

## Shorter function declaration

```shell
# Normal method
f(){ echo hi;}

# Using a subshell
f()(echo hi)

# Using arithmetic
# This can be used to assign integer values.
# Example: f a=1
#          f a++
f()(($1))

# Using tests, loops etc.
# NOTE: ‘while’, ‘until’, ‘case’, ‘(())’, ‘[[]]’ can also be used.
f()if true; then echo "$1"; fi
f()for i in "$@"; do echo "$i"; done
```

## Shorter `if` syntax

```shell
# One line
# Note: The 3rd statement may run when the 1st is true
[[ $var == hello ]] && echo hi || echo bye
[[ $var == hello ]] && { echo hi; echo there; } || echo bye

# Multi line (no else, single statement)
# Note: The exit status may not be the same as with an if statement
[[ $var == hello ]] &&
    echo hi

# Multi line (no else)
[[ $var == hello ]] && {
    echo hi
    # ...
}
```

## Simpler `case` statement to set variable

The `:` built-in can be used to avoid repeating `variable=` in a case statement. The `$_` variable stores the last argument of the last command. `:` always succeeds so it can be used to store the variable value.

```shell
# Modified snippet from Neofetch.
case "$OSTYPE" in
    "darwin"*)
        : "MacOS"
    ;;

    "linux"*)
        : "Linux"
    ;;

    *"bsd"* | "dragonfly" | "bitrig")
        : "BSD"
    ;;

    "cygwin" | "msys" | "win32")
        : "Windows"
    ;;

    *)
        printf '%s\n' "Unknown OS detected, aborting..." >&2
        exit 1
    ;;
esac

# Finally, set the variable.
os="$_"
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# OTHER

## Use `read` as an alternative to the `sleep` command

Surprisingly, `sleep` is an external command and not a `bash` built-in.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
read_sleep() {
    # Usage: sleep 1
    #        sleep 0.2
    read -rst "${1:-1}" -N 999
}
```

**Example Usage:**

```shell
read_sleep 1
read_sleep 0.1
read_sleep 30
```

## Check if a program is in the user's PATH

```shell
# There are 3 ways to do this and either one can be used.
type -p executable_name &>/dev/null
hash executable_name &>/dev/null
command -v executable_name &>/dev/null

# As a test.
if type -p executable_name &>/dev/null; then
    # Program is in PATH.
fi

# Inverse.
if ! type -p executable_name &>/dev/null; then
    # Program is not in PATH.
fi

# Example (Exit early if program is not installed).
if ! type -p convert &>/dev/null; then
    printf '%s\n' "error: convert is not installed, exiting..."
    exit 1
fi
```

## Get the current date using `strftime`

Bash’s `printf` has a built-in method of getting the date which can be used in place of the `date` command.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
date() {
    # Usage: date "format"
    # See: 'man strftime' for format.
    printf "%($1)T\\n" "-1"
}
```

**Example Usage:**

```shell
# Using above function.
$ date "%a %d %b  - %l:%M %p"
Fri 15 Jun  - 10:00 AM

# Using printf directly.
$ printf '%(%a %d %b  - %l:%M %p)T\n' "-1"
Fri 15 Jun  - 10:00 AM

# Assigning a variable using printf.
$ printf -v date '%(%a %d %b  - %l:%M %p)T\n' '-1'
$ printf '%s\n' "$date"
Fri 15 Jun  - 10:00 AM
```

## Get the username of the current user

**CAVEAT:** Requires `bash` 4.4+

```shell
$ : \\u
# Expand the parameter as if it were a prompt string.
$ printf '%s\n' "${_@P}"
black
```

## Generate a UUID V4

**CAVEAT**: The generated value is not cryptographically secure.

**Example Function:**

```sh
uuid() {
    # Usage: uuid
    C="89ab"

    for ((N=0;N<16;++N)); do
        B="$((RANDOM%256))"

        case "$N" in
            6)  printf '4%x' "$((B%16))" ;;
            8)  printf '%c%x' "${C:$RANDOM%${#C}:1}" "$((B%16))" ;;

            3|5|7|9)
                printf '%02x-' "$B"
            ;;

            *)
                printf '%02x' "$B"
            ;;
        esac
    done

    printf '\n'
}
```

**Example Usage:**

```shell
$ uuid
d5b6c731-1310-4c24-9fe3-55d556d44374
```

## Progress bars

This is a simple way of drawing progress bars without needing a for loop
in the function itself.

**Example Function:**

```sh
bar() {
    # Usage: bar 1 10
    #            ^----- Elapsed Percentage (0-100).
    #               ^-- Total length in chars.
    ((elapsed=$1*$2/100))

    # Create the bar with spaces.
    printf -v prog  "%${elapsed}s"
    printf -v total "%$(($2-elapsed))s"

    printf '%s\r' "[${prog// /-}${total}]"
}
```

**Example Usage:**

```shell
for ((i=0;i<=100;i++)); do
    # Pure bash micro sleeps (for the example).
    (:;:) && (:;:) && (:;:) && (:;:) && (:;:)

    # Print the bar.
    bar "$i" "10"
done

printf '\n'
```

## Get the list of functions in a script

```sh
get_functions() {
    # Usage: get_functions
    IFS=$'\n' read -d "" -ra functions < <(declare -F)
    printf '%s\n' "${functions[@]//declare -f }"
}
```

## Bypass shell aliases

```shell
# alias
ls

# command
# shellcheck disable=SC1001
\ls
```

## Bypass shell functions

```shell
# function
ls

# command
command ls
```

## Run a command in the background

This will run the given command and keep it running, even after the terminal or SSH connection is terminated. All output is ignored.

```sh
bkr() {
    (nohup "$@" &>/dev/null &)
}

bkr ./some_script.sh # some_script.sh is now running in the background
```

<!-- CHAPTER END -->

# 后记

谢谢你的阅读！如果这本圣经在任何方面帮助了你，你想回报，考虑捐赠。捐款使我有更多的时间来使这项目变得更好。不能捐献？没关系，给本项目来个 star 然后和你的朋友分享我们的项目吧！

<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=V7QNJNKS3WYVS"><img src="https://img.shields.io/badge/donate-paypal-yellow.svg"></a> <a href="https://www.patreon.com/dyla"><img src="https://img.shields.io/badge/donate-patreon-yellow.svg"> </a><a href="https://liberapay.com/2211/"><img src="https://img.shields.io/badge/donate-liberapay-yellow.svg"></a>


嗨起来吧！ 🤘
