# 成员管理

如何维护人才库。

## 人才库位置

[`data/people.md`](https://github.com/grassroots-project/tasks/blob/main/data/people.md)（在 grassroots-tasks 仓库中）

## 添加新成员

新成员通过自动化流程加入：

1. 申请人填写 [GitHub Issue 表单](https://github.com/grassroots-project/tasks/issues/new?template=join_request.yml)
2. 管理员审核后打 `approved` 标签
3. GitHub Action 自动生成 PR，将成员信息添加到 `data/people.md`
4. 合并 PR 后成员正式入库

无需手动编辑。

### 成员模板

```markdown
### [名字/昵称]

- **GitHub**：@username
- **加入时间**：YYYY-MM-DD
- **技能标签**：[用逗号分隔]
- **时间承诺**：每周 Xh
- **当前任务**：无
- **历史贡献**：-
```

## 任务状态自动同步

成员的任务信息由 GitHub Action 自动维护：

- Issue 打"进行中"标签 → 自动更新"当前任务"
- Issue 打"已完成"标签 → 自动归入"历史贡献"
- 统计表在 Issue/PR 变更时自动重建

成员无需手动更新任务相关字段。

## 成员统计

人才库页面会自动展示：
- 成员总数
- 每人的任务参与情况
- 最近活动

## 退出机制

成员可以随时退出：
- 通知项目发起人
- 可选择保留或删除人才库信息
- 历史贡献记录通常保留
