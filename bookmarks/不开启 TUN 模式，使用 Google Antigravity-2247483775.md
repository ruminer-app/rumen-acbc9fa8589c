---
title: "不开启 TUN 模式，使用 Google Antigravity"
author: "原创
                                                      
                                                                                    白桃大麻花
                        白桃大麻花
                                                                            
                                      
                                                                
              
                搓手浴盐"
saved_at: 2026-02-08T13:21:55.537Z
source: https://mp.weixin.qq.com/s?__biz=Mzg5MTczNjAxMQ==&mid=2247483775&idx=1&sn=44b42b2878fb79c90aac682a46f47b65&chksm=ceda3d5f802ff140d21a527fe731e4c0cfce186686920962eed6af586d7e28436b18b2768551&mpshare=1&scene=24&srcid=0116WsBZHDbqJMFiCnwJKDCc&sharer_shareinfo=aa4b974fd70cc64ea5db1134417f09a3&sharer_shareinfo_first=aa4b974fd70cc64ea5db1134417f09a3#rd
---
![cover_image](https://mmbiz.qpic.cn/mmbiz_jpg/N7pZcSv8tMysnjuDMkUoAguNRbWtvmDDTysVEQLxowYJ0jtlk7RL8LfZeiaNyfXeRSe4x97HmC1juRUj1xazEzQ/0?wx_fmt=jpeg)

# 不开启 TUN 模式，使用 Google Antigravity

原创 白桃大麻花 白桃大麻花 [搓手浴盐](javascript:void\(0\);)

在小说阅读器中沉浸阅读

“Google Antigravity” 是谷歌在 2025 年 11 月 18 日随 Gemini 3 Pro 一同发布的实验性“代理优先”开发平台（Agentic Development Platform）。一句话概括：它把 AI 从“代码补全助手”升级成“能独立干活的程序员搭档”。它有多强，不用过多介绍。

但是，一如既往的，Antigravity 不能顺畅地在国内使用，需要搭建相应的网络环境。

方案有多种，本文介绍一种”不使用 TUN ，使用 Proxifier + Clash verge 自定义规则“的方案，好处是clash不开启全局模式，节省一部分流量，，并记录本次遇到的问题。

*   Proxifier 相关的配置：

首先，下载 Proxifier ,  并且新建 Proxy server ，Address  127.0.0.1 , Port 填写 clash verge 实际使用端口，Type 选择 SOCKS5.

创建规则，

①，需要添加的几个exe的文件夹路径（其中XXX需要换成你的用户名）：

C:\\Users\\xxx\\AppData\\Local\\Programs\\Antigravity

C:\\Users\\xxx\\AppData\\Local\\Programs\\Antigravity\\resources\\app\\extensions\\antigravity

为了保险起见，我把Antigravity相关的exe 都加入了进来（一定要通过点击 'Browser' 搜索相关路径，而不是直接把 exe 名字填写进去）：

language\_server\_windows\_x64.exe;antigravity.exe; inno\_updater.exe; fd.exe

配置完成后启用

*   Clash verge 相关的配置：

选择 Profiles --\> 右键自己的 Profile 文件，选择“Edit Proxies” （这样添加后更新规则不会被覆盖）

1.  为什么要 Edit Proxies：

在正确配置 Proxifier 之后， Antigravity 的网络访问将通过 Clash 代理。通过 Clash verge 日志可以看到，（icon 1）goog 网址都已经通过代理访问了。而（icon 2）访问谷歌 ip 却仍在直连，而没有通过代理。这就是为什么 Antigravity 无法加载模型。

1.  需要加入哪些 ip 代理规则：

通过 clash verge 日志得知：

```
11-22 18:12:56warning
```

Antigravity 使用了 google 两个 IP 的核心网段

**IP 地址**

**所属 CIDR 网段**

**子网掩码**

**备注**

**216.239.32.223**

`216.239.32.0/23`

`255.255.254.0`

Google 核心基础设施

**142.250.107.95**

`142.250.0.0/15`

`255.254.0.0`

Google 全球服务常用段

综上，需要在 Clash verge 中加入两条规则，①选择 “Match IP address range（IP-CIDR）” ，②写入相应 ip 和掩码，③选择 “⚡ 代理”， ④选择 “PREPEND RULE”

通过以上 Proxifier + Clash verge “锁链式的整体配置” ， Antigravity 就可以正常连接到 Agent 服务了

可以尝试选择 Gemini3 模型，让它回答一些问题

（虽然不知道问的问题是什么，更不知道回答的为何物。但是，我大受震撼）

预览时标签不可点

修改于

微信扫一扫
关注该公众号

继续滑动看下一个
