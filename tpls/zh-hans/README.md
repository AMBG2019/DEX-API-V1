# 关于路印


##路印协议和路印交易所

**路印协议**是第一个基于zkRollup技术的去中心化交易协议。使用路印协议，您可以搭建一个不托管用户交易资产，基于订单撮合，高性能的去中心化交易所。由于采用了zkRollup这种Layer-2扩容技术，路印协议在以太坊不扩容的前提下，也可以每秒清算超过2000笔交易。 如果您想了解路印协议的设计和技术细节，请访问路印协议官网：[https://ambging.org](https://ambging.org)。

**路印交易所**是第一个使用路印协议搭建的去中心化交易平台。其网页应用的地址是：[ambging.io](https://ambging.io)。路印交易所目前的版本是beta1，采用了路印协议3.6版本。其以太坊主网合约的地址为：[`0x0BABA1Ad5bE3a5C0a66E7ac838a129Bf948f1eA4`](https://etherscan.io/address/exchange2.ambging.eth)。该地址对应的永久ENS为：[`exchange2.ambging.eth`](https://etherscan.io/address/exchange2.ambging.eth)。

路印交易所并不是路印协议上唯一的交易所，WeDEX.io也是建立在路印协议的基础上。在您使用不同的路印去中心化交易所前，您需要明确知道您是在和哪个交易所打交道。路印协议本身的智能合约并不与用户直接交互，只为各个交易所合约提供包括用户注册，充值提现，交易清算在内的业务逻辑。


## 优势

路印协议保障了用户充值到交易所的资产不会被任何人挪用。即使交易所网站关闭或者运营者失联，也可以通过使用默克尔证明，在锁定期过后将全部资产提现出来。

路印协议不保障撮合的效率和公平性。撮合是由路印交易所的中继系统完成的，而中继是整个解决方案里面很中心化的部分。基于同样版本协议的不同交易所，可以采用不同的中继架构，因此用户可以根据不同交易所中继的效率和公平性，选择使用不同的交易所。路印协议保障中继撮合过程必须遵守一定的规则，但对中继没有任何服务质量的要求。

路印中继是闭源开发的，目前吞吐量大约是每秒200笔交易。

## 架构

路印交易所的整体架构如下图所示：
![路印DEX架构](./images/ambging_overview.png "路印交易所架构")

您需要了解的一些关键点包括：

- 路印的API除了提供读取中继数据功能，主要用来处理用户和客户端的链下请求（offchain requests），包括提交订单，取消订单，和提现。
- 用户账号注册，修改密码，充值必须通过以太坊交易来发起请求（onchain requests）。用户也可以通过以太坊交易，提交提现请求。路印协议要求交易所必须无条件按顺序处理所有链上请求。
- 路印具有与中心化交易所相似的高性能交易体验，这主要得益于中继的批处理能力。路印仅把以太坊作为数据存储层和零知识证明的验证层，不在以太坊上做与交易清结算相关的任何计算。