# 解决VSCode代理问题

使用VSCode的版本控制功能，尝试向GitHub推送更新，失败。报错信息：

```text
Failed to connect to github.com port 443: Operation timed out
```

但在本地，我用v2ray开启了全局代理，所以使用浏览器能正常访问 github.com 。

那么问题就在于v2ray并未代理VSCode的流量。

接下来设置VSCode的代理：

1. VSCode左下角设置，搜索Proxy。
2. 设置中搜索proxy。
3. 将`Http: Proxy`的值设置为`http://127.0.0.1:10808`。这里的代理地址取决于个人情况。就我的情况而言，我使用v2ray，在参数设置 - Core:基础设置中看到本地监听端口是10808，所以我的命令行中的端口为10808。
4. 将`Http: Support`的值设置为`on`。

……坏了。成功一会之后，现在发现又没法推送了，说明之前的设置大失败。学点计网再来解决吧。

感谢某个伟大的墙催我学知识。

现在好了。设置VSCode的代理并没有起作用，似乎是因为VSCode在做版本控制时只是单纯通过命令行执行git的命令，真正的工作还是git来做的。于是尝试设置git的代理：

1. 打开Powershell。
2. 执行两个命令

```shell
git config --global https.proxy http://127.0.0.1:10808
git config --global https.proxy https://127.0.0.1:10808
# 这里代理地址的设置与上面对VSCode代理的设置同理。
```

再次Sync changes，终于成功。

好像也没有想的那么难，不太需要把计网从头到尾学一遍。但书已经翻开了，干脆多看一点吧，反正找工作也要用，而且我对这些知识也很好奇。

但之前为什么成功了一小会呢……
