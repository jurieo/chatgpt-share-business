# chatgpt-share-web

本项目是基于[chatgpt-share-server](https://github.com/xyhelper/chatgpt-share-server)的二开项目。  
感谢[xyhelper](https://github.com/xyhelper/)提供的项目支持，感谢`xyhelper` 提供的免费接入点。respect~

> [!NOTE]
> 本项目使用者必须在遵循 OpenAI 的[使用条款](https://openai.com/policies/terms-of-use)以及**法律法规**的情况下使用，不得用于非法用途。
>
> 根据[《生成式人工智能服务管理暂行办法》](http://www.cac.gov.cn/2023-07/13/c_1690898327029107.htm)的要求，请勿对中国地区公众提供一切未经备案的生成式人工智能服务。

由于发现一些利用免费版本恶意收费的现象，现在免费版本将进行限制。  
本项目有免费版（用户 5 人内），`pro` 版本（用户超过 5 人）和 `plus`版本（全部功能，以前的付费版） 三个版本。

## 免费版和 pro 版

免费版本和 `pro` 版本唯一区别是免费版本用户限制为 5 人内，`pro` 版本不限制用户数。其余功能一模一样。会同步 `chatgpt-share-server` 的全部功能。  
镜像为：https://hub.docker.com/r/jurieo/gpt-share-server  
主要实现了以下功能：

- ✅ 官网 UI 一比一还原，每小时同步官网。
- ✅ 可使用官网的所有功能，GPTs，画图，高级代码分析，画图，插件，gpt-4-all 等。
- ✅ 左侧同步用户所有车的聊天记录，点击聊天记录，自动换车
- ✅ 右上角换车，抽屉弹出可用车，一键换车
- ✅ 禁止多设备登录
- ✅ 聊天页可查看公告
- ✅ 聊天页订阅到期 7 天内有到期提醒，配置环境变量 FAKA_URL，用户可以点击此提醒，自行续费或购买。
- ✅ 只有一个车可用的时候，直接进入登陆页上车
- ✅ 支持单个用户限制额度,默认 1 小时 20 次。
- ✅ 登陆页可返回选车页
- ✅ 翻车不能上车
- ✅ 支持用户名密码登录
- ✅ 后台新增用户默认有效期一个月，默认 1 小时 20 次。

特别提示：免费版本的用户不得超过 5 人，超过 5 人即需升级为`pro`版进行授权才能使用。

## plus 版

tag 为`undefined`即为 plus 版。更新较频繁。  
用户注册，登陆，购买，使用，一条龙服务，安心做你的甩手掌柜。  
在免费版的基础上增加如下功能：

- ✅ gpt-4-mobile 模型，无限额度(默认关闭,好像被官方和 pc 共享了，待验证)
- ✅ 支付功能，暂只支持易支付。
- ✅ 聊天记录备份到数据库，翻车后聊天记录仅供查看，不能继续聊天。
- ✅ 可以给用户分配他只能特定使用的车。plus 类型高于分配的车。比如给用户分配了 plus 车，但他不是 plus 则无法使用该车。
- ✅ 用户注册验证邮箱后缀（邮箱白名单）
- ✅ 用户通过邮箱注册,重置密码,提现等。
- ✅ 文件代理，再也不怕文件打不开了。
- ✅ 邮箱配置
- ✅ 兑换码支持按额度和频率限制，按账号类型（3.5，plus）限制，按使用时间限制
- ✅ 先登陆再选车，登陆时可以快速上车（快速进入最空闲车的聊天页）
- ✅ 聊天页一键换车，自动换车
- ✅ 个人中心，车列表按空闲到繁忙排序
- ✅ 用户通过推广获得付费用户返佣
- ✅ 用户无感兑换码，解放手撸（可自行配置按月付，季付，周付等配置）
- ✅ 新增管理员审核，封禁用户
- ✅ 用户提现，审核
- ✅ 修改密码，忘记密码，重置密码
- ✅ 用户可设置为管理员
- ✅ 可配置新注册用户免费体验时长，通过邀请码注册再加 2 小时
- [ ] 后续会根据反馈和需求继续添加更多功能。。

## 部署

> [!IMPORTANT]
> 部署本项目推荐使用海外 VPS 且对服务器要求较高,至少需要 2 核 2G 才能稳定运行。本项目推荐使用如下 VPS 供你起航。[高性价比 VPS 推荐 1](https://my.racknerd.com/aff.php?aff=7367&pid=828)，[高性价比 VPS 推荐 2](https://my.racknerd.com/aff.php?aff=7367&pid=829)。  
> 如果你的用户较多(超过 50 人)，性能和速度稳定必不可少，可选择[高性能 VPS 推荐 1](https://bandwagonhost.com/aff.php?aff=74266&pid=88)，[高性能 VPS 推荐 2](https://bandwagonhost.com/aff.php?aff=74266&pid=87)。

### 免费版和 pro 版一键部署

本版本的部署和 `chatgpt-share-server` 保持一致，只需将镜像名称修改为`jurieo/gpt-share-server`。  
更多部署详情请参考[chatgpt-share-server](https://chatgpt-share-server.xyhelper.cn/install/)。

#### 免费版和 pro 版一键部署脚本

```bash
curl -sSfL https://raw.githubusercontent.com/jurieo/chatgpt-share-web/deploy-free/quick-install.sh | bash
```

### plus 版部署

`plus`版有一些配置需要简单设置，所以需要先拉取一些配置文件。  
拉取配置文件

```bash
curl -sSfL https://raw.githubusercontent.com/jurieo/chatgpt-share-web/deploy/quick-install.sh | bash
```

完成上面操作后，你需要进入目录`cd chatgpt-share-web`,修改`config.yaml`文件中的重要信息。

- `ENABLE_MORE_GPT`: 是否开启无限模式,默认关闭。字面意思，懂的都懂，有封号风险。
- `FREE_TIER`: 注册用户免费体验时间，单位小时，0 则没有。
- `AFF_TIME`: 通过邀请码注册免费体验时间，单位小时。0 则没有。
- `REGISTER_PLUS`: 刚注册的用户是否可以使用 plus。默认 false。
- `COMMISSION_RATE`: 佣金比例，0 则不返佣，前端无`推广有礼`的 tab。不影响之前的返现，但会影响之后注册的用户。
- `ALLOWED_WITHDRAWAL`: 最低提现金额，0 则无限制。
- `FAKA_URL`：发卡地址，以`https`开头。配置后，在用户兑换页（未登陆），用户选车页，用户聊天页都可以跳转发卡地址，以 `https` 开头。
- `DISALLOW_MUTI_DEVICE`：是否禁止多设备登录，默认 `true`
- `DISALLOW_ROAM`：是否关闭会话漫游 true 关闭 false 开启，默认 `false`
- `FILE_SERVER`：文件服务器，默认为空，则表示上传和下载都走 `share` 服务器。可选`https://files.oaiusercontent.com`
- #### **邮箱配置，必须配置，否则用户无法注册，无法重置密码，若不配置，无法启动。**
- `MAIL_FROM`: 发件人邮箱。
- `MAIL_PASS`: SMTP 授权码，谷歌邮箱为应用专用密码（在账号-安全性-开启两步验证后可开启应用专用密码）。
- `MAIL_HOST`: 邮箱服务器地址，默认`smtp.gmail.com`。
- `MAIL_PORT`: 邮箱服务器端口，默认 `587`,支持 `TLS(587)`和 `SSL(465)`。
- `MAIL_WHITELIST`: 注册邮箱白名单。清空: 关闭白名单 有值: 开启白名单。默认`@gmail.com,@yahoo.com,@hotmail.com,@outlook.com,@icloud.com,@163.com,@126.com,@qq.com,@foxmail.com`
- `SITE_NAME`: 邮箱别名，用于发送邮件的友好提示。
- #### 支付配置，目前仅支持易支付
- `EpayId`: 商户 id。
- `EpayKey`: 商户 key。
- `PayAddress`: 支付地址。
- `PayType`: 允许的支付类型，默认空，可填`alipay,wxpay`，表示支付宝和微信支付，只有一个就填写其中一个。

### 启动项目

保存好上面的 `config.yaml` 配置文件，执行以下命令（手动更新也是此命令）。

```sh
./deploy.sh
```

即可开启使用之旅。  
访问后台管理系统，`http://ip:38300/shareadmin`，使用`admin`/`123456`登陆之后，及时修改密码。新建一个用户，将这个用户设置为管理员，可以在前端生成兑换码，审核用户提现等操作。  
更多使用技巧，尽情探索吧。  
可有偿部署 100 元/次。

## 授权联系

`plus` 版可以试用 3 天，如需继续使用，[邮件联系我](mailto:junlinyizhan@gmail.com)或者[TG 联系我](https://t.me/jurieo_bot)。

## 项目预览

可访问[君临驿站](https://aiok.me/user/#/register?i=4ME9Z)注册体验。
<img src="https://raw.githubusercontent.com/jurieo/chatgpt-share-web/main/assets/login.png" width="640">
<img src="https://raw.githubusercontent.com/jurieo/chatgpt-share-web/main/assets/register.png" width="640">
<img src="https://raw.githubusercontent.com/jurieo/chatgpt-share-web/main/assets/carlist1.png" width="640">
<img src="https://raw.githubusercontent.com/jurieo/chatgpt-share-web/main/assets/chat1.png" width="640">
<img src="https://raw.githubusercontent.com/jurieo/chatgpt-share-web/main/assets/subtype.png" width="640">

### 风险声明

本项目仅供学习和研究使用，不鼓励用于商业用途。我们不对任何因使用本项目而导致的任何损失负责。
