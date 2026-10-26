# Web3 学习计划

这是一个面向 Ethereum / Solidity / Foundry / Java web3j / Go geth 的 Web3 学习路线与实践计划，适合从零到进阶的开发者使用。

目标：
- 建立 Ethereum 与 Solidity 基础认知
- 掌握智能合约开发与测试
- 完成一个真实的链上充值/交易项目
- 理解以太坊客户端实现与核心源码
- 选择 Java / Go 方向进行深入学习和求职准备

---

## 一、最终学习顺序（已校验版）

### 第 1 步：Ethereum 官方开发者文档

首选（需代理全局模式）：
- https://ethereum.org/zh/developers/docs/

镜像（免代理问题）：
- https://web.archive.org/web/2026/https://ethereum.org/zh/developers/docs/

源码（GitHub 直连）：
- https://github.com/ethereum/ethereum-org-website

学习重点：
- 区块链基础概念
- Ethereum 账户模型
- 交易和区块
- Gas 与费用
- JSON-RPC API
- 智能合约基础
- 开发工具链概览

---

### 第 2 步：Solidity 官方文档

- 英文版：https://docs.soliditylang.org/
- 中文版：https://docs.soliditylang.org/zh-cn/latest/

学习重点：
- Solidity 语法基础
- 数据类型与存储
- 函数与修饰符
- 事件与错误处理
- 继承与接口
- 库与特殊功能
- 编码风格与安全实践

---

### 第 3 步：Solidity by Example

- 官网：https://solidity-by-example.org/
- GitHub：https://github.com/Cyfrin/solidity-by-example.github.io

学习重点：
- 常见合约模式
- ERC-20 / ERC-721 / ERC-1155
- 安全问题示例
- Gas 优化思路
- 实战型代码示例

---

### 第 4 步：Foundry

- 官方书籍：https://book.getfoundry.sh/
- GitHub：https://github.com/foundry-rs/book
- 官网：https://getfoundry.sh/

学习重点：
- Foundry 安装与配置
- Forge：编译、测试、覆盖率
- Cast：RPC 交互工具
- Anvil：本地测试链
- 部署脚本与自动化流程
- 合约测试结构化设计

---

### 第 5 步：OpenZeppelin Contracts

- GitHub：https://github.com/OpenZeppelin/openzeppelin-contracts
- 官方文档：https://docs.openzeppelin.com/contracts/

学习重点：
- ERC 标准实现
- Access Control
- Security 模块
- Proxy 升级模式
- 生产级代码参考

---

### 第 6 步：web3j（Java Ethereum SDK）

- GitHub：https://github.com/LFDT-web3j/web3j
- 官方文档：https://docs.web3j.io/
- 示例项目：https://github.com/web3j/web3j-spring-boot-starter

学习重点：
- JSON-RPC 调用
- 钱包管理
- 私钥与签名
- 离线交易构造
- ERC-20 交互
- 事件监听与解析
- Spring Boot 集成

---

### 第 7 步：ERC-20 REST Service（架构参考）

- GitHub：https://github.com/web3labs/erc20-rest-service

说明：
- ⚠️ 最后更新时间：2021 年 12 月
- 适合学习 Spring Boot + web3j 的项目结构与 REST API 设计
- 实际生产中建议同步参考最新官方示例与依赖版本

学习重点：
- Spring Boot 项目结构
- web3j 集成方式
- REST API 设计模式
- 交易查询与事件处理
- 错误处理和响应封装

---

### 第 8 步：完成 Java 链上充值系统（自己动手实现）

这是最关键的实践阶段。目标：使用 Spring Boot、web3j、PostgreSQL、Kafka、Redis 实现一个真实的 ERC-20 充值系统。

核心功能：
- 区块扫描与断点续扫
- ERC-20 Transfer 事件解析
- 充值幂等性保证
- 确认数控制
- 临时链重组处理
- RPC 失败重试
- Kafka 异步处理
- Prometheus / 监控指标

推荐项目结构：

