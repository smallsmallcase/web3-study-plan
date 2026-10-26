# Web3 学习路线图（Roadmap）

本文件用于细化整个 Web3 学习路径，按阶段拆解学习目标、关键技术点和产出要求，帮助你按顺序推进。

---

## 一、学习目标总览

目标分为四层：
1. 基础认知：区块链、Ethereum、Solidity、Web3
2. 实战能力：合约开发、测试、部署、链上交互
3. 工程能力：Java / Spring Boot + web3j，Go + go-ethereum
4. 提升能力：真实项目、源码阅读、求职与职业方向

---

## 二、阶段 1：Ethereum 与区块链基础（1-2 周）

### 学习目标
- 理解区块链与去中心化的核心概念
- 了解 Ethereum 的账户模型、交易、区块、gas、状态机
- 能解释以太坊网络、节点、客户端、JSON-RPC 的关系

### 学习资料
- Ethereum 官方开发者文档：https://ethereum.org/zh/developers/docs/
- 镜像链接：https://web.archive.org/web/2026/https://ethereum.org/zh/developers/docs/
- GitHub：https://github.com/ethereum/ethereum-org-website

### 关键知识点
- 区块链的本质
- 共识机制
- 以太坊的账户模型
- 交易、区块、状态树
- Gas 成本和费用机制
- EOA 与 CA
- RPC 接口基础

### 产出要求
- 写一份“Ethereum 基础知识笔记”
- 记录你能理解的关键术语：Transaction、Receipt、Nonce、Gas、State、EVM等

---

## 三、阶段 2：Solidity 基础与智能合约开发（2-4 周）

### 学习目标
- 掌握 Solidity 基础语法
- 能编写基础合约、事件、修饰符、状态变量
- 理解 Solidity 中的安全设计和常见坑

### 学习资料
- Solidity 官方文档：https://docs.soliditylang.org/zh-cn/latest/
- Solidity by Example：https://solidity-by-example.org/

### 关键知识点
- 变量类型
- 函数与修饰符
- 构造函数
- 错误处理（require / revert / assert）
- 事件（event）
- 继承与库
- payable / fallback / receive
- ERC-20 / ERC-721 标准结构

### 产出要求
- 实现至少 3 个合约：
  1. 简单计数器
  2. ERC-20 Token 基础版
  3. 假定的存款 / 取款合约
- 用 Foundry 编写测试

---

## 四、阶段 3：Foundry 实战（2-4 周）

### 学习目标
- 使用 Foundry 编译、测试和部署合约
- 能写单元测试、集成测试和脚本化部署
- 形成 Solidity 开发工作流

### 学习资料
- Foundry 官方书籍：https://book.getfoundry.sh/
- GitHub：https://github.com/foundry-rs/book

### 关键知识点
- `forge init`
- `forge test`
- `forge build`
- `forge script`
- `cast call`
- `anvil` 本地链
- `vm` cheatcodes
- 测试覆盖率与断言

### 产出要求
- 用 Foundry 重写你前面的 Solidity 示例
- 每个合约至少完成 3 个测试用例
- 输出一份简洁的 deployment script

---

## 五、阶段 4：OpenZeppelin 与安全实践（1-2 周）

### 学习目标
- 了解生产级合约代码如何设计
- 学会使用 OpenZeppelin 规范实现标准合约
- 掌握常见安全问题和防范方式

### 学习资料
- OpenZeppelin Contracts：https://github.com/OpenZeppelin/openzeppelin-contracts
- 文档：https://docs.openzeppelin.com/contracts/

### 关键知识点
- Ownable
- AccessControl
- ReentrancyGuard
- ERC-20 / ERC-721 / ERC-1155
- Upgradeable patterns
- SafeMath / SafeERC20

### 产出要求
- 对一个 ERC-20 或一个治理类合约做一版安全审查
- 形成“风险点清单”和“修复方案”

---

## 六、阶段 5：Java + web3j 后端开发（4-6 周）

### 学习目标
- 掌握 Java 与 Spring Boot 的基本开发方式
- 学会使用 web3j 调用 Ethereum RPC
- 能查询账户余额、读取合约、发送交易

