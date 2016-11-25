# image: philoles/docker-mail-forwarder

From zixia/simple-mail-forwarder

# 转发邮件

先查看一下25端口是否被占用

```bash
docker run -d -e SMF_CONFIG="forward@xx.com:receive@xx.com" -p 25:25 philoles/docker-mail-forwarder
```
forward@xx.com转发到receive@xx.com, 需要把xx.com的mx记录设置到指向服务器的域名

* 如果要转发某个域名的全部邮件

```bash
SMF_CONFIG='@testo.com:all@test.com'
```
所有testo.com的邮件会转发到all@test.com

* 转发给多个邮箱

```bash
SMF_CONFIG='testi@testo.com:test1@test.com|test2@test.com|test3@test.com'
```

* 设置多个规则，用分号分隔

```bash
SMF_CONFIG='testi@testo.com:test@test.com;testo@testi.com:test@test.com'
```