### 工具
- [clash-meta](https://github.com/MetaCubeX/ClashMetaForAndroid)
- [sing-box](https://github.com/SagerNet/sing-box)
- [Hiddify Next](https://github.com/hiddify/hiddify-next/blob/main/README_cn.md)
- [v2rayNG](https://github.com/2dust/v2rayNG) 电脑版为v2rayN
- Linux推荐sing-box、clash-verge
- [nekobox-android](https://github.com/MatsuriDayo/NekoBoxForAndroid) 支持的协议多
- [nekobox-windows](https://github.com/MatsuriDayo/nekoray) 支持的协议多


### clash排除制定域名

Settings -> Parsers -> Edit -> 下面的代码 -> 保存后更新订阅生效

```jsx
parsers: # array
    - url: <你的订阅地址>
      yaml:
        prepend-rules:
            - DOMAIN-SUFFIX,baidu.com,DIRECT
            - DOMAIN-SUFFIX,qq.com,DIRECT
```
