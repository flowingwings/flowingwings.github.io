# 解决VSCode代理问题

使用VSCode的版本控制功能，尝试向GitHub推送更新，失败。报错信息：

```shell
Failed to connect to github.com port 443: Operation timed out
```

但在本地，我用v2ray开启了全局代理，所以使用浏览器能正常访问 github.com 。

那么问题就在于v2ray并未代理VSCode的流量。

接下来设置VSCode的代理：

1. VSCode左下角设置，搜索Proxy。
2. 设置……

……坏了。成功一会之后，现在发现又没法推送了，说明之前的设置大失败。学点计网再来解决吧。

感谢某个伟大的墙催我学知识。
