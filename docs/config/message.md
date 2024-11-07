# 通知

### 通知模版示例

```md
标题: ${title}
评分: ${score}
TMDB: ${themoviedbName}
BGM: ${bgmUrl}
季: ${season}
集: ${episode}
字幕组: ${subgroup}
进度: ${currentEpisodeNumber}/${totalEpisodeNumber}
首播: ${year}年${month}月${date}日
事件: ${text}
```

webhook

```md
${message} 会自动替换为信息
${image} 会自动替换为图片链接
```

### 通知类型

开始下载、下载完成、缺集、错误

::: warning
下载完成通知暂不支持 Aria2
:::

## 通知方式

![Xnip2024-11-05_06-02-38.png](/image/Xnip2024-11-05_06-02-38.png)

::: details 邮箱通知

### QQ邮箱设置示例

```md
SMTP地址: smtp.qq.com
SMTP端口: 465
发件人邮箱: [qq号]@qq.com
密码: xxxx
SSL: 开启
收件人邮箱: [qq号]@qq.com
```

### QQ邮箱密码

（电脑网页端）

设置 - 账号 - POP3/IMAP/SMTP/Exchange/CardDAV/CalDAV服务

开启服务并生成授权码

:::

::: details TG通知

[Creating a new bot](https://core.telegram.org/bots/features#botfather:~:text=and%20managing%20bots.-,Creating%20a%20new%20bot,-Use%20the%20/newbot)

:::

::: details Server酱

[Server酱³ 使用说明书](https://doc.sc3.ft07.com/)

:::

::: details 其他平台

微信、钉钉、飞书请参考对应平台的webhook接口文档

:::
