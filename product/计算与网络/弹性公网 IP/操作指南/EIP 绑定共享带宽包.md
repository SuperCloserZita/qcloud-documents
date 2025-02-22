IP 带宽包是共享带宽包的其中一种类型，详情请参见 [产品概述](https://cloud.tencent.com/document/product/684/15245#.E4.BA.A7.E5.93.81.E7.B1.BB.E5.88.AB)。创建 IP 带宽包实例后，您需要将使用该 IP 带宽包的 EIP 添加到 IP 带宽包实例中。

## 前提条件
- 预付费共享带宽包可以在 [共享带宽包控制台](https://console.cloud.tencent.com/vpc/package) 直接购买；后付费共享带宽包处于内测阶段，如需使用，请提交 [内测申请](https://cloud.tencent.com/apply/p/8o8lmsr5nj8) 或联系您的商务经理申请开通。
- 请确保您的账户类型为标准账户类型。若您无法确定账户类型，请参见 [判断账户类型](https://cloud.tencent.com/document/product/1199/49090#judge)。

## 限制说明
1. EIP 中仅支持将按流量和按小时带宽计费的常规 IP 手动加入 IP 带宽包，包月带宽的常规 IP 不支持加入 IP 带宽包。
2. EIP 中的加速 IP 和静态单线 IP 不支持手动加入 IP 带宽包。新建加速 IP 时，后台会自动创建 Anycast 加速带宽包（这里可视为 IP 带宽包）。新建静态单线 IP 时，后台会自动创建相应的移动、联通或电信带宽包（这里可视为 IP 带宽包）。
3. 添加 EIP 到 IP 带宽包后，EIP 原本的计费模式将变更为共享带宽包模式，不额外收取公网网络费，但正常收取 IP 资源费。
4. EIP 的 IP 资源费与是否加入 IP 带宽包无关，当 EIP 绑定云资源时，免收 IP 资源费。
5. 单个 IP 带宽包最多可添加100个 EIP。

## 操作步骤
1. 登录 [私有网络控制台](https://console.cloud.tencent.com/vpc/vpc?rid=1)，单击左侧导航栏的**共享带宽包**。
2. 选择地域，在列表中找到目标 IP 带宽包实例，单击实例 ID 进入详情页。
3. 在详情页的**带宽包资源**模块，单击**+添加资源**。
4. 在弹出的“绑定资源”窗口中，选择**弹性公网 IP/普通公网 IP** 为资源类型，并选择需添加到 IP 带宽包的 EIP，单击**确定**即可。
![](https://main.qcloudimg.com/raw/935a60911d409c65a3f4ec200b027bcc.png)
