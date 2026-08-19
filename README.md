# LLM 用量成本对比计算器

<div align="right">
  [![English](https://img.shields.io/badge/English-README-blue?style=for-the-badge)](README.en.md)
</div>

对比 **DeepSeek 官方**（元/百万 tokens，分 Flash / Pro 定价）与**其他积分制平台**（积分/百万 tokens）的月度成本，自动按「小时分布法」从你的用量 CSV 推算高峰/空闲占比，实时给出三渠道月费对比与最省方案。

- 纯前端单文件 HTML，可离线使用，数据不出本机
- 自动按模型分 Flash / Pro 统计用量
- DeepSeek Flash / Pro 官方价一键填入
- 其他平台默认「空闲 = 高峰」链接同步，点 🔗 解锁分别定价
- 中 / 英双语界面（右上角切换）
- 导出 CSV / JSON 存档

## 截图

### 中文界面
![中文界面](HTML界面中文.png)

### 英文界面
![English UI](HTML界面英文.png)

## 用法

1. 从 **DeepSeek 控制台**导出消费明细 CSV（点页面上的「**导出**」按钮）：

   ![导出 CSV 教程](导出csv教程图.png)

2. 双击打开 [`LLM成本对比计算器.html`](LLM成本对比计算器.html)，点击「**点击此按钮展示示例数据**」先看效果。

3. 把你的 CSV **拖入页面**或点击上传区导入；工具自动分模型统计 Flash / Pro 用量。

4. 调整 DeepSeek / 其他平台单价（可一键填官方价）、高峰时段、转换率。

5. 查看底部 **月费对比** 与 **明细表**，一键导出结果。

## 算法口径

- 每行 amount 在 `[start, end)` 内按小时均匀摊，落在高峰窗口的小时计入高峰 → 自动推导峰谷用量占比
- 加权单价 = 空闲占比 × 空闲价 + 高峰占比 × 高峰价
- 月用量 = 区间用量 × `30 / 覆盖天数`
- DeepSeek 官方成本 = Flash 用量 × Flash 价 + Pro 用量 × Pro 价（按模型名自动匹配）
- 其他平台 = 总用量 × 积分价 × `1积分=多少元`

## 文件

- `LLM成本对比计算器.html` — 主程序（单文件，无依赖）
- `HTML界面中文.png` / `HTML界面英文.png` — 界面截图
- `导出csv教程图.png` — DeepSeek 控制台导出 CSV 步骤

## 许可

MIT
