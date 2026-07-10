# 贡献指南

## Commit 规范

用 Conventional Commits。格式是 `type(scope): subject`，空一行写正文。

类型。

- `feat` 新功能或新 skill
- `fix` 修 bug
- `docs` 只改文档
- `refactor` 重构不改行为
- `chore` 杂项，构建、配置、依赖

作用域用 skill 名，比如 `de-ai-zh`。仓库级别改动可以省略 scope。

subject 简短，说明做了什么。正文说明为什么，不是再复述一遍做了什么。

例子。

```
feat: add de-ai-zh skill

中文去 AI 味底味 skill，从病根入手不只替换词汇。主文件自洽，配五个 references 按需查。
```

```
fix(de-ai-zh): 修活人感终审漏判的情况

正文判断被误判成 AI 味，因为没区分个人视角和旁白腔。补一条判据。
```

## Skill 结构

新建 skill 建一个目录，主文件是 `SKILL.md`，frontmatter 至少要有 `name` 和 `description`。主文件自洽，只读主文件就能跑完全套判断，长内容拆进 `references/`。

`description` 写得越具体，自动触发的准确率越高。写清楚适用场景和不适用的边界。
