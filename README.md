# 鸡蛋经费统计 Agent Skills

为[鸡蛋经费统计](https://egg-budget-cn.lifangyuanaa643449.chatgpt.site/#overview)准备的三项可复用技能，兼容 Cursor、Claude Code 与 Codex。

## 技能

| 技能 | 用途 | 调用示例 |
| --- | --- | --- |
| `egg-budget-recharge` | 登记并核验经费充值 | “充值 500 元，备注行政经费” |
| `egg-budget-consumption` | 登记并核验个人吃蛋数量与自动分摊花费 | “今天王晓琳吃了 2 枚鸡蛋” |
| `egg-budget-purchase` | 登记并核验采购数量、总价、商家与自动单价 | “今天在盒马买了 96 枚，共 113.28 元” |

## 目录兼容性

- Cursor 与 Codex 直接读取 `.agents/skills/` 中的标准 `SKILL.md`。
- Claude Code 从 `.claude/skills/` 读取轻量兼容入口，再加载同一份标准技能，避免维护三套业务规则。
- 每个标准技能都包含 `agents/openai.yaml`，用于 Codex 的技能列表名称、简介与默认提示。

## 使用

将仓库克隆到一个项目目录并从仓库根目录启动对应工具。随后可以显式调用：

- Cursor：`/egg-budget-recharge`、`/egg-budget-consumption`、`/egg-budget-purchase`
- Claude Code：`/egg-budget-recharge`、`/egg-budget-consumption`、`/egg-budget-purchase`
- Codex：`$egg-budget-recharge`、`$egg-budget-consumption`、`$egg-budget-purchase`

也可以直接用中文描述需求；各工具会根据技能的 `description` 自动匹配。

## 运行前提与数据范围

这些技能通过网页表单登记真实数据，因此运行它们的 Agent 需要浏览器自动化或 computer-use 能力。没有该能力时，技能只会整理字段并给出手动步骤，不会虚报成功。

当前网站把采购、食用和充值记录保存在操作浏览器的本地存储中，而不是共享数据库。登记结果只在执行操作的浏览器/设备上可见；清除浏览器网站数据可能同时清除这些记录。

## 格式依据

- [OpenAI：Build skills](https://developers.openai.com/codex/skills)
- [Cursor：Agent Skills](https://cursor.com/docs/skills)
- [Anthropic：Extend Claude with skills](https://code.claude.com/docs/en/skills)
