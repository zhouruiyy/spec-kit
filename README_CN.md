<div align="center">
    <img src="./media/logo_small.webp"/>
    <h1>🌱 Spec Kit</h1>
    <h3><em>更快地构建高质量软件。</em></h3>
</div>

<p align="center">
    <strong>通过规范驱动开发（Spec-Driven Development）帮助组织专注于产品场景而非编写无差异化的代码。</strong>
</p>

[![Release](https://github.com/github/spec-kit/actions/workflows/release.yml/badge.svg)](https://github.com/github/spec-kit/actions/workflows/release.yml)

---

## 目录

- [🤔 什么是规范驱动开发？](#-什么是规范驱动开发)
- [⚡ 快速开始](#-快速开始)
- [📽️ 视频概览](#️-视频概览)
- [🔧 Specify CLI 参考](#-specify-cli-参考)
- [📚 核心理念](#-核心理念)
- [🌟 开发阶段](#-开发阶段)
- [🎯 实验目标](#-实验目标)
- [🔧 前置条件](#-前置条件)
- [📖 了解更多](#-了解更多)
- [📋 详细流程](#-详细流程)
- [🔍 故障排除](#-故障排除)
- [👥 维护者](#-维护者)
- [💬 支持](#-支持)
- [🙏 致谢](#-致谢)
- [📄 许可证](#-许可证)

## 🤔 什么是规范驱动开发？

规范驱动开发**颠覆了**传统软件开发模式。几十年来，代码一直是王者——规范只是我们构建并在"真正的"编码工作开始时丢弃的脚手架。规范驱动开发改变了这一点：**规范变得可执行**，直接生成可工作的实现，而不仅仅是指导它们。

## ⚡ 快速开始

### 1. 安装 Specify

根据您使用的编码代理初始化项目：

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init <项目名称>
```

### 2. 建立项目原则

使用 **`/constitution`** 命令创建项目的治理原则和开发指南，这些将指导所有后续开发。

```bash
/constitution 创建专注于代码质量、测试标准、用户体验一致性和性能要求的原则
```

### 3. 创建规范

使用 **`/specify`** 命令描述您想要构建的内容。专注于**什么**和**为什么**，而不是技术栈。

```bash
/specify 构建一个应用程序，帮助我按相册整理照片。相册按日期分组，可以在主页面通过拖拽重新组织。相册永远不会嵌套在其他相册中。在每个相册内，照片以瓦片式界面预览。
```

### 4. 创建技术实现计划

使用 **`/plan`** 命令提供您的技术栈和架构选择。

```bash
/plan 应用程序使用 Vite 和最少数量的库。尽可能使用原生 HTML、CSS 和 JavaScript。图片不上传到任何地方，元数据存储在本地 SQLite 数据库中。
```

### 5. 分解为任务

使用 **`/tasks`** 从您的实现计划创建可操作的任务列表。

```bash
/tasks
```

### 6. 执行实现

使用 **`/implement`** 执行所有任务并根据计划构建您的功能。

```bash
/implement
```

有关详细的分步说明，请参阅我们的[综合指南](./spec-driven.md)。

## 📽️ 视频概览

想看看 Spec Kit 的实际应用吗？观看我们的[视频概览](https://www.youtube.com/watch?v=a9eR1xsfvHg&pp=0gcJCckJAYcqIYzv)！

[![Spec Kit 视频封面](/media/spec-kit-video-header.jpg)](https://www.youtube.com/watch?v=a9eR1xsfvHg&pp=0gcJCckJAYcqIYzv)

## 🔧 Specify CLI 参考

`specify` 命令支持以下选项：

### 命令

| 命令     | 描述                                                    |
|----------|--------------------------------------------------------|
| `init`   | 从最新模板初始化新的 Specify 项目                        |
| `check`  | 检查已安装的工具（`git`、`claude`、`gemini`、`code`/`code-insiders`、`opencode`、`cursor-agent`） |

### `specify init` 参数和选项

| 参数/选项            | 类型     | 描述                                                                  |
|---------------------|----------|----------------------------------------------------------------------|
| `<项目名称>`         | 参数     | 新项目目录的名称（使用 `--here` 时可选）                              |
| `--ai`              | 选项     | 使用的 AI 助手：`claude`、`gemini`、`copilot`、`opencode` 或 `cursor` |
| `--script`          | 选项     | 使用的脚本变体：`sh`（bash/zsh）或 `ps`（PowerShell）                |
| `--ignore-agent-tools` | 标志 | 跳过 AI 代理工具检查（如 Claude Code）                              |
| `--no-git`          | 标志     | 跳过 git 仓库初始化                                                  |
| `--here`            | 标志     | 在当前目录中初始化项目而不是创建新目录                                |
| `--skip-tls`        | 标志     | 跳过 SSL/TLS 验证（不推荐）                                          |
| `--debug`           | 标志     | 启用详细的调试输出以进行故障排除                                      |

### 示例

```bash
# 基本项目初始化
specify init my-project

# 使用特定 AI 助手初始化
specify init my-project --ai claude

# 使用 Cursor 支持初始化
specify init my-project --ai cursor

# 使用 PowerShell 脚本初始化（Windows/跨平台）
specify init my-project --ai copilot --script ps

# 在当前目录中初始化
specify init --here --ai copilot

# 跳过 git 初始化
specify init my-project --ai gemini --no-git

# 启用调试输出进行故障排除
specify init my-project --ai claude --debug

# 检查系统要求
specify check
```

### 可用的斜杠命令

运行 `specify init` 后，您的 AI 编码代理将可以访问这些斜杠命令进行结构化开发：

| 命令         | 描述                                                           |
|--------------|----------------------------------------------------------------|
| `/constitution` | 创建或更新项目治理原则和开发指南                                |
| `/specify`      | 定义您想要构建的内容（需求和使用故事）                          |
| `/plan`         | 使用您选择的技术栈创建技术实现计划                              |
| `/tasks`        | 为实现生成可操作的任务列表                                      |
| `/implement`    | 执行所有任务以根据计划构建功能                                  |

## 📚 核心理念

规范驱动开发是一个强调以下方面的结构化过程：

- **意图驱动开发**，其中规范在"如何"之前定义"什么"
- **丰富的规范创建**，使用护栏和组织原则
- **多步骤细化**，而不是从提示进行一次性代码生成
- **高度依赖**先进 AI 模型能力进行规范解释

## 🌟 开发阶段

| 阶段 | 重点 | 关键活动 |
|------|------|----------|
| **0到1开发**（"绿地"） | 从零生成 | <ul><li>从高级需求开始</li><li>生成规范</li><li>规划实现步骤</li><li>构建生产就绪的应用程序</li></ul> |
| **创意探索** | 并行实现 | <ul><li>探索多样化解决方案</li><li>支持多种技术栈和架构</li><li>实验 UX 模式</li></ul> |
| **迭代增强**（"棕地"） | 棕地现代化 | <ul><li>迭代添加功能</li><li>现代化遗留系统</li><li>适应流程</li></ul> |

## 🎯 实验目标

我们的研究和实验专注于：

### 技术独立性

- 使用多样化的技术栈创建应用程序
- 验证规范驱动开发是不绑定特定技术、编程语言或框架的过程这一假设

### 企业约束

- 演示关键任务应用程序开发
- 纳入组织约束（云提供商、技术栈、工程实践）
- 支持企业设计系统和合规要求

### 以用户为中心的开发

- 为不同用户群体和偏好构建应用程序
- 支持各种开发方法（从氛围编码到 AI 原生开发）

### 创意和迭代过程

- 验证并行实现探索的概念
- 提供强大的迭代功能开发工作流
- 扩展流程以处理升级和现代化任务

## 🔧 前置条件

- **Linux/macOS**（或 Windows 上的 WSL2）
- AI 编码代理：[Claude Code](https://www.anthropic.com/claude-code)、[GitHub Copilot](https://code.visualstudio.com/)、[Gemini CLI](https://github.com/google-gemini/gemini-cli)、[Cursor](https://cursor.sh/)、[Qwen CLI](https://github.com/QwenLM/qwen-code) 或 [opencode](https://opencode.ai/)
- [uv](https://docs.astral.sh/uv/) 用于包管理
- [Python 3.11+](https://www.python.org/downloads/)
- [Git](https://git-scm.com/downloads)

## 📖 了解更多

- **[完整的规范驱动开发方法论](./spec-driven.md)** - 深入探讨完整过程
- **[详细演练](#-详细流程)** - 分步实现指南

---

## 📋 详细流程

<details>
<summary>点击展开详细的分步演练</summary>

您可以使用 Specify CLI 来引导您的项目，这将在您的环境中引入所需的工件。运行：

```bash
specify init <项目名称>
```

或在当前目录中初始化：

```bash
specify init --here
```

![Specify CLI 在终端中引导新项目](./media/specify_cli.gif)

系统将提示您选择您正在使用的 AI 代理。您也可以直接在终端中主动指定：

```bash
specify init <项目名称> --ai claude
specify init <项目名称> --ai gemini
specify init <项目名称> --ai copilot
specify init <项目名称> --ai qwen
specify init <项目名称> --ai opencode
# 或在当前目录中：
specify init --here --ai claude
```

CLI 将检查您是否安装了 Claude Code、Gemini CLI、Qwen CLI 或 opencode。如果您没有安装，或者您更喜欢在不检查正确工具的情况下获取模板，请在命令中使用 `--ignore-agent-tools`：

```bash
specify init <项目名称> --ai claude --ignore-agent-tools
```

### **步骤1：** 建立项目原则

转到项目文件夹并运行您的 AI 代理。在我们的示例中，我们使用 `claude`。

![引导 Claude Code 环境](./media/bootstrap-claude-code.gif)

如果您看到 `/constitution`、`/specify`、`/plan`、`/tasks` 和 `/implement` 命令可用，您就会知道配置正确。

第一步应该是使用 `/constitution` 命令建立项目的治理原则。这有助于确保在所有后续开发阶段中一致的决策制定：

```text
/constitution 创建专注于代码质量、测试标准、用户体验一致性和性能要求的原则。包括这些原则应如何指导技术决策和实现选择的治理。
```

此步骤创建或更新 `/memory/constitution.md` 文件，其中包含您的项目基础指南，AI 代理将在规范、规划和实现阶段参考这些指南。

### **步骤2：** 创建项目规范

在建立项目原则后，您现在可以创建功能规范。使用 `/specify` 命令，然后提供您想要开发的项目具体需求。

>[!重要]
>尽可能明确地说明您正在尝试构建**什么**以及**为什么**。**此时不要专注于技术栈**。

示例提示：

```text
开发 Taskify，一个团队生产力平台。它应该允许用户创建项目、添加团队成员、
分配任务、评论并在看板样式的板之间移动任务。在这个功能的初始阶段，
让我们称之为"创建 Taskify"，让我们有多个用户，但用户将预先声明，预定义。
我想要五个用户，分为两个不同类别，一个产品经理和四个工程师。让我们创建三个
不同的示例项目。让我们为每个任务的状态设置标准的看板列，如"待办"、
"进行中"、"审查中"和"完成"。此应用程序将没有登录，因为这只是
第一个测试，以确保我们的基本功能已设置。对于看板工作板中的任务卡片，
您应该能够将任务的当前状态更改为看板的不同列之间。
您应该能够为特定卡片留下无限数量的评论。您应该能够从该任务
卡片中分配一个有效用户。当您首次启动 Taskify 时，它将为您提供五个用户列表供选择。
不需要密码。当您点击用户时，您进入主视图，显示项目列表。
当您点击项目时，您打开该项目的看板。您将看到列。
您将能够在不同列之间来回拖拽卡片。您将看到任何分配给
您（当前登录用户）的卡片，颜色与所有其他卡片不同，这样您就可以快速
看到您的。您可以编辑您发表的任何评论，但您不能编辑其他人发表的评论。您
可以删除您发表的任何评论，但您不能删除任何人发表的评论。
```

输入此提示后，您应该看到 Claude Code 启动规划和规范起草过程。Claude Code 还将触发一些内置脚本来设置仓库。

此步骤完成后，您应该有一个新分支（例如 `001-create-taskify`），以及在 `specs/001-create-taskify` 目录中的新规范。

生成的规范应包含一组用户故事和功能需求，如模板中定义的那样。

在此阶段，您的项目文件夹内容应类似于以下内容：

```text
├── memory
│	 ├── constitution.md
│	 └── constitution_update_checklist.md
├── scripts
│	 ├── check-task-prerequisites.sh
│	 ├── common.sh
│	 ├── create-new-feature.sh
│	 ├── get-feature-paths.sh
│	 ├── setup-plan.sh
│	 └── update-claude-md.sh
├── specs
│	 └── 001-create-taskify
│	     └── spec.md
└── templates
    ├── plan-template.md
    ├── spec-template.md
    └── tasks-template.md
```

### **步骤3：** 功能规范澄清

创建基线规范后，您可以继续澄清第一次尝试中未正确捕获的任何需求。例如，您可以在同一个 Claude Code 会话中使用这样的提示：

```text
对于您创建的每个示例项目或项目，应该有5到15个任务之间的可变数量
任务，随机分布到不同的完成状态。确保每个完成阶段至少有一个任务。
```

您还应该要求 Claude Code 验证**审查和验收清单**，检查已验证/符合要求的事项，并保留未检查的事项。可以使用以下提示：

```text
阅读审查和验收清单，如果功能规范符合标准，请检查清单中的每个项目。如果不符合，请保留空白。
```

重要的是将与 Claude Code 的交互作为澄清和询问规范问题的机会 - **不要将其第一次尝试视为最终结果**。

### **步骤4：** 生成计划

现在您可以具体说明技术栈和其他技术要求。您可以使用项目模板中内置的 `/plan` 命令，提示如下：

```text
我们将使用 .NET Aspire 生成这个，使用 Postgres 作为数据库。前端应该使用
带有拖拽任务板的 Blazor 服务器，实时更新。应该创建一个 REST API，包含项目 API、
任务 API 和通知 API。
```

此步骤的输出将包括许多实现细节文档，您的目录树类似于：

```text
.
├── CLAUDE.md
├── memory
│	 ├── constitution.md
│	 └── constitution_update_checklist.md
├── scripts
│	 ├── check-task-prerequisites.sh
│	 ├── common.sh
│	 ├── create-new-feature.sh
│	 ├── get-feature-paths.sh
│	 ├── setup-plan.sh
│	 └── update-claude-md.sh
├── specs
│	 └── 001-create-taskify
│	     ├── contracts
│	     │	 ├── api-spec.json
│	     │	 └── signalr-spec.md
│	     ├── data-model.md
│	     ├── plan.md
│	     ├── quickstart.md
│	     ├── research.md
│	     └── spec.md
└── templates
    ├── CLAUDE-template.md
    ├── plan-template.md
    ├── spec-template.md
    └── tasks-template.md
```

检查 `research.md` 文档以确保根据您的指令使用正确的技术栈。如果任何组件突出，您可以要求 Claude Code 完善它，或者甚至让它检查您想要使用的平台/框架的本地安装版本（例如 .NET）。

此外，如果这是快速变化的东西（例如 .NET Aspire、JS 框架），您可能希望要求 Claude Code 研究所选技术栈的详细信息，提示如下：

```text
我希望您浏览实现计划和实现细节文件，
寻找可能受益于额外研究的领域，因为 .NET Aspire 是一个快速变化的库。对于您识别出
需要进一步研究的那些领域，我希望您使用我们将在此 Taskify 应用程序中使用的
特定版本的额外详细信息更新研究文档，并生成并行研究任务以使用
网络研究澄清任何细节。
```

在此过程中，您可能会发现 Claude Code 在研究错误的东西时卡住了 - 您可以使用这样的提示帮助引导它朝正确的方向：

```text
我认为我们需要将其分解为一系列步骤。首先，识别您在实现期间需要做的
您不确定或会受益于进一步研究的任务列表。写下这些任务的列表。
然后对于这些任务中的每一个，我希望您启动一个单独的研究任务，这样
净结果是我们并行研究所有这些非常具体的任务。我看到您正在做的是
看起来您正在研究一般的 .NET Aspire，我认为在这种情况下这对我们不会有太大帮助。
这是太无针对性的研究。研究需要帮助您解决特定的有针对性的问题。
```

>[!注意]
>Claude Code 可能过于急切并添加您没有要求的组件。要求它澄清理由和变更来源。

### **步骤5：** 让 Claude Code 验证计划

有了计划后，您应该让 Claude Code 运行它以确保没有遗漏的部分。您可以使用这样的提示：

```text
现在我希望您去审计实现计划和实现细节文件。
阅读它，着眼于确定是否有您需要做的任务序列
从阅读中显而易见。因为我不知道这里是否有足够的信息。例如，
当我查看核心实现时，参考实现细节中它可以找到信息的
适当位置会很有用，因为它遍历核心实现或细化中的每个步骤。
```

这有助于完善实现计划，并帮助您避免 Claude Code 在规划周期中遗漏的潜在盲点。一旦初始细化完成，在您进入实现之前，要求 Claude Code 再次浏览清单。

如果您安装了 [GitHub CLI](https://docs.github.com/en/github-cli/github-cli)，您也可以要求 Claude Code 继续从您当前分支到 `main` 创建一个带有详细描述的拉取请求，以确保努力得到适当跟踪。

>[!注意]
>在您让代理实现它之前，也值得提示 Claude Code 交叉检查细节，看看是否有任何过度工程的部分（记住 - 它可能过于急切）。如果存在过度工程的组件或决策，您可以要求 Claude Code 解决它们。确保 Claude Code 遵循 [constitution](base/memory/constitution.md) 作为在建立计划时必须遵守的基础部分。

### 步骤6：实现

准备就绪后，使用 `/implement` 命令执行您的实现计划：

```text
/implement
```

`/implement` 命令将：
- 验证所有先决条件都已到位（constitution、spec、plan 和 tasks）
- 从 `tasks.md` 解析任务分解
- 按正确顺序执行任务，尊重依赖关系和并行执行标记
- 遵循任务计划中定义的 TDD 方法
- 提供进度更新并适当处理错误

>[!重要]
>AI 代理将执行本地 CLI 命令（如 `dotnet`、`npm` 等）- 确保您的机器上安装了必需的工具。

实现完成后，测试应用程序并解决可能在 CLI 日志中不可见的任何运行时错误（例如，浏览器控制台错误）。您可以将此类错误复制并粘贴回您的 AI 代理进行解决。

</details>

---

## 🔍 故障排除

### Linux 上的 Git 凭据管理器

如果您在 Linux 上遇到 Git 身份验证问题，可以安装 Git 凭据管理器：

```bash
#!/usr/bin/env bash
set -e
echo "正在下载 Git 凭据管理器 v2.6.1..."
wget https://github.com/git-ecosystem/git-credential-manager/releases/download/v2.6.1/gcm-linux_amd64.2.6.1.deb
echo "正在安装 Git 凭据管理器..."
sudo dpkg -i gcm-linux_amd64.2.6.1.deb
echo "配置 Git 使用 GCM..."
git config --global credential.helper manager
echo "正在清理..."
rm gcm-linux_amd64.2.6.1.deb
```

## 👥 维护者

- Den Delimarsky ([@localden](https://github.com/localden))
- John Lam ([@jflam](https://github.com/jflam))

## 💬 支持

如需支持，请打开 [GitHub 问题](https://github.com/github/spec-kit/issues/new)。我们欢迎错误报告、功能请求以及关于使用规范驱动开发的问题。

## 🙏 致谢

这个项目深受 [John Lam](https://github.com/jflam) 的工作和研究的影响和基于。

## 📄 许可证

本项目根据 MIT 开源许可证的条款获得许可。请参阅 [LICENSE](./LICENSE) 文件了解完整条款。
