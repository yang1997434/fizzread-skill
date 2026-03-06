[English](README.md) | [中文](README.zh-CN.md)

# FizzRead — OpenClaw Skill

在 AI 对话中即时获取 100K+ 本非虚构书籍摘要和 1 分钟音频预览。内置免费 Demo Key，无需注册即可使用。由 [FizzRead](https://www.fizzread.ai) 提供支持。

## 功能

- **每日一书** — 每天获取一本精选书籍推荐，含摘要和音频
- **书籍搜索** — 在 100K+ 本书中按关键词、书名或作者搜索
- **书籍摘要** — 阅读完整摘要，收听 1 分钟音频预览
- **分类推荐** — 按主题浏览书籍（心理学、效率、商业等）
- **多语言** — 摘要自动翻译为你的语言；音频保持英文原版

## 快速开始

### 1. 安装 Skill

直接对你的 OpenClaw 机器人说：

> 安装这个 skill: https://github.com/yang1997434/fizzread-skill 并重启 gateway 生效

或通过命令行：

```bash
claw install fizzread-skill
```

### 2. 直接使用 — 无需配置

本 skill 内置 **免费 Demo API Key**，安装即用，无需注册。直接开始对话！

### 3.（可选）使用自己的 API Key

如需更高调用频率，获取自己的 key 并设置为系统环境变量：

1. 访问 [fizzread.ai](https://www.fizzread.ai) 并注册账号
2. 进入 **设置 > API Keys > 生成**
3. 添加到 shell 配置文件（`~/.bashrc` 或 `~/.zshrc`）：

```bash
export FIZZREAD_API_KEY="your_key_here"
```

然后重启终端或运行 `source ~/.zshrc`。

### 试试看

直接和你的 AI 对话：

- "今天推荐什么书？"
- "搜索关于习惯的书"
- "推荐一些心理学书籍"
- "介绍一下《原子习惯》"

## 使用示例

### 每日一书

> **你：** 今天推荐什么书？
>
> **AI：** 今日推荐 — *Thinking, Fast and Slow*，作者 Daniel Kahneman
>
> 人类思维通过两个系统运作：快速直觉的系统 1 和缓慢理性的系统 2……
>
> [1 分钟音频预览（英文）](https://nccgpub.blob.core.windows.net/media/xxx.mp3)

### 搜索

> **你：** 找一些关于效率的书
>
> **AI：**
> 1. *Atomic Habits* — James Clear
> 2. *Deep Work* — Cal Newport
> 3. ...

### 分类浏览

> **你：** 推荐一些商业类书籍
>
> **AI：** 商业类热门书籍（共 287 本）：...

## 每日定时推送

配置 cron 触发器，每天自动接收一本书推荐：

```yaml
cron: "0 8 * * *"    # 每天早上 8:00
```

详情请参考 OpenClaw cron 调度文档。

## 常见问题

| 问题 | 解决方法 |
|------|---------|
| "API key 无效" | 内置 demo key 应该开箱即用。如使用自己的 key，检查 `FIZZREAD_API_KEY` 是否正确。如需要，在 [fizzread.ai](https://www.fizzread.ai) 重新生成。|
| "未找到书籍" | 尝试不同或更宽泛的搜索关键词。|
| 回复中没有音频 | 并非所有书籍都有音频预览，skill 会自动跳过无音频的书。|
| 频率限制错误 | 稍等片刻再试。API 允许每分钟 100 次请求。|

## 工作原理

本 skill 是纯指令驱动的 OpenClaw skill（无脚本或模块）。AI 读取 SKILL.md 中的指令，用 `curl` 调用 FizzRead API，然后将结果格式化呈现给你。所有书籍内容直接来自 FizzRead 数据库，不使用 AI 生成摘要。

## 许可证

[MIT](LICENSE)
