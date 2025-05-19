## Terminal（终端）如何配置网络代理



- 0. ### 适用于macOS系统

- 1. ### 确定代理客户端的端口

​               首先我们打开我们使用的代理客户端设置页面，查看其开放的 **HTTP** 端                   口，例如我这里是7897.

​               <img src="端口.png">



- 2. ### 配置代理

     - 打开Terminal：

     ```html
     vim ~/.zshrc
     ```

     - 在zshrc中：

     ```html
     alias proxy='export all_proxy=socks5://127.0.0.1:7897'
     alias unproxy='unset all_proxy'
     ```

     - 最后执行如下命令使配置生效：

     ```html
     source ~/.zshrc
     ```

- 3. ### 开始测试

     - 执行如下命令开启代理模式：

     ```html
     proxy
     ```

     - 看一下目前终端IP地址

     ```html
     mbp2021@fsing ~ % curl ipinfo.io
     {
       "ip": "152.53.231.109",
       "hostname": "v2202502258231319859.goodsrv.de",
       "city": "Schopfheim",
       "region": "Baden-Wurttemberg",
       "country": "DE",
       "loc": "47.6510,7.8209",
       "org": "AS197540 netcup GmbH",
       "postal": "79650",
       "timezone": "Europe/Berlin",
       "readme": "https://ipinfo.io/missingauth"
     }%  
     ```

     - 执行如下命令关闭代理模式：

     ```html
     unproxy																							
     ```

     

- ### 配置 Git 代理

          
          git config --global http.proxy http://127.0.0.1:7897
          git config --global https.proxy https://127.0.0.1:7897
      
   取消git代理
  
   ```html
   git config --global --unset http.proxy
   git config --global --unset https.proxy
   ```
  
- ## 其他包代理

  	其他包如NPM，poetry均需单独配置代理，可以自行在网络上搜索教程，配置代理。