```text
erc20-deposit-service/
├── scanner/           # 区块扫描器
├── decoder/           # 事件解析器
├── consumer/          # Kafka 消费者
├── ledger/            # 账务处理
├── retry/             # 重试机制
├── reorg/             # 链重组处理
├── monitoring/        # 监控指标
├── docker-compose.yml
├── schema.sql
├── README.md
└── pom.xml / build.gradle
```

预期收获：
- 理解链上数据处理的生产模式
- 形成真实项目经验
- 适合放到简历中作为核心作品

---

### 第 9 步：Go 基础

- A Tour of Go：https://go.dev/tour/
- Go 官方教程：https://go.dev/doc/tutorial/
- Effective Go：https://go.dev/doc/effective_go
- Go by Example：https://gobyexample.com/
- Go 语言圣经：https://www.gopl.io/

中文资源：
- Go 语言圣经中文版：https://golang-china.github.io/gopl-zh
- Go 语言高级编程：https://chai2010.cn/advanced-go-programming-book/

学习重点：
- 基本语法与类型系统
- Struct 与 Interface
- Goroutine 与 Channel
- Context 与 Sync
- Error 处理
- HTTP 与 WebSocket
- 并发模式
- pprof 与性能分析

---

### 第 10 步：go-ethereum（Geth）

- GitHub：https://github.com/ethereum/go-ethereum
- 官方文档：https://geth.ethereum.org/docs
- JSON-RPC 文档：https://geth.ethereum.org/docs/interacting-with-geth/rpc

学习方法：
不要从头完整阅读所有代码，应该围绕真实问题阅读：

1. 一个 JSON-RPC 请求如何被处理？
2. 一笔交易如何进入交易池？
3. 区块如何执行与确认？
4. 事件日志如何生成和查询？
5. EVM 执行状态如何维护？

推荐深入模块：
- accounts/
- core/types/
- core/txpool/
- eth/
- core/
- trie/
- p2p/
- vm/

---

### 第 11 步：阅读 Geth 源码与分析资料

推荐参考：

- go-ethereum-code-analysis：https://github.com/ZtesoftCS/go-ethereum-code-analysis
- Understanding-Ethereum-Go-version：https://github.com/ABCDELabs/Understanding-Ethereum-Go-version

说明：
- 这两个资源都非常适合理解 geth 的关键流程
- 两个可以结合着看，互补性强

不推荐：
- https://github.com/miguelmota/ethereum-development-with-go-book
- 原因：已归档，适合作为很老的参考资料，不建议作为主学习路径

---

### 第 12 步：根据求职方向深化

#### 方向 A：钱包与资金系统

学习内容：
- BIP-32 / BIP-39 / BIP-44
- HD Wallet
- 多签与钱包控制
- 提现审核和风控
- Safe Smart Account

参考：
- BIP-32：https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki
- BIP-39：https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki
- BIP-44：https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki
- Safe：https://github.com/safe-global/safe-smart-account

#### 方向 B：交易系统 / 订单簿 / 区块链交易引擎

学习内容：
- 订单簿与撮合
- 资金冻结与结算
- WebSocket 推送
- 风控与限频
- 事件驱动架构

#### 方向 C：链上数据平台

学习内容：
- 区块浏览器
- 资产统计
- 链上行为分析
- Kafka + ClickHouse + Elasticsearch
- 事件和链数据采集

---

## 二、学习周期建议

建议按 6 个月节奏推进：

| 阶段 | 时间 | 内容 | 输出 |
|---|---:|---|---|
| 第 1 阶段 | 1-3 周 | Ethereum 与 Solidity 基础 | 笔记 + 简单合约 |
| 第 2 阶段 | 4-8 周 | Solidity 实战与 Foundry | 测试型合约项目 |
| 第 3 阶段 | 9-14 周 | Java + web3j 学习 | SDK 交互项目 |
| 第 4 阶段 | 15-20 周 | 链上充值系统 | 真实项目作品 |
| 第 5 阶段 | 21-24 周 | Go 基础 + geth 学习 | 源码阅读笔记 |
| 第 6 阶段 | 25-28 周 | 深化方向与项目打磨 | 进阶项目 |

