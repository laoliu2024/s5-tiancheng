# 来自天成脚本的socks5-hysteria2-for-serv00-ct8
- 给 serv00 & ct8 机器一键安装 socks5 & hysteria2 & nezha-agent
- CT8目前不推荐安装哪吒探针，安装探针容易封号。
- serv00 & CT8 请勿安装PM2，安装PM2容易封号。
- 在面板Additional servoces里打开Run your own applications为Enable
- 在面板Port reservation里添加 Add port 开放UDP和TCP端口
- Hysteria2用UDP端口，Socks5用TCP端口
- 如果你只是为了保活登陆，serv00 ct8可以不安装任何东西，只需设置Github Actions保活
- 如果安装部署过其它脚本，请你在安装此脚本之前用下面的清理服务器命令清除一次服务器后再安装！！！！！！
## 一键脚本
- 推荐Socks5 hysteria2 nohup模式
```bash
bash <(curl -s https://raw.githubusercontent.com/gshtwy/socks5-for-serv00/main/install-socks5-hysteria.sh)
```
- Socks5 pm2模式
```bash
bash <(curl -s https://raw.githubusercontent.com/gshtwy/socks5-for-serv00/main/install-socks5-pm2.sh)
```

卸载pm2
```bash
pm2 unstartup
pm2 delete all
npm uninstall -g pm2
```
## 清理服务器

```bash
pkill -kill -u 用户名
chmod -R 755 ~/* 
chmod -R 755 ~/.* 
rm -rf ~/.* 
rm -rf ~/*
```

## Github Actions保活
添加 Secrets.`ACCOUNTS_JSON` 变量
```json
[
  {"username": "cmliusss", "password": "7HEt(xeRxttdvgB^nCU6", "panel": "panel4.serv00.com", "ssh": "s4.serv00.com"},
  {"username": "cmliussss2018", "password": "4))@cRP%HtN8AryHlh^#", "panel": "panel7.serv00.com", "ssh": "s7.serv00.com"},
  {"username": "4r885wvl", "password": "%Mg^dDMo6yIY$dZmxWNy", "panel": "panel.ct8.pl", "ssh": "s1.ct8.pl"}
]
```
# cloudflare worker部署保活
## cloudflare 部署步骤
- 复制worker.js代码到cloudflare Workers保存
- Workers设置变量名称，添加 ACCOUNTS_JSON TELEGRAM_JSON 值，替换自己的账号 密码 面板
- 在设置里设置Cron 触发器，设置触发时间。

## worker部署变量
添加变量名称 ACCOUNTS_JSON 
添加变量值，复制下面代码替换成自己的账号 密码 面板

```json
[  
  { "username": "serv00user1", "password": "serv00password1", "panelnum": "0", "type": "serv00" },
  { "username": "serv00user2", "password": "serv00password2", "panelnum": "4", "type": "serv00" },
  { "username": "serv00user3", "password": "serv00password3", "panelnum": "7", "type": "serv00" },
  { "username": "ct8user1", "password": "ct8password1", "type": "ct8" },
  { "username": "ct8user2", "password": "ct8password2", "type": "ct8" }
]
```

添加变量名称 TELEGRAM_JSON 
添加变量值，复制下面代码替换成自己的TG TOKEN ID

```json
{
  "telegramBotToken": "YOUR_BOT_TOKEN",
  "telegramBotUserId": "YOUR_USER_ID"
}
```


