# 任务 1：第一次克隆——用 Git 克隆 Git

## 1. 总提交数

```bash
DCU@C13-404-18 MINGW64 /c/LyuTianle/work/famous-repos-tour/git (master)
$ git log --oneline | wc -l
80753
```

## 2. 第一次提交的日期和作者

```bash
DCU@C13-404-18 MINGW64 /c/LyuTianle/work/famous-repos-tour/git (master)
$ git log --reverse --pretty=format:"%an %ad" --date=short | head -1
Linus Torvalds 2005-04-07
```

## 3. 第一次提交的完整信息

```bash
DCU@C13-404-18 MINGW64 /c/LyuTianle/work/famous-repos-tour/git (master)
$ git show $(git rev-list --max-parents=0 HEAD)
commit 0ca71b3737cbb26fbf037aa15b3f58735785e6e3
Author: Avery Pennarun <apenwarr@gmail.com>
Date:   Fri Apr 24 14:13:34 2009 -0400

    basic options parsing and whatnot.

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000000..b25c15b81f
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1 @@
*~
diff --git a/git-subtree b/git-subtree
new file mode 120000
index 0000000000..7d7539894e
--- /dev/null
+++ b/git-subtree
@@ -0,0 +1 @@
git-subtree.sh
\ No newline at end of file
diff --git a/git-subtree.sh b/git-subtree.sh
new file mode 100755
```

# 任务 2：探索 Linux 内核历史

## 1. 前 10 名贡献者姓名

```bash
DCU@C13-404-18 MINGW64 /c/LyuTianle/work/famous-repos-tour/linux (master)
$ git shortlog -sn | head -10
     1  Linus Torvalds
```

因为用了 `git clone --depth=1 https://github.com/torvalds/linux.git` 克隆了 Linux 内核仓库。这意味着只下载了最新的 1 个提交，所以 `git shortlog -sn` 只能统计到这个提交的贡献者（Linus Torvalds）。

## 2. 最有趣的 3 个文件夹及原因

最有趣的 3 个文件夹及原因

基于 Linux 内核仓库的目录结构，这里是最有趣的 3 个文件夹及其原因（选择基于其在操作系统中的重要性和多样性）：

- **drivers/**: 这个文件夹包含所有硬件设备驱动程序，展示了 Linux 如何支持数千种硬件设备（如网卡、显卡、存储等）。有趣之处在于它体现了开源生态的广度——社区贡献者不断添加新驱动，使 Linux 能在各种设备上运行。
- **arch/**: 架构特定代码文件夹，包含针对不同 CPU 架构（如 x86、ARM、RISC-V）的代码。原因：它展示了 Linux 的跨平台能力，从桌面到嵌入式设备，无所不包，是内核多架构支持的核心。
- **Documentation/**: 庞大的文档文件夹，包含内核开发指南、API 文档和维护说明。原因：开源项目的文档文化在这里体现得淋漓尽致，它不仅帮助新贡献者入门，还记录了内核的历史和决策过程。

## 3. MAINTAINERS 文件中喜欢的一行

喜欢的行：`Orphan: No current maintainer [but maybe you could take the role as you write your new code].`

原因：这一行体现了开源项目的开放精神——当某个子系统没有维护者时，它鼓励开发者在贡献新代码时主动接手维护责任。这不仅促进了社区的可持续发展，还让新人有机会成长为维护者，体现了 Linux 内核的包容性和活力。

# 任务 3：选择本领域的著名仓库

## 1. 仓库名称及选择理由

```bash
$ git clone https://github.com/ollama/ollama.git
```

## 2. 最近一个月的活动量

```bash
DCU@C13-404-18 MINGW64 /c/LyuTianle/work/famous-repos-tour/ollama (main)
$ git log --since='1 month ago' --oneline | wc -l
76
```

## 3. 按 4.4 节 8 项健康清单评分

- [x] **最近提交**：近 6 个月是否有活动？
- [x] **Issue 回复**：维护者是否回复近期 issue？
- [x] **PR 合并节奏**：PR 是否在一周内被审查？
- [x] **贡献者人数**：是否过度依赖单一开发者？
- [x] **许可证**：是否存在明确的 LICENSE 文件？
- [x] **文档**：除了 README 外是否有 docs/ 文件夹或 Wiki？
- [x] **测试**：是否有 tests/ 文件夹和 CI 徽章？
- [x] **CONTRIBUTING.md**：贡献指南是否完善？

# 任务 4：追随一个人的足迹

## 1. 所选贡献者及其提交数

```bash
DCU@C13-404-18 MINGW64 /c/LyuTianle/work/famous-repos-tour/ollama (main)
$ git shortlog -sn | head -1
  1290  Michael Yang
```

## 2. 印象最深的一条提交信息

印象最深的提交信息：`deepseek2: upgrade to run v3+ models (#13166)`

原因：这条提交展示了 Ollama 对最新 AI 模型（DeepSeek v3+）的支持升级，体现了开源项目快速跟进行业发展的能力。它不仅涉及技术实现，还关联了具体的 PR (#13166)，反映了社区协作和持续创新的精神，让我印象深刻。

## 3. 该贡献者主要修改的文件或文件夹

基于统计，Michael Yang 主要修改的文件/文件夹如下（按修改次数排序）：

- **server/** 文件夹（尤其是 server/images.go: 131 次，server/routes.go: 124 次，server/upload.go: 43 次，server/download.go: 37 次）——这些文件涉及服务器路由、图像处理、上传/下载逻辑，显示他主要负责 Ollama 的服务器端功能开发。
- **ml/backend/ggml/** 和 **llm/** 文件夹（ml/backend/ggml/ggml.go: 48 次，llm/ggml.go: 45 次，llama/llama.go: 36 次）——这些是机器学习和 LLM（大语言模型）后端代码，表明他也深度参与模型推理和后端优化。
- **api/types.go**: 46 次 和 **cmd/cmd.go**: 73 次——API 类型定义和命令行工具，补充了整体架构。

总体上，他的工作集中在服务器管理和 AI 模型后端，体现了他在 Ollama 项目中的核心贡献者角色。

# 任务 5：测量你与第一次 PR 的距离

## 1. 3 个你认为可以挑战的 issue 链接

基于 Ollama 仓库的 "good first issue" 标签，以下是 3 个看起来可挑战的开放 issue（选择基于简单性和相关性）：

- Issue #12954: app: sidebar animates opening on load instead of appearing open - 前端 UI 动画问题，适合有基础 JavaScript/React 经验的人。
- Issue #10333: CLI: image path not recognized correctly - CLI 路径解析 bug，适合熟悉命令行工具和文件系统的人。
- Issue #4072: Ollama should prevent sleep when working - Windows 睡眠阻止功能，适合有系统编程经验的人。

## 2. 每个 issue 所需的技术栈

- **#12954**: JavaScript/TypeScript (前端), HTML/CSS (UI), 可能涉及 React 或类似框架（Ollama app 使用 Electron/Web 技术）。
- **#10333**: Go (Ollama 核心语言), CLI 开发, 文件路径处理。
- **#4072**: Go, Windows API (如 Power Management), 系统调用。

## 3. 用三句话总结 CONTRIBUTING.md

Ollama 的贡献指南强调优先处理 bug 和性能问题，避免添加新功能以减少维护负担，并要求非平凡更改先通过 issue 讨论。PR 提交时，提交消息格式为 "<package>: <short description>"，必须包含测试，并谨慎添加新依赖。指南还提供了设置开发环境的链接，并鼓励在 Discord 上寻求帮助。
