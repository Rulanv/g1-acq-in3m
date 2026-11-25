# 安装步骤（已按 Rulanv 生成，不需要再改任何文件）

模块里的脚本地址已经写死成你的仓库，你只需要上传 + 在小火箭里加同一个地址。

## 你的模块地址（复制保存）

```
https://cdn.jsdelivr.net/gh/Rulanv/g1-acq-in3m@main/g1-acq-in3m.sgmodule
```

---

## 第 1 步：建仓库

1. Chrome 打开 https://github.com/new
2. Repository name 填 `g1-acq-in3m`
3. 选 **Public**
4. 点 `Create repository`

## 第 2 步：上传这 3 个文件

打开（把地址粘到 Chrome 地址栏）：

```
https://github.com/Rulanv/g1-acq-in3m/upload/main
```

把下面 3 个文件一起拖进浏览器窗口：

```
g1-acq-in3m.sgmodule
g1-acq-discount.js
g1-sku-report-discount.js
```

然后点绿色 **Commit changes**（默认提交到 main 分支即可）。

## 第 3 步：在小火箭里加模块

1. 小火箭 → 首页 → **模块** → 右上角 `+`
2. 粘贴：`https://cdn.jsdelivr.net/gh/Rulanv/g1-acq-in3m@main/g1-acq-in3m.sgmodule`
3. 下载 → 启用
4. **关掉**以前所有 G1 改写模块（G1 ACQ / Ultra 75p / Ultra 一折 / G1 SKU Scan…），**只留这一个**
5. 断开再连接小火箭

> 刚提交后 jsDelivr 有 1–5 分钟延迟，下载 404 是正常的，等一会儿再试。
> 之后若改了文件但手机没变，浏览器打开下面地址刷缓存：
> `https://purge.jsdelivr.net/gh/Rulanv/g1-acq-in3m@main/g1-acq-discount.js`

---

## 第 4 步：确认装的是改造版

Safari 打开 `https://one.google.com/g1-sku-report`，应显示「本机脚本已接管」。

报告页新增一条规则，目标填 `com.google.gemini.2tb.ai.m.3month_ip_99p`：

- 官方版 → 保存被拒（提示目标只能用 g1. / com.google.one.）
- 改造版 → 保存成功，`mappingConfig.mode` 变 `custom`

能存进去 → 装对了。

---

## 第 5 步：下单

1. App Store 已登录**印度区 Apple ID**
2. 打开 **Gemini App**（不是 Google One App）→ 升级 / 方案页，等加载完
3. 回 Safari 报告页，在采集列表里找 5TB Pro 那条**源 SKU**
4. 新增规则：源 = 该源 SKU，目标 = `com.google.gemini.2tb.ai.m.3month_ip_99p`，保存
5. 关掉方案页 → 从 Gemini App **重新进**方案页（规则只对下一次响应生效）
6. 收银台应显示 **₹10 × 3 期**（合计 ₹30），标题 Google AI Pro（5TB）
7. 付款后到 App Store 订阅管理确认：下次扣费 = 3 期后，**₹1,950/月**

---

## 出问题对照

| 现象 | 处理 |
|---|---|
| 小火箭加模块 404 | 仓库不是 Public / 还没 Commit / jsDelivr 缓存（用 purge 地址刷） |
| 收银台提示商品不可用 | 该区没有这个 SKU，依次换 `_90p`、`_75p`、`..._90p.acq`、`..._75p.acq` |
| 收银台显示 ₹1,950 | 规则没命中：报告页看 `test.matchedFrom` 目标是否 `count>0`，并确认保存后**重进了方案页** |
| 报告页显示普通 Google 页面 | 模块没启用 / HTTPS 解密没开 / 证书没信任 / hostname 缺 `one.google.com` |
| 在 Google One App 或 Safari 里买 | `com.google.gemini.*` 只有 Gemini App 能拉商品 |

## 边界

- intro offer 每个 Apple ID 每个订阅组**只有一次**；
- 模块只改 SKU 字符串，不改价格字段，价格由 Apple 按 storefront 下发；
- 别同时开多个改写模块。
