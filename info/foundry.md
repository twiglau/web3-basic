# Foundry

- 是一个只能合约开发套件，包含多个命令工具

1. forge: 管理依赖包，编译，运行，测试，部署合约
2. cast: 命令行工具，链交互
3. anvil: 启动本地节点
4. chisel: 运行Solidity 代码片段

## 项目结构

1. cache: forge 缓存信息，在 forge build 后出现
2. lib: 存放依赖库（默认安装forge-std)
3. out: 存放编译输出文件
4. script: 合约脚本，可用于部署合约，广播交易
5. src: 合约源代码
6. test: 测试合约代码
7. foundry.toml: 项目foundry 配置

## 编译使用 forge build
  
1. 在out目录下生成abi, 字节码及编译相关信息。
2. forge inspect 用来查看合约编译产物和元信息。

## 合约测试 forge test

  1. 测试文件默认用 t.sol 结尾，也可 CounterTest.sol;
  2. 导入Test合约：提供了基本的日志和断言功能；
  3. 导入测试目标合约；
  4. 继承Test合约，使用Test功能；
  5. Setup函数（可选）：每个测试用例运行前都调用；
  6. 前缀为test的函数将作为测试用例运行；
  7. testFuzz模糊测试：测试用例的参数值，由foundry随机抽样；

## 合约部署

- 准备：钱包账号 + RPC URL
- 本地启动测试： anvil
   > 在 127.0.0.1:8545 启动服务
   > 默认配置 10 个账号
   > --fork-url 基于网络的状态启动一个本地模拟环境

```bash
anvil
anvil --fork-url <RPC_URL>
```

```bash
# 通过脚本部署
forge script script/Counter.s.sol --private-key 0xdlakdfadlfka --rpc-url http://chain.net --broadcast
```

## 在 Foundry 工程发行 ERC20

1. 导入 Openzepplin 依赖

```bash
# update,remove
forge install OpenZeppelin/openzeppelin-contracts
```

- Forge 依赖库重映射(建立别名)
  > 可重新映射依赖项，使它们更容易导入
  > 映射推导： forge remappings > remappings.txt



2. Cast 命令 管理部署账号，链交互

```bash
# 查找某个命令输入历史
history | grep --pri
# bash加载环境变量
source .env
# 查看加载变量中某个变量
echo $PRIVATE_KEY
```

- 与链交互瑞士军刀，众多子命令：
  > Wallet命令
  > Chain,Transaction,Block命令
  > Account命令
  > ENS命令
  > Etherscan命令
  >ABI,Conversion,Utility命令

1. 开源合约