---

## 三、每周学习模板

```text
周一：学习官方文档和概念
  ↓
周二：阅读官方示例代码
  ↓
周三：实现最小版本功能
  ↓
周四：补充测试和异常处理
  ↓
周五：阅读相关源码与实现细节
  ↓
周六：整理笔记和问题记录
  ↓
周日：提交 GitHub，准备下一周
```

---

## 四、适合初学者的最小可执行版本

如果你只有 12 周的时间，可以按下面顺序：

### 第 1 个月：基础
- Ethereum 官方文档
- Solidity 官方文档
- Foundry 基础

### 第 2 个月：项目实践
- 完成简单 ERC-20 合约
- 用 Foundry 做测试
- 学习 OpenZeppelin 合约

### 第 3 个月：后端与链上交互
- 学习 web3j
- 完成简单链上查询和发送交易

### 第 4 个月：真实项目
- 完成 ERC-20 充值系统
- 聚焦架构、日志、重试、幂等、监控

---

## 五、推荐技术栈

### Solidity / 智能合约
- Solidity
- Foundry
- OpenZeppelin
- Hardhat（可选，作为辅助）

### Java / 后端
- Java 17+
- Spring Boot
- web3j
- PostgreSQL
- Redis
- Kafka
- Docker

### Go / 客户端与源码研究
- Go 1.22+
- Geth / go-ethereum
- pprof
- gRPC / HTTP

---

## 六、建议的个人学习节奏

1. 每个阶段都要写代码，而不是只看文档。
2. 不要过早深入底层源码，先完成项目再看源码。
3. 选定一个技术方向（Java / Go / Solidity）后持续加深。
4. 每完成一个模块，更新 GitHub 仓库，并写 README 说明。
5. 优先做真实可运行项目，而不是只看示例代码。

---

## 七、最终建议

如果你的目标是：

- 进入 Web3 开发：优先走 Solidity + Foundry + Java / web3j 路线
- 进入区块链底层或客户端开发：优先走 Go + geth 路线
- 求职型项目：以 ERC-20 充值系统、链上扫描器、钱包系统为主

推荐最终路线：

```text
Ethereum 官方文档 → Solidity → Foundry → OpenZeppelin → web3j → 充值系统 → Go 基础 → geth 源码 → 方向深化
```

这是最平衡、最实战、最适合从零到中高级的路线。

---

## 八、资源索引（整理版）

### 官方资源
- Ethereum Docs：https://ethereum.org/zh/developers/docs/
- Solidity Docs：https://docs.soliditylang.org/zh-cn/latest/
- Foundry Book：https://book.getfoundry.sh/
- web3j Docs：https://docs.web3j.io/
- Go 官方文档：https://go.dev/

### 示例与项目资源
- Solidity by Example：https://solidity-by-example.org/
- OpenZeppelin：https://github.com/OpenZeppelin/openzeppelin-contracts
- web3j：https://github.com/LFDT-web3j/web3j
- go-ethereum：https://github.com/ethereum/go-ethereum
- ERC-20 REST Service：https://github.com/web3labs/erc20-rest-service

### 中文资料
- Go 语言圣经中文版：https://golang-china.github.io/gopl-zh
- Go 语言高级编程：https://chai2010.cn/advanced-go-programming-book/
- Geth 分析：
  - https://github.com/ZtesoftCS/go-ethereum-code-analysis
  - https://github.com/ABCDELabs/Understanding-Ethereum-Go-version

---

## 九、结语

Web3 学习的重点，不只是“会写智能合约”，而是理解：
- 交易如何被处理
- 状态如何改变
- 合约如何与链交互
- 系统如何做到高可靠、可扩展、可审计

最重要的是：在实践中积累真实经验，而不是只停留在概念层面。

如果你愿意，我还可以继续为这个仓库补充以下内容：
- `roadmap.md`：更细的分阶段路线图
- `learning-log.md`：学习笔记模板
- `project-template.md`：ERC-20 充值系统开发模板
- `daily-study-plan.md`：每天/每周任务计划

你可以直接在仓库中继续扩展。
