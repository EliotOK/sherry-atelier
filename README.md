# 橘雪莉工坊 / Sherry Atelier

一套面向 DSH Web GUI 的 v2 皮肤：**半透明深蓝玻璃界面 + 时段自动切换壁纸**。

| | |
|---|---|
| **id** | `sherry-atelier` |
| **版本** | 1.0.0 |
| **作者** | 橘雪莉 |
| **强调色** | `#5b8fd6` |
| **须要 hooks** | 是（`facets.client`）|

> ⚠️ **本皮肤是衍生作品**。来源、授权与署名见下方「来源与授权」一节，**这是本提交的必要说明**。

---

## 效果概览

| 部位 | 说明 |
|---|---|
| **顶部** | 半透明深蓝玻璃，与顶栏、右侧栏使用同一色源（`--dsw-specific-sidebar-fill`）|
| **顶栏** | 玻璃底 + `对话/轨迹`、标题、状态、右侧图标在同一行；空间不足时左侧内容自动折行；三个工具图标钉在右上 |
| **左侧栏** | 半透明玻璃（无模糊），展开/收起沿用 app 原生网格过渡 |
| **右侧栏** | 与顶栏同款半透明玻璃蒙版（按需**不加模糊**）|
| **壁纸** | 铺满整屏（含顶部条带区域），按时段自动切换三张场景图 |
| **工作区选中态** | 简洁玻璃底 + 细描边（原版的缎带装饰已移除）|

### 壁纸时段

| 时段 | 场景 | 素材 |
|---|---|---|
| 08:00–18:00 | 雨中踩水（街道）| `assets/sherry-scene-puddle.jpg` |
| 18:00–02:00 | 咖啡厅夜读 | `assets/sherry-scene-coffee.jpg` |
| 02:00–08:00 | 草坪仰望星空 | `assets/sherry-scene-lawn.jpg` |

`backgroundMedia.dark` 指向咖啡图，使**启动首帧**与常见时段一致，避免闪图。

---

## 来源与授权

**本皮肤是衍生作品**，上游是一条完整的创作链。依 CC BY-NC-SA 4.0 的
**署名（BY）** 与 **相同方式共享（SA）** 要求，完整保留如下：

| 层级 | 作者 | 贡献 | 链接 |
|---|---|---|---|
| **一创** | **上善** | 鲸鱼娘（whale-girl）角色形象原作 | [pixiv/62155430](https://www.pixiv.net/users/62155430) |
| **二创** | **zipzip** | 在上善形象上加入 DeepSeek 元素的女仆鲸鱼娘（生成模型 GPT Image 2）| [pixiv/18604994](https://www.pixiv.net/users/18604994) |
| **三创** | **Small-tailqwq** | 上游皮肤「maid-atelier / 深海女仆工坊」| [dsh-deep-whale](https://github.com/Small-tailqwq/dsh-deep-whale/tree/main/maid-atelier) |
| **四创** | **橘雪莉** | **本皮肤**「sherry-atelier / 橘雪莉工坊」| — |

| 项 | 内容 |
|---|---|
| **原版皮肤** | Abyssal Maid Atelier（id: `maid-atelier`）v0.3.2 |
| **原版许可** | **CC BY-NC-SA 4.0** |
| **本版许可** | **CC BY-NC-SA 4.0**（继承：署名 + 非商业性使用 + 相同方式共享）|

授权文字位置：

- `skin.json` 的 `license` / `licenseUrl` / `noticeUrl` / `sourceUrl` / `attribution`
- `NOTICE` —— 本皮肤的衍生作品声明（含完整创作链）
- `LICENSE` —— 上游 CC BY-NC-SA 4.0 原文
- `ATTRIBUTION/` —— 上游 `NOTICE` / `skin.json` 原文副本（verbatim）
- `hooks.mjs` 头部注释的「来源与授权」段

本皮肤使用的**橘雪莉形象与场景壁纸**由本皮肤作者生成：

| 项 | 内容 |
|---|---|
| 生成方式 | **ComfyUI 本地生成** |
| 基础模型 | Illustrious / SDXL 系（`waiIllustriousSDXL v17.0`）|
| 角色 LoRA | 橘雪莉角色 LoRA（`c_tachibana_sherry il v1.0 XL`，基于 SDXL base 1.0，1024×1024）|
| 场景 | 雨天街道踩水 / 咖啡厅夜读 / 草坪仰望星空 |

> **注意**：本皮肤与上游**共用界面结构（CSS / hooks 思路），但不共用美术素材** ——
> 上游素材为鲸鱼娘女仆形象（一创 上善 → 二创 zipzip → 三创 Small-tailqwq），
> 本皮肤素材为作者本地生成的橘雪莉形象。

### 相对原版的改动

1. **配色与素材**：改用橘雪莉的蓝发配色与三张场景壁纸；移除原版宫殿背景与女仆立绘
2. **移除装饰**：女仆吉祥物、侧栏四角金饰、上下花边、工作区缎带、左右立绘
3. **顶部重构**：顶栏与右侧栏改为半透明玻璃；顶栏改为单行 + 图标靠右 + 自动折行
4. **壁纸**：改为铺满整屏 + 按时段切换三张场景
5. **清理**：移除旧模板残留的内部标识符（`--maid-*` → `--sherry-*` 等）
6. **修掉的问题**：侧栏开合掉帧（`transform` 绑定每帧变化的 CSS 变量 + 多层矛盾背景规则 + `backdrop-filter`）

---

## 文件结构

```
sherry-atelier/
├── skin.json                 清单（v2）
├── skin.css                  L1 token 重映射
├── patches.css               L3 覆盖层（语义选择器）
├── hooks.mjs                 客户端 hooks
├── LICENSE / NOTICE          原版授权文件
├── ATTRIBUTION/              原版 LICENSE / NOTICE / manifest 副本
├── assets/                   素材（13 个装饰 + 3 张壁纸）
└── preview/                  预览图（light / dark，1400×700）
```

---

## 本地开发说明

本机开发时，皮肤目录内的 `dsh-market.provenance.json` 使用 `localDevelopmentTrust: true`
使 hooks 可在本地运行。**提交到仓库时该文件不应包含**（它由市场安装器在安装时写入）。

## 已知限制

- 依赖 `hooks.mjs`：若在不被信任的目录（无有效 provenance 的用户目录）安装，
  hooks 会被拒绝，玻璃与时段壁纸等效果将失效，仅保留 `skin.css` / `patches.css` 的观感
- 壁纸为夜蓝冷色调，浅色主题下观感以深色为主（本皮肤设计为深色优先）
