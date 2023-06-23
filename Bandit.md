<details open>
<summary>Level 0</summary>

通过 SSH 连接到 OverTheWire 的 Bandit 服务器的命令。其中，bandit0 是用户名，bandit.labs.overthewire.org 是服务器地址，-p 2220 是指定连接端口。
密码是bandit0
  
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

```
bandit0
```

</details>

<details open>
<summary>Level 0 -> Level 1</summary>

ls: 列出当前文件的文件与文件夹


```
ls
```

cat: 显示文件内容即密码

```
cat readme
```

ctrl+d 断开与服务器连接，登陆bandit1

```
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 1 -> Level 2</summary>

```
ls
```

-比较特殊

```
cat ./-
```

ctrl+d

```
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 2 -> Level 3</summary>

含有空格需进行转义

```
ls

cat "spaces in this filename"

ssh bandit3@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 3 -> Level 4</summary>

```
ls

cd inhere

cat .hidden

ssh bandit4@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 4 -> Level 5</summary>

file: 检查文件类型

```
cd inhere

ls

file ./-file07

cat ./-file07

ssh bandit5@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 5 -> Level 6</summary>

-type f：文件类型为普通文件
-readable：文件可读
-size 1033c：文件大小为 1033 字节
! -executable：文件不可执行

```
cd inhere

find . -type f -readable -size 1033c ! -executable

cat ./maybehere07/.file2

ssh bandit6@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 6 -> Level 7</summary>

/: 从根目录开始
-user bandit7：文件所有者为 bandit7
-group bandit6：文件所属组为 bandit6
-size 33c：文件大小为 33 字节
2>/dev/null 是一种重定向操作，用于将标准错误输出（标准错误流，标识符为2）重定向到特殊设备文件 /dev/null 中

```
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null

cat /var/lib/dpkg/info/bandit7.password

ssh bandit7@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 7 -> Level 8</summary>

head: 查看文件结构
grep: 正则匹配紧邻单词 "millionth" 旁边的内容
-o 选项表示只输出匹配到的部分，而不是整行。默认情况下，grep 输出整行匹配的内容，但使用 -o 选项可以只输出匹配部分。
-P 选项表示使用 Perl 兼容的正则表达式模式进行匹配。Perl 正则表达式提供了更多的功能和语法，相对于标准的基本正则表达式（BRE）或扩展正则表达式（ERE），更为强大和灵活。

```
head -n 10 data.txt

grep -oP '(?<=millionth\s)\S+' data.txt

ssh bandit8@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 8 -> Level 9</summary>

cat data.txt：将文件 data.txt 的内容输出到标准输出。
sort：对输入进行排序。
uniq -u：只输出唯一的行，即只输出没有重复出现的行。
在使用 uniq -u 命令之前对数据进行排序的原因是，uniq 命令要求输入的数据是有序的。它会检查连续的行并删除重复的行，但只有当相邻行是重复的时候才会删除。因此，在应用 uniq -u 命令之前，我们需要对数据进行排序，以确保相同的行是连续的。

```
cat data.txt | sort | uniq -u

ssh bandit9@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 9 -> Level 10</summary>

strings: 提取文件中的人类可读字符串
grep: ^ 表示行的开头，.* 表示任意数量的字符，$ 表示行的结尾。这个模式表示匹配以 "=" 开头，以任意字符结尾的行，即满足要求的字符串行。

```
strings data.txt | grep "^=.*$"

ssh bandit10@bandit.labs.overthewire.org -p 2220
```

</details>

<details open>
<summary>Level 10 -> Level 11</summary>

Base64是一种用于将二进制数据转换为文本格式的编码方式。它将任意二进制数据转换为由 64 个不同字符组成的文本字符串。Base64 编码常用于在文本协议中传输或存储二进制数据，例如在电子邮件中传输附件或在网页中嵌入图像。

```
cat data.txt | base64 -d

ssh bandit11@bandit.labs.overthewire.org -p 2220
```

6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

</details>
