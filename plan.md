- 编写一个skill用于提示AI助手帮助用户自己部署VPN
# 第一步：提示用户所需的准备
- 阿里云账户注册（如果已经拥有则可以跳过），没有注册提醒用户前往https://account.aliyun.com/register/qr_register.htm注册

# 第二步：在确保用户注册完毕后，前往https://swasnext.console.aliyun.com/buy#/
- 实例选择通用型28元/月，系统镜像选择Debian
- 地域由用户自己选择，推荐东京（几乎无限制的同时，速率也较为不错），由需要体验最新AI产品的用户，也可以选择美国地区
- 购买一个月
- 由用户自主决定是否开启自动续费
- 要求用户在防火墙处打开所有端口，应用类型选择全部TCP+UDP即可
- 提醒用户在5天内阿里云机器都可以免费退订，所以不用担心配置失败问题
![alt text](image.png)

# 第三步：帮助用户下载客户端
- 观察用户当前所在的环境，在https://github.com/2dust/v2rayN/releases上下载对应的软件包，安装参考https://github.com/2dust/v2rayN/wiki/Release-files-introduction
- win中软件还需要解压，解压后点击v2rayN.exe 即可以正常打开
![alt text](image-3.png)

# 第四步 ：要求用户在https://swasnext.console.aliyun.com/servers界面点击重置密码，
- 提醒用户将ip公网地址和重置后的密码告诉ai
- ai执行ssh连接远端
- 在远端执行命令
```bash
bash <(wget -qO- https://raw.githubusercontent.com/gansxx/net_tools/main/sb.sh)
```
- 把最后的四合一分享链接给用户（不要包括中文部分），让用户在打开的gui界面
    - 示例：
```text
🚀【 四合一聚合订阅 】节点信息如下：
分享链接
dmxlc3M6Ly84YWYxYWE4Zi1hNjcyLTQ1YTktYjVjOC05NmMyYmQzMDA1ZmVAOC4yMTEuMTY4LjE2OToyNzU5ND9lbmNyeXB0aW9uPW5vbmUmZmxvdz14dGxzLXJwcngtdmlzaW9uJnNlY3VyaXR5PXJlYWxpdHkmc25pPXd3dy55YWhvby5jb20mZnA9Y2hyb21lJnBiaz14RXVGWWxIMEFUbVNvZENRYjFPRkRPSldmb05MU1FQWVpfZTB5dW5PWUc0JnNpZD01OGI5MTQ3OSZ0eXBlPXRjcCZoZWFkZXJUeXBlPW5vbmUjdmwtcmVhbGl0eS1pWjZ3ZTFrczE5OWN4enV0c2JtcGZlWgp2bWVzczovL2V5SmhaR1FpT2lJNExqSXhNUzR4TmpndU1UWTVJaXdpWVdsa0lqb2lNQ0lzSW1odmMzUWlPaUozZDNjdVltbHVaeTVqYjIwaUxDSnBaQ0k2SWpoaFpqRmhZVGhtTFdFMk56SXRORFZoT1MxaU5XTTRMVGsyWXpKaVpETXdNRFZtWlNJc0ltNWxkQ0k2SW5keklpd2ljR0YwYUNJNklqaGhaakZoWVRobUxXRTJOekl0TkRWaE9TMWlOV000TFRrMll6SmlaRE13TURWbVpTMTJiU0lzSW5CdmNuUWlPaUk0TURnd0lpd2ljSE1pT2lKMmJTMTNjeTFwV2paM1pURnJjekU1T1dONGVuVjBjMkp0Y0dabFdpSXNJblJzY3lJNklpSXNJblI1Y0dVaU9pSnViMjVsSWl3aWRpSTZJaklpZlFvPQpoeXN0ZXJpYTI6Ly84YWYxYWE4Zi1hNjcyLTQ1YTktYjVjOC05NmMyYmQzMDA1ZmVAOC4yMTEuMTY4LjE2OTozMjc3OT9zZWN1cml0eT10bHMmYWxwbj1oMyZpbnNlY3VyZT0xJnNuaT13d3cuYmluZy5jb20jaHkyLWlaNndlMWtzMTk5Y3h6dXRzYm1wZmVaCnR1aWM6Ly84YWYxYWE4Zi1hNjcyLTQ1YTktYjVjOC05NmMyYmQzMDA1ZmU6OGFmMWFhOGYtYTY3Mi00NWE5LWI1YzgtOTZjMmJkMzAwNWZlQDguMjExLjE2OC4xNjk6MTYxMzU/Y29uZ2VzdGlvbl9jb250cm9sPWJiciZ1ZHBfcmVsYXlfbW9kZT1uYXRpdmUmYWxwbj1oMyZzbmk9d3d3LmJpbmcuY29tJmFsbG93X2luc2VjdXJlPTEjdHU1LWlaNndlMWtzMTk5Y3h6dXRzYm1wZmVaCg==
```
# 第五步： 测试和提醒
- 首要推荐使用hysteria协议，使用体验最佳，延迟最低
## 测试
- 在将链接复制到客户端后，右键单击测试配置文件真延迟![alt text](image-2.png)
- 测试时只要显示的延迟如图不是-1，则代表能够正常访问![alt text](image-1.png)

## 额外提醒
- 如果用户检测时，延迟-1，无法正常连接，请记得提醒用户是否在阿里云端正确配置了防火墙（云主机上的防火墙都已经在脚本处正确配置了）
- 需要让任何应用都使用该网络开启tun模式即可
- 遇到google网站无法打开通常是规则配置问题
- 遇到校园网或公司内网内端口突然无法访问问题，通常是内网对端口的临时封锁导致的，而非服务器本身，解决方案有稍等一会，或者配置端口跳跃即可
- 如果还存在无法解决问题，通过gansxxzhgo@gmail.com联系以取得帮助
