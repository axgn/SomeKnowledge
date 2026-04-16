按类别整理（偏实用、简洁）：

---

## 一、文件与目录

* `ls`：列出目录

  * `ls -l` 详细信息
  * `ls -a` 显示隐藏文件

* `cd`：切换目录

* `pwd`：当前路径

* `mkdir dir`：创建目录

* `rm file`：删除文件

  * `rm -r dir` 删除目录
  * `rm -rf dir` 强制删除

* `cp src dst`：复制

  * `cp -r dir1 dir2`

* `mv src dst`：移动/重命名

---

## 二、文件查看与编辑

* `cat file`：输出全部内容

* `less file`：分页查看（推荐）

* `head -n 10 file`：前10行

* `tail -n 10 file`：后10行

  * `tail -f log` 实时日志

* `vim file`：编辑（你偏好这个）

---

## 三、查找


  ```bash
  find . -name "*.cpp"
  ```


  ```bash
  grep "main" file.cpp
  grep -r "main" .
  ```

---

## 四、权限与属性


  ```bash
  chmod +x file
  chmod 755 file
  ```


  ```bash
  chown user:group file
  ```

---

## 五、压缩与解压

  ```bash
  tar -czf a.tar.gz dir     # 压缩 -z gz 
  tar -xzf a.tar.gz        # 解压 -J xz
  ```


  ```bash
  zip -r a.zip dir
  unzip a.zip
  ```

---

## 六、进程管理

* `ps aux`：查看进程

* `top` / `htop`：实时监控

* `kill PID`：结束进程

  * `kill -9 PID` 强制杀死

---

## 七、网络

* `ip a`：查看IP

* `ping`：测试连通性

* `curl`：请求接口

  ```bash
  curl https://example.com
  ```

* `wget`：下载文件

* `ss -tuln`：查看端口
  （或 `netstat`）

---

## 八、磁盘与系统

* `df -h`：磁盘使用

* `du -sh dir`：目录大小

* `free -h`：内存

* `uname -a`：系统信息

---

## 九、用户与环境

* `whoami`：当前用户
* `env`：环境变量
* `export VAR=xxx`

---

## 十、重定向与管道（核心）


  ```bash
  cmd > file
  cmd >> file
  ```


  ```bash
  ps aux | grep nginx
  ```

---

## 十一、常用组合（很重要）

* 查端口占用

  ```bash
  ss -tuln | grep 8080
  ```

* 实时看日志并过滤

  ```bash
  tail -f log | grep error
  ```

* 统计行数

  ```bash
  wc -l file
  ```

---

## 十二、包管理（Ubuntu）

* `apt update`
* `apt install pkg`
* `apt remove pkg`

