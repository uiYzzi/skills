# skills

我的个人 agent skills 合集。每个 skill 是一个独立目录，主文件是 `SKILL.md`，长清单和示例放 `references/` 子目录。遵循 [agent skills 规范](https://agentskills.io)，可以装到任何支持的 agent。

## 现有的 skills

- [de-ai-zh](./de-ai-zh/)：中文去 AI 味底味，面向脚本、小说、文案、文章这类要交付的成段写作

## 怎么装

用 [skills CLI](https://skills.sh) 从这个仓库安装。

```bash
# 装所有 skills
npx skills add uiYzzi/skills

# 只装某一个
npx skills add uiYzzi/skills --skill de-ai-zh

# 装到全局（跨项目可用）
npx skills add uiYzzi/skills -g

# 装到指定 agent
npx skills add uiYzzi/skills -a claude-code -a cursor

# 先列出仓库里有哪些 skill
npx skills add uiYzzi/skills --list
```

CLI 会自动检测你装了哪些 agent，没有检测到会问你要装到哪几个。项目级装在 `./<agent>/skills/`，全局装在 `~/<agent>/skills/`。推荐用默认的 symlink 方式，单一来源，好更新。

不用装也能试用，直接生成 prompt 喂给 agent：

```bash
npx skills use uiYzzi/skills@de-ai-zh --agent claude-code
```

## 怎么加新 skill

新建一个目录，里面写 `SKILL.md`。frontmatter 至少要有 `name` 和 `description` 两个字段：

```markdown
---
name: my-skill
description: 这个 skill 做什么，什么时候用
---

# my-skill

具体指令。
```

主文件自洽，只读主文件就能跑完全套判断，长内容拆进 `references/`。这样上下文塞得少，模型遵循率高。

`description` 写得越具体，自动触发的准确率越高。写清楚适用场景和不适用的边界，别只写一句通用的话，否则该触发时不触发，不该触发时乱触发。

## 目录约定

```
skills/
  README.md          本文件
  <skill-name>/
    SKILL.md         主文件，frontmatter 加正文
    README.md        这个 skill 的说明
    references/      长清单、示例、参考资料，按需读
```

## 一点说明

这里的 skill 偏向写作和文本处理，不是代码工具。我自己用着顺手才放上来，每个都在实际使用里迭代过几轮。skill 文件本身可以改，skills 本来就该越用越准。
