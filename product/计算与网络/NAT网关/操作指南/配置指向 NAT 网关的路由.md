创建 NAT 网关后，需要配置路由规则，将子网流量指向 NAT 网关。
1. 在私有网络控制台左侧目录中，单击【路由表】。
2. 在路由表列表中，单击需要访问 Internet 的子网所关联的路由表 ID 进入详情页，在路由策略中单击【新增路由策略】。
 ![2](https://main.qcloudimg.com/raw/86d1a69fd07814a4dc7230420ea154c5.png)
3. 在弹框中输入目的端，下一跳类型选择【NAT 网关】，下一跳选择已创建的 NAT 网关 ID。
 ![](https://main.qcloudimg.com/raw/4d48231dac7395c88600884983ba5bd9.png)
4. 单击【创建】完成以上配置后，关联此路由表的子网内的云服务器访问 Intenet 的流量将指向 NAT 网关。
