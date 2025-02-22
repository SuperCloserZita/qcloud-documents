### BHLoader 是必须要安装的吗？
BHLoader 的主要功能是拉起本地应用程序，并通过本地应用程序创建连接，访问连接相关的目标资源，因此 BHLoader 是运维人员必须要安装的。

### 安装 BHLoader 后，是否还需要安装 SecureCRT，Xshell 等连接工具软件？
BHLoader 的主要功能是拉起本地应用程序，剩余的连接工作，以及从本地操作 CVM 都是需要在相关的 SecureCRT 或 Xshell 等软件操作的，所以需要在本地安装相关连接工具软件。

### 安装 BHLoader 时，操作系统账户是否需要管理员权限？
需要管理员权限，若没有管理员权限会报如下错误：
![](https://main.qcloudimg.com/raw/025754eb4726ec12c66ce04ef35067e2.png)

### BHLoader 程序出现闪退现象，如何处理？
#### 场景一：检查 Mac 电脑版本，如果是13.0及以上，请按照如下步骤操作。
1. 在本地电脑上执行命令。
```
sudo vim /etc/ssh/ssh_config
```
2. 在文件最后追加一行命令。
```
HostKeyAlgorithms +ssh-rsa,ssh-dss
```
3. 在堡垒机上重新访问资产。

#### 场景二：如果是运维工具（例如PuTTY）安装路径配置错误，请按照如下步骤操作。
1. 找到 BHLoader 的安装目录。
2. 在安装目录下找到文件 config.toml。
3. 打开 config.toml 文件，检查运维工具安装路径是否正确，如果错误，可以直接删除，后续程序将引导客户重新选择运维工具，也可以修改为正确的运维工具路径。


### 资产账号是否必须是 CVM 上的真实用户？
资产账号中必须是目标 CVM 上已有的用户（如 root、administrator），堡垒机服务本身不会对 CVM 进行创建用户操作。

### 登录堡垒机运维页面之后，在一段时间内没有进行操作将自动断开，是否支持自定义超时时间？
支持，管理员可自己设置 Web 闲置超时时间，详情请参见 [登录安全设置](https://cloud.tencent.com/document/product/1025/59809)。

### 目前登录 Linux 服务器的私钥带有密码，应如何录入？
设置私钥时，同时设置解密私钥口令，即可实现通过带密码的私钥登录 Linux 服务器。
![](https://qcloudimg.tencent-cloud.cn/raw/669fc3b977b7018d5b2ffd785ace8838.png)

### 双因子认证是否可以关闭？
SaaS 型堡垒机必须使用双因子认证，目前阶段有两种选择：密码+OTP 或密码+短信，出于安全性考虑，不支持关闭双因子。

### 访问白名单是什么，没有添加为什么里面会有相关的 IP 地址？
- 访问白名单是限制用户使用本地工具软件（SecureCRT，Xshell，mstsc等），连接堡垒机的 IP 名单，类似于 CVM 的安全组。
- 当用户成功访问运维页面时，会自动把用户的公网 IP 地址添加到白名单里面，也可以手动添加。

### 已登录运维页面了，在使用工具访问时，有时候无法连接成功？
造成这种问题可能是贵公司网络出口有多个公网 IP 导致，登录运维页面添加的 IP 地址，和使用本地工具连接堡垒机的 IP 地址不一致。可将贵公司出口 IP 地址的相关 IP 网段手动添加到白名单中。
 
###  SaaS 型堡垒机是否可以阻止 Linux 执行相关命令？
可以阻止 Linux 执行需要禁止的命令，具体操作如下：
1. 在 [高危命令模板](https://console.cloud.tencent.com/bh/high-risk) 页面，单击**新建模板**，添加需要禁止的命令。
2. 在 [访问权限配置 ](https://console.cloud.tencent.com/bh/ctrl-policy)页面，单击**编辑**，为相关权限添加该模板就可实现。

### 当企业运维人员，登录运维页面后发现主机列表为空？
使用管理员登录到堡垒机管理界面，在 [访问权限配置 ](https://console.cloud.tencent.com/bh/ctrl-policy) 页面单击**新建访问权限**或**编辑**，在第3步选择对应主机或主机组，可新建或修改访问权限。
![](https://main.qcloudimg.com/raw/ab51f0ae8a44b842069baf05f0fc201c.png)

### SaaS 型堡垒机的日志可以存储多久？
目前由于上线不久，用户可以免费存储180天的审计数据，后续可能会按照存储量收费。

###  WinSCP 创建相同文件名，提示被堡垒机阻断，管理端审计记录为下载操作被阻断，这个是什么原因？
在 WinSCP 中创建文件时，如果服务器上已有同名文件，那么 WinSCP 会默认将这个文件下载下来并进入编辑模式。而如果堡垒机限制了 SFTP 只能上传不能下载，那么就会出现上述情况。
