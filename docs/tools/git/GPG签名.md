使用GPG签名

以下是按照local配置，要配置成global加上--global即可

## 生成密钥对

- 密钥种类：选择默认 RSA and RSA 即可；
- 密钥长度：GitHub 的要求是 4096 bits；
- 密钥过期时间：按需选择；
- 用户 ID 和邮箱：github用户名和邮箱。

```shell
$ gpg --full-generate-key
gpg (GnuPG) 2.2.29-unknown; Copyright (C) 2021 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
  (14) Existing key from card
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: 用户名
Email address: 邮箱
Comment: test
You selected this USER-ID:
    "XXXXXXXXXXXXXXXXXXXX"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?
Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 2881B9F9F1FC944E marked as ultimately trusted
gpg: revocation certificate stored as '/c/Users/XXX/.gnupg/openpgp-revocs.d/XXXXXXXXXXXXXXX.rev'这里是密钥文件位置
public and secret key created and signed.

pub   rsa4096 2024-03-17 [SC]
      密钥对内容XXXXX
uid                      用户信息XXXXX
sub   rsa4096 2024-03-17 [E]


```

## 添加至github关联

```

$ gpg --armor --export 密钥对内容
XXXXXXXXXXXXXXXXXXXXXXXX（全部复制到github）
```

setting-->ssh和GPG ，创建

## 关联本地仓库

```
git config user.signingkey 密钥对内容

git config commit.gpgsign true


```

## 签名

```
git add .

git commit -s -S -m "update"

git push
 
```

