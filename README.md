# 旺店通委外出入库与订单

在阿里云 ECS Workbench RDP 里的 **旺店通 ERP 企业版**上，完成委外入库/出库/开单、订单客审、手工建单，以及库存按待发货排序截图。

## 使用

仓库地址：<https://github.com/willgrt-stack/wangdiantong-outsourcing-orders-skill>。

在支持安装 GitHub Skill 的 Agent 中，可以说：

```text
从 https://github.com/willgrt-stack/wangdiantong-outsourcing-orders-skill
安装 skills/wangdiantong-outsourcing-orders 目录里的旺店通委外出入库与订单 Skill。
```

把 `skills/wangdiantong-outsourcing-orders/` 整个文件夹放入所用 Agent 的技能目录。

例如：

```text
用旺店通委外出入库与订单：
在 05ISAKELY仓 做一笔加工入库，货品前缀 ISAKELY，数量按演示 10/20/30，
保存并审核后回报单号。
```

需要已登录的 Workbench RDP 会话（实例演示：`i-bp18qh7v25tcscbv1qq3`，杭州）。客审/强制审核会改真实单据，生产环境执行前先确认；强制审核密码只能由操作者当场提供，Skill 不会也不应内置密码。

## 文件

- [Skill 入口](skills/wangdiantong-outsourcing-orders/SKILL.md)

## 更新

通过复制文件安装的版本不会自动更新。需要更新时，把仓库链接发给 Agent，要求先比较仓库版本与本地版本、保留自己的修改，再更新 `wangdiantong-outsourcing-orders` 目录。

版本：0.1.0。
