# XMU每日打卡

此项目托管于``Github Action``进行XMU的每日健康打卡，仅供交流学习使用。
由于XMU系统事故频发及本脚本使用比较简单暴力的selenium，打卡运行会时不时出错（成功率大概在80%以上），若出错，可选择手动执行一次或手动打卡。
本脚本后续不再更新，若出现打卡页面变更，请自行修改网址/元素路径。

## Action执行打卡

1. Fork本项目；
2. 在`Settings->Secrets`下新建两个`Secrets`：
   + `USERNAME`：你的XMU用户名
   + `PASSWD`：统一身份认证的密码
   + `PASSWD_VPN`: WebVPN密码，若和统一身份认证密码不一致，请自行到`py`文件中修改`passwd_vpn`字段从环境中读取的值为`PASSWD_VPN`，此脚本中默认为一致，直接读取`PASSWD`并无需添加此字段
3. 在`Action`下允许`workflow`运行；
4. 提交一次修改触发`workflow`，比如可以修改一下`README.md`。

## 邮件推送

出于某些考量，本项目添加了邮件推送服务。只需要另外再添加四个`Secrets`：

+ `FROM_ADDR`：发件人邮箱；
+ `MAIL_PWD`：邮箱授权密码，不是登录密码，需要注意；
+ `TO_ADDR`：收件人邮箱；
+ `SMTP_SERVER`：发件人邮箱的smtp服务器地址。

若不想开启邮件推送，请根据注释提示，将`XMUAutoCheckIn.py`脚本最后的相关内容注释掉。

## Server酱推送（已更新推送途径，请自行查阅教程进行一定的修改）

邮件推送可能比较麻烦，因此也添加了Server酱推送部分。前往http://sc.ftqq.com/ 获得个人的`SCKEY`，然后添加一条`Secrets`：

+ `SERVER_KEY`：将`SCKEY`复制进去。

若不想开启Server酱推送，请根据注释提示，将`XMUAutoCheckIn.py`脚本最后的相关内容注释掉。本人默认是关闭Server酱的，如要启用，请将相关注释去掉。

***<u>相关内容</u>***

![image-20201208005845077](https://ljw-typora.oss-cn-shanghai.aliyuncs.com/mdImg/image-20201208005845077.png)

## 免责声明

1. 本项目不会记录你的任何敏感信息，也不会上传到任何服务器上。（Secrets是连创建者本人也看不到现有的信息的）
2. 本工具执行过程中产生的日志，仅会在使用者自行配置推送渠道后进行推送。日志中不包含任何用户敏感信息。
3. 本项目仅用于学习交流，请不要用于盈利，由于某些特殊原因，也请不要肆意传播，导致的不良后果本人不承担任何责任。
4. 本项目遵守[MIT License](https://github.com/JunzhouLiu/BILIBILI-HELPER/blob/main/LICENSE) ，请各位知悉。