### 学习资料
- web3j：https://github.com/LFDT-web3j/web3j
- 文档：https://docs.web3j.io/
- Spring Boot 示例：https://github.com/web3j/web3j-spring-boot-starter

### 关键知识点
- Web3j API 结构
- 连接节点（HTTP / IPC / WebSocket）
- 获取区块、交易、余额
- 读取合约状态
- 调用合约函数
- 发送 raw transaction
- 事件监听与解析
- Spring Boot 整合 web3j

### 产出要求
- 实现一个 Java 项目：
  - 读取 ETH 余额
  - 调用 ERC-20 合约
  - 发送转账或授权交易
  - 解析事件日志

---

## 七、阶段 6：链上充值项目实战（4-6 周）

### 学习目标
- 完成一个真正能落地的链上充值系统
- 掌握链上事件扫描、异步处理、状态管理和幂等设计

### 项目建议
- 语言：Java + Spring Boot + web3j
- 数据库：PostgreSQL
- 缓存：Redis
- 消息队列：Kafka
- 监控：Prometheus / Grafana

### 核心功能
- 扫描区块并获取 Transfer 事件
- 解析 ERC-20 转账事件
- 根据用户地址和金额更新充值状态
- 保证幂等性与重试
- 避免链重组导致重复充值
- 提供充值查询接口

### 产出要求
- GitHub 上有一个完整可运行的项目
- README 说明部署步骤和核心设计
- 至少包含一个真实测试或 Mock 测试

---

## 八、阶段 7：Go 基础与 Geth 源码学习（4-6 周）

### 学习目标
- 掌握 Go 语言基础和并发编程
- 能阅读 geth 的关键模块
- 理解 Ethereum 客户端内部机制

### 学习资料
- Go Tour：https://go.dev/tour/
- Go 官方文档：https://go.dev/doc/
- go-ethereum：https://github.com/ethereum/go-ethereum
- Geth 分析资料：
  - https://github.com/ZtesoftCS/go-ethereum-code-analysis
  - https://github.com/ABCDELabs/Understanding-Ethereum-Go-version

### 关键知识点
- Go 语法、接口、错误处理
- Goroutine / Channel
- net/http / JSON-RPC
- pprof
- Geth 交易池
- EVM 执行
- Trie / State / Block / TxPool / P2P

### 产出要求
- 选择一个模块做源码阅读笔记：例如 `txpool` / `eth` / `core` / `trie`
- 输出一份阅读总结

---

## 九、阶段 8：职业方向深化（根据目标调整）

### 方向 A：钱包/支付/链上资金系统
- 钱包开发
- 私钥和签名
- 多签钱包
- 风控与权限控制
- 账户抽象

### 方向 B：链上数据平台
- 区块浏览器
- 事件索引
- 大数据处理
- Kafka + ClickHouse + Elasticsearch

### 方向 C：底层协议研发
- geth 源码阅读
- 共识 / P2P / EVM
- 客户端实现

### 方向 D：智能合约安全/审计
- 审计思路
- 漏洞分析
- 代码审计流程

---

## 十、最终产出建议

在 6 个月内，建议至少完成以下 3 个实战作品：

1. Solidity 合约项目
   - ERC-20 / NFT / 存款合约
   - 用 Foundry 测试

2. Java web3j 项目
   - 区块扫描 / 钱包查询 / 交易发送

3. 真实 Web3 充值系统
   - Java + web3j + Spring Boot + Kafka + Redis + PostgreSQL

这三者组合起来，能够非常有效地展示你的 Web3 实战能力。

---

## 十一、学习顺序一览（最推荐）

```text
Ethereum Docs
  → Solidity
  → Foundry
  → OpenZeppelin
  → Java + web3j
  → ERC-20 充值系统
  → Go 基础
  → Geth 源码
  → 方向深化
```

---

## 十二、建议的学习原则

- 不要只看文档，必须写代码
- 每阶段都要产出实际项目或笔记
- 先实现小功能，再做复杂系统
- 通过 GitHub 记录成长过程
- 以真实工程项目为核心，不以“概念堆砌”为主

---

## 十三、结语

这个路线不是为了“看完所有资料”，而是为了帮助你系统建立 Web3 能力，并最终具备从零到真实项目落地的能力。最重要的是：在每一阶段都能完成真实作品，并持续更新 GitHub。
