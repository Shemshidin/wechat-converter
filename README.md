# Wechat Converter · 公众号排版装机包

Obsidian 插件 **Wechat Converter v2.12.0** 的可直接安装版本，附 AI 排版技能包。

- 上游项目：[DavidLam-oss/obsidian-wechat-converter](https://github.com/DavidLam-oss/obsidian-wechat-converter)（MIT）
- 本仓库只是把编译好的运行时（`main.js` / `styles.css` / `manifest.json`）和 `ai-layout-skills/` 打包出来，方便直接装机；源码、Issue、更新请看上游。
- 版权归原作者 **林小卫 (DavidLam)**，见 [LICENSE](LICENSE)。本仓库不修改任何代码。

## 它做什么

Markdown → 微信公众号后台可直接粘贴的富文本：

- 预览什么样，粘进公众号就什么样（内联样式，不依赖外部 CSS）
- 宽表格自动横向滑动，手机上不被压扁
- 图片横滑、敏感图先遮罩
- 代码块、Mermaid、数学公式、引用/Callout 样式
- 中文标点规范化（中英文之间加空格、全角标点等，已保护链接和代码）
- 一键同步到公众号草稿箱（需 AppID / AppSecret）
- 多平台分发：知乎、CSDN、掘金、小红书等（需配套浏览器插件）

## 安装

1. 本页右上 **Code → Download ZIP**，解压。
2. 在 Obsidian 库目录下建文件夹：`.obsidian/plugins/wechat-converter/`
3. 把 `main.js`、`manifest.json`、`styles.css` 三个文件放进去（`ai-layout-skills/` 一并放入，AI 编排要用）。
4. Obsidian → 设置 → 第三方插件 → 关闭安全模式 → 刷新 → 启用 **Wechat Converter**。

最终路径长这样：

```
<你的库>/.obsidian/plugins/wechat-converter/
├── main.js
├── manifest.json
├── styles.css
└── ai-layout-skills/
```

## 使用

1. `Ctrl/Cmd + P` → 搜 `Open Wechat Converter`（或点左侧 🪄 图标）
2. 右侧实时预览当前笔记
3. 点底部 **📋 复制到公众号** → 打开公众号后台编辑器 → `Ctrl/Cmd + V`
4. （可选）设置里填好公众号 AppID / AppSecret，点 **🚀 一键同步** 直接进草稿箱
   - 公众号后台 → 设置与开发 → 基本配置 拿 AppID / AppSecret
   - 服务器 IP 必须在该页面的 IP 白名单里，否则同步会报 40164

## Markdown 用法速查

| 需求 | 写法 |
|---|---|
| 普通表格 | 标准 Markdown 表格；列多或超宽时自动左右滑动 |
| 图片横滑 | `> [!image-swipe] 左右滑动查看图片` 后接多行图片 |
| 敏感图遮罩 | `> [!image-sensitive] 此类图片可能引发不适，向左滑动查看` 后接图片 |
| 摘要 / 封面 | frontmatter 里写 `excerpt` / `cover` |
| 数学公式 | `$...$` / `$$...$$`（导出时转图片） |

## AI 排版技能（ai-layout-skills/）

插件「AI 编排」用的布局家族，每个目录含 `SKILL.md`（说明）、`prompt.md`（给模型的提示词）、`blocks.json`（可用区块）、`fallback.json`（无 AI 时的降级策略）：

| 目录 | 名称 | 适合 |
|---|---|---|
| `source-first` | 原文增强型 | 长文、笔记、知识库（最接近原文，默认推荐） |
| `tutorial-cards` | 教程卡片型 | 步骤、清单、案例拆解 |
| `editorial-lite` | 轻杂志型 | 观点、经验、品牌表达 |

`_shared/` 里是共用的区块目录、配色表和 JSON Schema（`article-layout.schema.json`），让 AI 按 schema 产出可被插件消费的布局 JSON。

## 注意事项

- 插件配置存在 `data.json`，里面有公众号 AppSecret、AI Key 等，**不要提交到公开仓库**（本仓库已 `.gitignore`）。
- 版本固定 2.12.0；要跟进新版，直接去上游 Release 或装 BRAT 加 `DavidLam-oss/obsidian-wechat-converter`。
- 上游 README 里还有 Cloudflare Worker 反代方案（解决固定 IP 白名单问题），有需要自己去翻。
