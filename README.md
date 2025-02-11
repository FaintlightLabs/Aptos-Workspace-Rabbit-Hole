# Aptos-Workspace-Rabbit-Hole

<br>

欢迎尝试 Aptos Workspace 兔子洞，你可以自己创建一个 Aptos workspace github repo 并跑完下面的流程后可以在 [Build3 - https://www.buildthree.xyz/](https://www.buildthree.xyz/) 中完成对应的体验任务并获取体验奖励

<br>

--------

### 任务要求：

1. **Fork 当前仓库**：
   - 在 GitHub 上 Fork 当前仓库。

2. **体验 Aptos Workspace**：
   - 根据教程步骤，使用 Aptos Workspace 创建一个 TS/JS 项目并进行体验。
   - 在项目中进行相关操作，确保能够顺利完成步骤。

3. **创建 GitHub Repo 并提交**：
   - 创建一个新的 GitHub 仓库，将你的项目上传到此仓库。

4. **撰写体验反馈**：
   - 在你创建的 GitHub 仓库中，编辑 `README.md` 文件。
   - 在 `README.md` 文件中写下你的 **体验感受和反馈内容**，并确保反馈内容不少于 20 字。
   - 注意：反馈不能简单使用“好、不错”等词语，需提供有效的反馈。

5. **提交任务**：
   - 在 Build3 平台上提交任务。
   - 将你创建的 GitHub 仓库 URL 提交到任务证明中。
   - 请将你提交任务时使用的 **钱包地址** 放入 `README.md` 文件中，以防止奖品被冒领。

<br>
<br>

**github repo 的目录示例**：
```
- my-workspace-project      // 你的项目名称(可以随意修改) 
  - contract                // 包含所有 Move 包的目录
    - hello_blockchain      // 一个示例 Move 包，包含 hello_blockchain 合约
      - sources
        - message.move
      - Move.toml
  - tests                   // 集成测试目录
    - my-first-test.ts      // 使用 `hello_blockchain` 的集成测试
  - tsconfig.testing.json   // 测试运行器的配置文件（我们当前使用 Mocha）
  - workspace.config.ts     // Aptos Workspace的配置文件
  - README.md               // 用于填写使用体验和反馈内容 （使用体验和反馈内容不得少于 20 字且为有效反馈, 使用 “好、不错” 等反馈将被判定为无效反馈）
```

<br>

--------

# 任务详情
| 任务链接 | 任务名称 | 任务奖励 |
|--------|--------|--------|
| [Aptos Workspace Rabbit Hole](https://www.buildthree.xyz/bounty/0xa644b70faca61ad460626cfe5c189426244206c518ca4e46bb65db641c1ea9de) | 体验 Aptos workspace 并反馈使用体验 | 1.5 USDT | 

--------
<br>
<br>

### 此处为任务提交区
**********

**提交任务时使用的 Aptos 钱包地址**:
- 0x

**运行结果**
```
XXXXXXXXXXXXXXXXXXXX
```

**使用体验**：
- XXXXXXXX

**使用反馈**: 
- XXXXXXXX

**********

<br>
<br>

**********

## 开始创建

本教程将带你一步步创建一个使用 Aptos Workspace的 TS/JS 项目。完成后，你将拥有一个功能齐全的开发环境，包含一个示例 Move 合约和集成测试。

## 步骤 0：安装先决条件

在开始之前，请确保你已安装所需的依赖项。

请参阅 [Aptos Workspace README](https://github.com/aptos-labs/workspace/blob/main/workspace/README.md#prerequisites)，安装如 **Docker** 等必要的先决条件。

如果你尚未安装 **Node.js** 和 **npm**，请参考官方安装指南：

- [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

## 步骤 1：初始化 npm 项目

要设置项目，请在终端中运行以下命令：

```bash
npm init -y
```

这将初始化一个 npm 包，并生成一个 `package.json` 文件。

以下是它的示例内容：

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

## 步骤 2：安装 Aptos Workspace

现在，作为开发依赖项安装 **Aptos Workspace**：

```bash
npm install --save-dev @aptos-labs/workspace
```

这会将以下内容添加到 `package.json` 中：

```json
  "devDependencies": {
    "@aptos-labs/workspace": "^0.0.24"
  }
```

## 步骤 3：初始化 Aptos Workspace

接下来，通过运行以下命令初始化 Aptos Workspace：

```bash
npx aptos-workspace init
```

你将被提示选择 **JavaScript** 或 **TypeScript**。

在本教程中，我们将继续使用 **TypeScript**。

该命令会生成以下项目结构：

```
- my-project
  - contract                // 包含所有 Move 包的目录
    - hello_blockchain      // 一个示例 Move 包，包含 hello_blockchain 合约
      - sources
        - message.move
      - Move.toml
  - tests                   // 集成测试目录
    - my-first-test.ts      // 使用 `hello_blockchain` 的集成测试
  - tsconfig.testing.json   // 测试运行器的配置文件（我们当前使用 Mocha）
  - workspace.config.ts     // Aptos Workspace的配置文件
```

如上所示，生成的文件包括一个示例 **Move 合约** 和一个 **集成测试**，可以直接运行。

## 步骤 4：运行集成测试

为了验证一切设置正确，运行集成测试：

```bash
npx aptos-workspace test
```

如果一切配置正确，你应该看到类似以下的输出：

```
Aptos CLI version 6.0.2 detected.
Docker version 27.5.1 detected.

Spinning up local networks to run tests, this may take a while...

  my first test
    ✔ publish the contract (5866ms)
    ✔ set message (134ms)
    ✔ get message

  3 passing (24s)
```

## 一切设置完成！🎉

恭喜你！你刚刚完成了第一个 **Aptos Workspace** 项目的设置！

现在，让我们来探索生成的 Move 合约和集成测试，了解它们是如何工作的。

### 探索 `hello_blockchain` 合约

```rust
module hello_blockchain::message {
    use std::error;
    use std::signer;
    use std::string;

    struct MessageHolder has key {
        message: string::String,
    }

    const ENO_MESSAGE: u64 = 0;

    #[view]
    public fun get_message(addr: address): string::String acquires MessageHolder {
        assert!(exists<MessageHolder>(addr), error::not_found(ENO_MESSAGE));
        borrow_global<MessageHolder>(addr).message
    }

    public entry fun set_message(account: signer, message: string::String)
    acquires MessageHolder {
        let account_addr = signer::address_of(&account);
        if (!exists<MessageHolder>(account_addr)) {
            move_to(&account, MessageHolder {
                message,
            })
        } else {
            let old_message_holder = borrow_global_mut<MessageHolder>(account_addr);
            old_message_holder.message = message;
        }
    }
}
```

这个 **Move 模块** 允许用户：

- 使用 `set_message` **将消息存储到链上**
- 使用 `get_message` **检索存储的消息**

### 探索示例集成测试

生成的集成测试 (`tests/my-first-test.ts`) 演示了如何编写一个完整的测试工作流。

**主要特点**

- 使用 [mocha](https://mochajs.org/#getting-started) 作为测试框架，应该对大多数 TS/JS 开发者来说比较熟悉。
- 通过全局变量 **`workspace`** 提供一个 **功能齐全的 Aptos 客户端**，允许与测试网络交互。
    - 支持 [Aptos TypeScript SDK](https://aptos-labs.github.io/aptos-ts-sdk/@aptos-labs/ts-sdk-1.33.2/classes/Aptos.html) 中的所有功能。

## 下一步 🚀

现在你已经完成了环境的搭建，你可以：

- ✅ 修改 **Move 合约** 以实现更多功能。
- ✅ 扩展 **集成测试**，验证更复杂的工作流。
- ✅ 尝试不同的 **Aptos SDK 功能**。

进一步探索，请查看 [Aptos 文档](https://aptos.dev/) 和 [Aptos Workspace GitHub 仓库](https://github.com/aptos-labs/workspace)。

祝编码愉快！🎉🚀
