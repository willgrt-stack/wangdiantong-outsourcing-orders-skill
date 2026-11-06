# 旺店通企业版 Skills

在阿里云 ECS Workbench RDP 里的 **旺店通 ERP 企业版**上用的两套 Agent Skill：委外出入库/订单，以及货品档案新建与维护。

仓库：<https://github.com/willgrt-stack/wangdiantong-outsourcing-orders-skill>。

## Skills

| 目录 | 用途 |
| --- | --- |
| [skills/wangdiantong-outsourcing-orders](skills/wangdiantong-outsourcing-orders/SKILL.md) | 委外入库/出库/开单、订单客审、手工建单、库存按待发货排序截图 |
| [skills/wangdiantong-product-archive](skills/wangdiantong-product-archive/SKILL.md) | 货品档案新建、编辑、搜索、停用/启用 |

## 使用

在支持安装 GitHub Skill 的 Agent 中，可以说：

```text
从 https://github.com/willgrt-stack/wangdiantong-outsourcing-orders-skill
安装 skills/ 下的旺店通相关 Skill。
```

把对应文件夹整份拷进所用 Agent 的技能目录。

例如：

```text
用旺店通货品档案：新建货品，名称/分类/品牌按我说的填，条码用唯一值，保存后回报。
```

```text
用旺店通委外出入库与订单：
在 05ISAKELY仓 做一笔加工入库，货品前缀 ISAKELY，数量按演示 10/20/30，
保存并审核后回报单号。
```

需要已登录的 Workbench RDP 会话（实例演示：`i-bp18qh7v25tcscbv1qq3`，杭州）。客审/强制审核/停用启用会改真实单据，生产环境执行前先确认；强制审核密码只能由操作者当场提供，Skill 不会也不应内置密码。

## 更新

通过复制文件安装的版本不会自动更新。需要更新时，把仓库链接发给 Agent，要求先比较仓库版本与本地版本、保留自己的修改，再更新对应目录。

版本：0.2.0。
