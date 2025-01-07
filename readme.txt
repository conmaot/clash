N1 设置
1、PPOE拨号  
    EH0 Lan口桥接取消，改为指向ETH0网口
    新建wan口，PPOE拨号，wan要小写
    设置防火墙，将wan口和lan口允许数据出入站

2、dokcer安装 subconver
    docker run -d --restart=always -p 25500:25500 tindy2013/subconverter:latest

3、安装openclash内核、客户端
    插件设置--> 流量控制--> 勾选 实验性：绕过指定区域 IP 关闭 绕过服务器地址 
    覆写设置-> DNS设置  -->  勾选 自定义上游 DNS 服务器 勾选 追加上游 DNS  勾选 Fake-IP-Filter 黑名单模式
    配置订阅-->新增配置文件 填入机场订阅地址  user-agent 选择 clash.meta 在线转化地址服务器 选择自定义填入docker地址 http://127.0.0.1:25500/sub
                            订阅转化模板填入 https://raw.githubusercontent.com/conmaot/clash/refs/heads/main/main/clash_lian.ini
                            UDP 支持选择启用    排除节点 官网、剩余、到期、失败、异常 0.1 0.2 0.3节点
