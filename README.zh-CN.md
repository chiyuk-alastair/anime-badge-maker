# Anime Badge Maker

简体中文 | [English](README.md)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![Codex Skill](https://img.shields.io/badge/Codex-Agent%20Skill-111827.svg)

一个可长期复用的 Agent Skill：根据动漫人物截图、GK/收藏手办照片或多角度角色参考，生成高质量圆形徽章原画，再把已经通过检查的原画自然放入实体徽章照片中。

本项目固化了一套可执行的视觉标准：人物身份和人体结构高于画面华丽程度。它重点防止常见错误，例如把其他人物的手画到主体身上、改变闭眼状态、虚构饰品、为了塞进圆形而压缩人体，以及把平面圆图直接贴在实体照片上。

## 默认产物

上传参考图并输入：

```text
使用 $anime-badge-maker 按徽章标准制作。
```

默认得到：

1. `01-badge-art.png`：1:1 画布中的圆形动漫徽章原画。
2. `02-badge-mockup.png`：使用同一张已批准原画制作的实体徽章效果图。

也可以只执行一个阶段：

- “只要原画”：只生成徽章原画。
- “把这个图案换进徽章”：只替换实体徽章印刷面，不重新设计角色。

## 主要能力

- 自动判断上传图片是人物参考、完成的徽章图案还是实体徽章照片。
- 按正面、侧面、全身、手部和配件等信息分配多张参考图的作用。
- 生成前建立主体归属关系，避免把背景人物的肢体或道具错误归给主体。
- 保留发型、眼睛状态、表情、面部标记、服装、饰品、动作和体型。
- 全身构图会损害比例时，自动优先使用胸像或半身。
- 让背景适合圆形裁切，同时不遮脸、不抢主体。
- 实体合成时保留金属包边、曲面、透视、反光、高光、阴影和摄影纹理。
- 使用硬性质量门检查，并针对具体错误修正，而不是接受明显缺陷。
- 支持根据 description 自动触发，也支持 `$anime-badge-maker` 显式调用。

## 使用条件

- Codex、ChatGPT 桌面应用或其他兼容 Agent Skills 的宿主。
- 宿主具备图片生成和图片编辑能力。
- 生成原画时至少提供一张人物参考图。
- 实体徽章照片可选；未提供时使用项目内置的空白徽章照片。

Skill 本身不要求 API Key、Python 包或命令行依赖。图片能力和使用额度取决于实际宿主。

## 安装

### 使用 Codex Skill Installer

在 Codex 中输入：

```text
$skill-installer 请从 https://github.com/chiyuk-alastair/anime-badge-maker/tree/main/skills/anime-badge-maker 安装这个 Skill。
```

如果安装后没有立即显示，请重启 Codex。

### 手动安装

克隆仓库：

```bash
git clone https://github.com/chiyuk-alastair/anime-badge-maker.git
```

把 `skills/anime-badge-maker` 整个文件夹复制到用户级 Skills 目录。当前 Codex 官方文档列出的目录是：

```text
$HOME/.agents/skills/anime-badge-maker
```

部分 Codex 版本或自定义环境会使用 `$CODEX_HOME/skills`，通常是 `$HOME/.codex/skills`。请以当前宿主已经能够识别的目录为准。

### 仅供某个项目使用

复制到目标项目：

```text
你的项目/.agents/skills/anime-badge-maker
```

## 使用示例

### 默认生成两张图

上传一张或多张人物/手办参考：

```text
按徽章标准制作。
```

### 只生成原画

```text
使用 $anime-badge-maker，只要圆形徽章原画。
```

### 只做实体换图

同时上传完成的圆形图案和实体徽章照片：

```text
使用 $anime-badge-maker，把这个图案换进实体徽章，只替换印刷区域。
```

### 使用自己的实体徽章照片

同时上传人物参考和实体照片：

```text
先制作徽章原画，通过检查后再放进我上传的实体徽章照片。
```

## 判断优先级

Skill 按以下顺序决定结果是否合格：

1. 人物身份准确。
2. 人体结构及肢体归属正确。
3. 表情、眼睛状态、服装、饰品和关键动作得到保留。
4. 圆形构图自然，人物足够突出。
5. 背景氛围和装饰完成度。

即使画面很华丽，只要人物被改错、手脚畸形或出现外来肢体，就必须判定为不合格。

## 实体徽章合成原则

实体阶段不重新解释角色，而是把通过检查的原画作为唯一图案，仅进行适应实物表面的必要变化：

- 曲面和透视；
- 可印刷边界裁切；
- 曝光、颗粒和色温匹配；
- 覆盖在图案之上的真实高光与反射；
- 金属包边产生的自然遮挡。

最终效果应像真实生产并拍摄的徽章，而不是后期覆盖的圆形贴图。

## 印刷说明

默认产物是高分辨率视觉稿和商品预览，不自动等同于生产级印刷文件。用于制造时，请提供印厂的直径、出血、安全区、分辨率和色彩配置要求。

## 隐私、版权与合理使用

- 只上传或传播你有权使用的参考素材。
- 不把原图中的水印、卖家账号、工作室标志或平台界面复制到生成结果。
- 公开仓库未包含私人开发阶段使用的动漫原图和人物生成案例。
- 内置空白实体徽章照片专为本次开源发布生成，不含人物、商标或文字。
- 用户需要自行负责所处理角色和参考资料的相关权利。

## 仓库结构

```text
anime-badge-maker/
├── README.md
├── README.zh-CN.md
├── LICENSE
├── CONTRIBUTING.md
├── CHANGELOG.md
└── skills/
    └── anime-badge-maker/
        ├── SKILL.md
        ├── README.md
        ├── quality-checklist.md
        ├── agents/openai.yaml
        ├── assets/default-blank-badge.png
        └── references/
            ├── README.md
            └── design-rationale.md
```

## 参与贡献

欢迎提交 Issue 和 Pull Request。最有价值的问题报告会说明：输入图片各自的作用、预期保持的特征、实际失败表现，以及错误出现在原画阶段还是实体合成阶段。详见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 开源协议

采用 [MIT License](LICENSE)。

## 参考

本项目使用 Codex 支持的开放 Agent Skills 目录结构。参见 [OpenAI 官方 Skill 文档](https://learn.chatgpt.com/zh-Hans/docs/build-skills)。

