# 下载设置

![Xnip2024-11-05_06-01-41.png](/image/Xnip2024-11-05_06-01-41.png)

## 下载工具

<div>
<img src="/image/tr.png" alt="transmission" width="60">
<img src="/image/qb.png" alt="qbittorrent" width="60">
<img src="/image/aria2.png" alt="qbittorrent" width="60">
</div>

`ani-rss`支持`Transmission`、`qBittorrent`、`Aria2`三种下载工具。

由于受 API 限制，`ani-rss`的支持情况如下

<div style="overflow-x: auto;">
<div style="width: 900px;">

| 名称           | 自动下载 | 下载时重命名 | 下载时复杂解构重命名 | 下载完成后重命名 | 做种时修改下载位置 | 下载完成通知 | AList |
|--------------|------|--------|------------|----------|-----------|--------|-------|
| qBittorrent  | ✅    | ✅      | ✅          | ✅        | ✅         | ✅      | ✅     |
| Transmission | ✅    | ✅      | ❌          | ✅        | ✅         | ✅      | ✅     |
| Aria2        | ✅    | ❌      | ❌          | ✅        | ❌         | ❌      | ❌     |

</div>
</div>

*（强烈推荐使用 **qBittorrent**）*

::: details qBittorrent设置

1. 在设置面板中打开WebUI并设置用户名和密码。

![qBittorrent设置](/image/qBittorrent_settings.png)

2. 在浏览器中打开 `http://localhost:8989`
   （注意将端口号改为与设置qBittorrent中一致）。不出意外的话应该能进入WebUI，登陆成功后应该能见到如下页面，说明`qBittorrent`
   端设置无误。（如果无法打开页面，请重新检查`qBittorrent`的设置）

![qBittorrent页面](/image/qBittorrent_WebUI.png)

3. 在`ani-rss`中将上述的地址，用户名，密码填入后点击`测试`。

![qBittorrent测试](/image/qBittorrent_test.png)

如果出现`登陆成功`则说明设置成功。

:::

::: warning
**使用 Aria2 时，必须让 ani-rss 与 Aria2 路径保持一致才能自动重命名 详见** [docker映射挂载](#docker映射挂载)
:::

不支持下载时重命名会导致:

`在视频文件未重命名时已经有 emby 生成视频缩略图 .nfo 元数据,
当重命名后还会再次生成一次。且重命名后的视频再次被刮削到时 emby 无法触发 Webhook 通知。`

`个人喜欢使用 Webhook 通知让` [EmbyPinyin](https://github.com/wushuo894/EmbyPinyin) `(我的另一个项目) 处理中文拼音首字母索引`

## 保存位置

下载器的保存位置

::: warning
如果为空则 **不会进行下载**
:::

## 剧场版保存位置

如果为空则使用 **下载位置**

## 自动删除

自动删除已完成的任务, 不会删除本地文件

如果同时开启了 备用rss功能 将会自动删除对应洗版视频, 以实现 主rss 的替换

### 等待做种完毕

等待做种完成后才会删除任务

::: warning
推荐等待做种，否则可能被 **PeerBanHelper** 标记为吸血
:::

### 仅在主RSS更新后删除备用RSS

主RSS将不会自动删除，仅在其更新后删除对应备用RSS的任务与文件

## 拼音首字母

用于整理番剧到A-Z文件夹中
如:

```md
├── A
│ └── 安达与岛村
│ └── S01
│ ├── 安达与岛村 S01E01.mp4
│ ├── 安达与岛村 S01E02.mp4
│ ├── 安达与岛村 S01E03.mp4
│ └── 安达与岛村 S01E04.mp4
├── B
│ └── BanG Dream! It's MyGO!!!!!
│ └── S01
│ ├── BanG Dream! It's MyGO!!!!! S01E01.mp4
│ ├── BanG Dream! It's MyGO!!!!! S01E02.mp4
│ ├── BanG Dream! It's MyGO!!!!! S01E03.mp4

```

## 季度

将番剧存放于 `yyyy-MM` 下 如 `2024-07`

## 同时下载限制

防止同时下载任务过多导致qb卡死

强烈建议视性能设置, 推荐 `2-3`

## 延迟下载

主要用于需要同步到网盘的场景

一般30分钟后就支持秒传了

## 检测是否死种

RSS更新后添加下载任务时如果出现异常则会发送 [通知](/config/message.md)

## qBittorrent设置

### 分享率

"-1"表示禁用, "-2"使用全局设置

### 总做种时长

"-1"表示禁用, "-2"使用全局设置

### 非活跃时长

"-1"表示禁用, "-2"使用全局设置

### qb保存路径

开启后将使用qBittorrent的保存路径配置 (下载路径不受影响)
