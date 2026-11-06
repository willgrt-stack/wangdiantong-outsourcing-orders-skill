---
name: 旺店通货品档案
description: >-
  Use when creating, editing, searching, disabling, or enabling products in
  旺店通企业版 货品档案 on the Aliyun ECS Windows host (via Workbench RDP).
---
# 旺店通货品档案（企业版）

## Where this runs
Assumes signed-in Aliyun ECS Workbench RDP into the Hangzhou Windows host (`ecs-workbench.aliyun.com`, instance used for ISAKELY ops), with **旺店通ERP企业版** already open or launchable from the Windows taskbar. Do not invent ERP/Aliyun passwords; use the saved Workbench credential / existing session.

## Goal
Create and maintain SKUs in **货品 → 货品档案** (Product Archive). This skill is **not** 订单审核 or 入库; those need a separate teach.

## Inputs (parameterize)
- `{product_name}` — 货品名称 / 简称
- `{category}` — 分类（demo used `测试1`）
- `{brand}` — 品牌（demo used `测试`）
- `{unit}` — 单位（demo used `件`）
- `{spec_name}` — 规格名称
- `{barcode}` / `{spec_code}` — 条码 / 规格编码（must be unique; duplicate barcode shows 条码已经存在）
- `{search}` — 货品编号/简称/条码 search string

## Steps
1. In 旺店通, open left nav **货品 → 货品档案**.
2. **新建**: toolbar **新建** → fill 货品名称/简称, 分类, 品牌, 单位; in the specs grid fill 规格名称 + 条码 (and 规格编码 if needed) → **保存** → **确定** on 保存成功.
3. Add another spec with **+ 新增**; delete a bad row with checkbox + **删除** before save if needed.
4. On barcode conflict, change 条码/规格编码 to a unique value and **保存** again.
5. **打开详情**: double-click a list row → **货品详情**; use **编辑** to change fields (e.g. 简称, 规格编码, 条码) → **保存** → **确定**; close the tab with X.
6. **搜索**: type `{search}` in 货品编号/简称/条码 → **搜索**.
7. **停用**: select row → **停用** → confirm; default list hides disabled (停用=否). To find them, set 停用 filter to show disabled → **搜索**.
8. **启用**: select disabled row → **启用** → confirm; set 停用 filter back to 否 → **搜索**.
9. Cancel an unfinished create with **退出** → confirm 是否取消新建.

## Report back
Product name, barcode/spec codes saved, and whether disable/enable was applied. Do not store test names as production defaults unless the user says so.

## Consequential
停用/启用 and Save change live ERP data — confirm with the user before running on real SKUs (demo used test values like `测试` / `letsgogo` / `yili`).
