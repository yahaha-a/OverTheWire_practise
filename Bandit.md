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
6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```

</details>

<details open>
<summary>Level 11 -> Level 12</summary>

```
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
ssh bandit12@bandit.labs.overthewire.org -p 2220
JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```

</details>

<details open>
<summary>Level 12 -> Level 13</summary>

xxd: 将十六进制转储文件转换为二进制文件

```
mkdir /tmp/mydir

cp data.txt /tmp/mydir/myfile.hex

cd /tmp/mydir

xxd -r myfile.hex > binary_data

file binary_data

mv binary_data binary_data.gz

gzip -d binary_data.gz

tar xf data2.bin

bunzip2 data6.bin

ssh bandit13@bandit.labs.overthewire.org -p 2220
wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
```

</details>

<details open>
<summary>Level 13 -> Level 14</summary>

```
ssh -i sshkey.private -p 2220 bandit14@localhost

cat /etc/bandit_pass/bandit14

ssh bandit14@bandit.labs.overthewire.org -p 2220
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
```

</details>

<details open>
<summary>Level 14 -> Level 15</summary>

```
echo "fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq" | nc localhost 30000

ssh bandit15@bandit.labs.overthewire.org -p 2220
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```

</details>

<details open>
<summary>Level 15 -> Level 16</summary>

```
echo "jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt" | openssl s_client -connect localhost:30001 -ign_eof

ssh bandit16@bandit.labs.overthewire.org -p 2220
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```

</details>

<details open>
<summary>Level 16 -> Level 17</summary>

```
echo "JQttfApK4SeyHwDlI9SXGR50qclOAil1" | openssl s_client -connect localhost:31790 -ign_eof

nano /tmp/bandit17.sshkey

chmod 600 /tmp/bandit17.sshkey

ssh -i /tmp/bandit17.sshkey -p 2220 bandit17@localhost

cat /etc/bandit_pass/bandit17

ssh bandit17@bandit.labs.overthewire.org -p 2220
VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e
```

</details>

<details open>
<summary>Level 17 -> Level 18</summary>

```
diff passwords.old passwords.new | grep "^>"

ssh bandit18@bandit.labs.overthewire.org -p 2220
hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
```

</details>

<details open>
<summary>Level 18 -> Level 19</summary>

```
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat ./readme"

ssh bandit19@bandit.labs.overthewire.org -p 2220
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```

</details>

<details open>
<summary>Level 19 -> Level 20</summary>

```
ls

./bandit20-do

./bandit20-do cat /etc/bandit_pass/bandit20

ssh bandit20@bandit.labs.overthewire.org -p 2220
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
```

</details>

<details open>
<summary>Level 20 -> Level 21</summary>

```
ls

./suconnect

echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | nc -l -p 30088 &

./suconnect 30088

ssh bandit21@bandit.labs.overthewire.org -p 2220
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
```

</details>

<details open>
<summary>Level 21 -> Level 22</summary>

```
ls /etc/cron.d

cat /etc/cron.d/cronjob_bandit22

cat /usr/bin/cronjob_bandit22.sh

cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

ssh bandit22@bandit.labs.overthewire.org -p 2220
WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
```

</details>

<details open>
<summary>Level 22 -> Level 23</summary>

```
cd /etc/cron.d

ls

cat cronjob_bandit23

cat /usr/bin/cronjob_bandit23.sh

echo I am user bandit23 | md5sum | cut -d ' ' -f 1

cat /tmp/8ca319486bfbbc3663ea0fbe81326349

ssh bandit23@bandit.labs.overthewire.org -p 2220
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
```

</details>

<details open>
<summary>Level 23 -> Level 24</summary>

```
cd /etc/cron.d

ls

cat cronjob_bandit24

cat /usr/bin/cronjob_bandit24.sh

cd /tmp

nano get_24pass.sh
#!/bin/bash
chmod +x ./get_24pass.sh
cat /etc/bandit_pass/bandit24 > /tmp/bandit24pass

cd /var/spool/bandit24/foo

cp /tmp/get_24pass.sh /var/spool/bandit24/foo

chmod +x ./get_24pass.sh

cat /tmp/bandit24pass

ssh bandit24@bandit.labs.overthewire.org -p 2220
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
```

</details>

<details open>
<summary>Level 24 -> Level 25</summary>

```
for pin in {9000..9999}; do
    echo $(cat /etc/bandit_pass/bandit24) $pin | tee -a ./bandit25pin
done

cat ./bandit25pin | nc localhost 30002 | tee ./bandit25pass

ssh bandit25@bandit.labs.overthewire.org -p 2220
p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d
```

</details>

<details open>
<summary>Level 25 -> Level 26</summary>

```
cat /etc/passwd|grep bandit26

cat /usr/bin/showtext

ls

ssh -i bandit26.sshkey -p 2220 bandit26@localhost
#调小终端

:r /etc/bandit_pass/bandit26

ssh bandit26@bandit.labs.overthewire.org -p 2220
c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
```

</details>

<details open>
<summary>Level 26 -> Level 27</summary>

```
:set shell sh=/bin/sh

:sh

$ ls

$ ls -al

$ ./bandit27-do

$ ./bandit27-do cat /etc/bandit_pass/bandit27

ssh bandit27@bandit.labs.overthewire.org -p 2220
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
```

</details>

<details open>
<summary>Level 27 -> Level 28</summary>

```
cd /tmp

git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo /tmp/repo_new

cd repo_new

ls

cat README

ssh bandit28@bandit.labs.overthewire.org -p 2220
AVanL161y9rsbcJIsFHuw35rjaOM19nR
```

</details>

<details open>
<summary>Level 28 -> Level 29</summary>

```
git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo /tmp/repo_28

cd /tmp/repo_28

ls

cat README.md

git show

ssh bandit29@bandit.labs.overthewire.org -p 2220
tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S
```

</details>

<details open>
<summary>Level 29 -> Level 30</summary>

```
git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo /tmp/repo_29

ls

cat README.md

git branch -a

git checkout dev

cat README.md

ssh bandit30@bandit.labs.overthewire.org -p 2220
xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS
```

</details>
