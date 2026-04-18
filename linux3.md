## 创建软链接

```bash
sudo ln -s /usr/local/toolchain/toolchain-4.6.4/bin/arm-none-linux-gnueabi-g++ /usr/bin/
```

## 查看用户信息

```bash
id
# Windows
whoami
```

## 查看目录所有者

```bash
ls -ln
# Windows
(Get-Acl .).Owner
```
