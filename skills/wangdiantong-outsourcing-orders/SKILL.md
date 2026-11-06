---
name: 旺店通委外出入库与订单
description: >-
  Use on Aliyun ECS Windows 旺店通企业版 for 委外入库单/委外出库单/委外出入库开单、订单客审、手工建单；includes
  WMS push failure checks and force-audit notes.
---
# 旺店通委外出入库与订单

## Where
Aliyun Hangzhou ECS Workbench RDP → Windows → **旺店通ERP企业版** (assumes already signed in). Prefer reconnect with saved credentials if Workbench drops (`网络连接断开…` → **重新连接**).

Instance used in demos: `i-bp18qh7v25tcscbv1qq3` (cn-hangzhou).

Prefer running via **Will's Mac Chrome** Workbench when the bot box browser cannot reach Aliyun (keep Shadowrocket on with Aliyun DIRECT).

## A. 委外入库单（create → 保存 → 审核）
1. Top menu **委外出入库 → 委外入库单** (or open existing list then **新建**).
2. Set **入库仓库** to `{warehouse}` (demo: type `05` → **05ISAKELY仓**).
3. Set **入库类别** to `{inbound_category}` (demo: **加工入库**).
4. **添加货品** → in dialog, 商家编码 search `{merchant_code_prefix}` (demo: `ISAKELY`) → **搜索**.
5. Enter **数量** per selected SKU line (`{qty}` per line; demo pattern 10/20/30 on ISAKELY…ISAKELY05), then **确定选中货品**.
6. **保存** → **审核** → confirm **是** → in audit dialog set **入库日期** `{audit_date}` if prompted → **确定**.
7. Report 单号 / status to the user when they asked for numbers.

## A2. 委外出入库开单（alternate path, 2026-11-06 demo）
1. **库存 → 委外管理 → 委外出入库开单** (or open **委外出入库单管理** then create).
2. **单据类型** = **委外入库**.
3. **仓库** = `{warehouse_alt}` (demo: **ISAKELY买手店**).
4. **运输模式** = `{ship_mode}` (demo: **到仓自提**).
5. Open **单品选择** → search by 商家编码 `{sku_code}` (demo codes: `xiehuajtxh` 焦糖星火, `xiehuawyly` / `xiehuaygzz` 夜光珍珠) → set qty → **保存** selection into the form.
6. Save/submit the 开单. Check **委外出入库单管理** for new 单号 (demo: `WK202611060001`) and **推送信息**.
7. If push fails with `商品{code}未上传wms`, stop and tell the user — upload that SKU to WMS before retrying push. Do not invent a workaround.

## B. 委外出库单（create → 保存 → 审核）
1. Top menu **委外出入库 → 委外出库单** → **新建**.
2. Set **出库仓库** to `{warehouse}` (demo: **05ISAKELY仓**).
3. Set **出库类别** to `{outbound_category}` (demo: **加工发料**).
4. **添加货品** same as A with `{merchant_code_prefix}` and `{qty}` lines → **确定选中货品**.
5. **保存** → **审核** → **是** → set **出库日期** `{audit_date}` if prompted → **确定**.

## C. 订单客审
1. **订单 → 订单处理 → 订单审核** (or top **订单管理 → 订单审核**).
2. Select target row(s) → **客审** / **快速审核** / right-click **客审通过** → 确定.
3. If dialog **订单快速审核失败原因** appears:
   - Platform already shipped → UI says right-click **强制审核**. Only do 强制审核 when the user already gave the force-audit password for this run; never invent the password.
   - 可审核库存不足 → skip that order; report SKU and stock to the user.
4. If risk dialog appears: only **忽略风险，强制通过** when the user already approved that for this run.

## D. 手工建单（earlier demo）
1. **订单 → 订单处理 → 手工建单**.
2. 店铺 + 发货仓库 = `{shop_or_warehouse}`.
3. Fill 买家账号 / 收件人 / 手机; **省市区 must be filled** or save fails.
4. Add SKUs by merchant code, set quantities → **保存** → **审核**.

## E. 库存管理截图（待发货）
1. Open **库存管理** / **库存查询**.
2. Set warehouse if needed (`ISAKELY买手店` or `05ISAKELY仓`).
3. Sort or filter by **待发货** (column 待发货 / 待发货量).
4. Screenshot and deliver the image to the user.

## Inputs
`{warehouse}`, `{warehouse_alt}`, `{inbound_category}`, `{outbound_category}`, `{merchant_code_prefix}`, `{sku_code}`, `{qty}` per line, `{audit_date}`, `{ship_mode}`, force-audit password (user-provided only), and for manual orders buyer/recipient/phone/省市区.

## Consequential
审核 / 客审 / 强制审核 / 强制通过 change live ERP data — confirm with the user before production runs. Demo quantities and dates are examples; do not reuse unless asked.

## Related
Product master: [旺店通货品档案](../wangdiantong-product-archive/SKILL.md)。
