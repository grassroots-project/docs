# 资源管理

如何维护资源池。

## 资源池位置

[`data/resources.md`](https://github.com/grassroots-project/tasks/blob/main/data/resources.md)（在 grassroots-tasks 仓库中）

## 添加资源

通过 GitHub Issue 表单自动化添加：

1. 填写 [添加资源表单](https://github.com/grassroots-project/tasks/issues/new?template=add_resource.yml)
2. 管理员审核后打 `approved` 标签
3. GitHub Action 自动生成 PR，将资源添加到 `data/resources.md`
4. 合并 PR 后资源入库

### 资源模板

```markdown
### [资源名称]

- **资源类型**：比特币/知识/工具/人力/其他
- **描述**：[具体描述]
- **当前状态**：可用/已占用/待规划/暂停
- **负责人**：[你的名字/昵称]
- **使用说明**：[如何使用这个资源]
- **链接**：[相关链接，如果有]
```

## 更新资源状态

通过 Issue 表单自动化更新：

1. 填写 [更新资源状态表单](https://github.com/grassroots-project/tasks/issues/new?template=update_resource.yml)
2. 管理员打 `approved` 标签后，GitHub Action 直接提交更新

## 申请使用资源

通过 Issue 表单驱动：

1. 填写 [申请使用资源表单](https://github.com/grassroots-project/tasks/issues/new?template=use_resource.yml)
2. 管理员打 `approved` 标签后，自动更新资源状态为"已占用"并记录使用信息
3. 使用完毕关闭 Issue，资源状态自动恢复为"可用"

## 资源类型

| 类型 | 说明 | 示例 |
|------|------|------|
| 比特币 | 资金类资源 | 项目基金、奖励池 |
| 知识 | 文档、资料 | 项目文档、研究报告 |
| 工具 | 软件、服务 | AI 工具、设计软件 |
| 人力 | 时间、技能 | 咨询、培训 |

## 资源状态

| 状态 | 说明 |
|------|------|
| 可用 | 可以直接使用 |
| 已占用 | 当前有人在用 |
| 待规划 | 尚未明确用途 |
| 暂停 | 暂时不可用 |

## 资源页面

[资源池页面](https://www.grassroots-project.app/pages/resources.html) 会自动：
- 解析资源列表
- 显示统计（可用/已占用/待规划）
- 支持按类型筛选
