---
title: AI 视频 · 仓库与 Skill 清单（跨机器版）
version: v1.0
date: 2026-11-06
audience: 任何在另一台机器上的 coding agent
scope: 只要链接与介绍，不含任何本地项目路径 / 账号信息
---

# AI 视频 · 仓库与 Skill 清单

> 所有条目都能用三种方式之一装上：`npx skills add <owner>/<repo>`、Claude Code 的 `/plugin marketplace add`、或 `git clone` 到技能目录。
> **代码许可 ≠ 素材许可**，见第 6 节。

---

## 0. 给 agent 的读取指令

```text
这是一份 AI 视频类 Agent Skill / 开源仓库清单，全部是公开 GitHub 链接。

用法：
1. 先读第 1 节的分类表，按用户要做的片型定位 1 个主仓 + 1 个参考仓，不要贪多。
2. 需要细节读第 2 节（作者逐个读过 README 的 15 个仓）。
3. 需要更多候选读第 3 节的索引仓（133 条，含渲染栈与许可）。
4. 安装前先读目标仓的 LICENSE 和 SKILL.md；装法见第 5 节。
5. 输出任何成片前确认：素材可商用、AI 内容已标注、事实有出处。
6. 不要因为某个仓 star 高就假定它质量高；也不要假定 skill 会自动写对代码——先跑 5 秒测试。
```

---

## 1. 分类总表

| 你要做的事 | 主仓 | 备选 |
|---|---|---|
| 一条完整的代码出片产线（Remotion） | [weilanx-claude-videos](https://github.com/Azure12355/weilanx-claude-videos) | [gold-noir-video-creator](https://github.com/cpp285/gold-noir-video-creator) |
| 选视觉风格 / 写风格提示词 | [code-animation-prompts](https://github.com/XiaoyeCodes/code-animation-prompts) | [lemo-opuscar](https://github.com/lemomo-ai/lemo-opuscar) |
| 一句话 → 30 秒产品片 | [huashu-motion](https://github.com/alchaincyf/huashu-motion) | [huashu-art-motion](https://github.com/alchaincyf/huashu-art-motion) |
| 主题 → 1–3 分钟知识讲解 | [knowledge-video](https://github.com/Win-Hao/knowledge-video) | [qianrong-video-skill](https://github.com/yanghui960/qianrong-video-skill) |
| 音乐 MV / 卡点片 | [PDoomVideo](https://github.com/JohnHeibel/PDoomVideo) | [motion-graphics-music-video-skill](https://github.com/makevoid/motion-graphics-music-video-skill) |
| 抄镜头语言 / 补运动设计 | [video-shotcraft](https://github.com/Vincentwei1021/video-shotcraft) | [opus-video-prompts](https://github.com/joeseesun/opus-video-prompts) |
| 找现成模板直接改 | [opus-5-5-video-templates](https://github.com/lumian2015/opus-5-5-video-templates) | [short-video-script-skill](https://github.com/ShortVideo-AI/short-video-script-skill)（只出文案） |
| 剪成片 / 配音 / 字幕 | [video-use](https://github.com/browser-use/video-use) | [claude-video-edit-skill](https://github.com/dreamworker0/claude-video-edit-skill) |
| 看视频、拆视频、复刻动效 | [motion2code](https://github.com/lovisdotio/motion2code) | [video-to-skill](https://github.com/Lum1104/video-to-skill) |
| 想看还有哪些 | [awesome-opus-video-skills](https://github.com/ismoshushi/awesome-opus-video-skills)（133 条） | [awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos)（703 条 prompt） |

---

## 2. 逐个读过的 15 个（细节可信）

### 2.1 产线与工程

| 仓库 | 是什么 | 技术栈 / 规模 | 许可 | 装法 |
|---|---|---|---|---|
| **[weilanx-claude-videos](https://github.com/Azure12355/weilanx-claude-videos)** | 完整 Remotion 视频工程 + 8 个 creator skill（黑金、暗金、灯火史话、战术屏、暖纸、Vox、像素、风格蒸馏）；含 50+ 集成片源码、风格卡、封面与文案脚本 | Remotion + React + SVG；`ep00-demo` 无需外部素材即可跑通 | 见仓库 LICENSE | clone 到任意目录，`npm i` 后 `npx remotion studio` |
| **[gold-noir-video-creator](https://github.com/cpp285/gold-noir-video-creator)** | 暗金 / 黑金风科普片模板：60 秒可跑示例（行星 → 段落 → 收尾），3D 程序化纹理、逐字字幕、信息面板、代码合成配乐；可选 edge-tts 旁白 | Remotion + Three.js；Node 22.18+/24，需要 WebGL 与 ffmpeg | MIT（Remotion 自身另有商业条款） | `git clone` 后放 `~/.claude/skills/gold-noir-video-creator/`；或直接 `cd template && npm ci` |
| **[PDoomVideo](https://github.com/JohnHeibel/PDoomVideo)** | 156.6 秒完整 MV：9 章 62 镜，`STORYBOARD.md` 精确到 0.1 秒；纯函数时间轴（`fn(t, lt, dur)` 只依赖时间），每章一个文件供并行生产 | p5.js 2.3.3 + p5.brush + puppeteer-core；原生 JS，无 React | 代码 ISC；歌曲/图像授权未确认 | 只作方法参考；`render.mjs` 逐帧导出再 ffmpeg 合成 |

### 2.2 风格与提示词

| 仓库 | 是什么 | 规模 | 许可 | 装法 |
|---|---|---|---|---|
| **[code-animation-prompts](https://github.com/XiaoyeCodes/code-animation-prompts)** | 341 种代码动画风格提示词 + 196 张参考静帧 + 离线挑选器，封装成 skill；另带 HTML 逐帧导出 MP4 脚本 | 10 系列：A–G 26 / M 40 / K 38 / Z 15 / H 12 / L 59 / V 15 / X 31 / R 7 / O 98；其中 145 条只有文字参考 | 免费分享，**禁止包装成课程或付费 skill 出售**；Lemo / mg-styles-15 / code-video 三方 MIT | `python scripts/install_skill.py --target codex\|claude`（或手动复制整个 `skills/code-animation-prompts/`） |
| **[lemo-opuscar](https://github.com/lemomo-ai/lemo-opuscar)** | 电影风格图册：每个 `styles/<name>/STYLE.md` 写 11 节（材料、颜色逻辑、运动质感、相机语法、声音调色板…）+ 纯代码样片 | 59 个风格目录、11 类；默认 30–60 秒 / 24fps / −14 LUFS | 代码 MIT，样片 CC BY 4.0 | `/plugin marketplace add lemomo-ai/lemo-opuscar` |
| **[awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos)** | 提示词数据集 + 对照重制画廊，可按技术栈标签筛选 | 703 条 prompt；canvas 267 / svg 183 / threejs 131 / shader 92 / gsap 86；418 条有 live remake | MIT（仅覆盖仓库文本/代码） | 直接查表，不需安装 |
| **[opus-video-prompts](https://github.com/joeseesun/opus-video-prompts)** | 18 份完整提示词 + 54 个公开案例 + 9 条技术路线；含 Playwright 每帧 4 subframe + ffmpeg `tmix` 做运动模糊等工程经验 | 18 / 54 / 9 | 无 LICENSE，只能作方法参考 | 直接读 |

### 2.3 流程型 Skill（装完就能说「做一条 X 视频」）

| 仓库 | 是什么 | 关键设计 | 许可 | 装法 |
|---|---|---|---|---|
| **[huashu-motion](https://github.com/alchaincyf/huashu-motion)** | 一句话 → 商业级产品宣传片：先给 3 个方向 → 写整片 → 自己作曲 → 浏览器编辑器里**指着画面改**（带时间点、元素、源码位置） | 每版留档、⌘Z 撤回；标题/数字/颜色/时长变成输入框 | MIT | `npx skills add alchaincyf/huashu-motion` |
| **[knowledge-video](https://github.com/Win-Hao/knowledge-video)** | 一个主题 → 1–3 分钟知识讲解片：调研 → 逐屏文案（每屏 ≤20 字）→ 免版权配图 → 三种观感 → 卡点分镜 → 先渲开头再渲全片 | 六步默认逐步停给你看；`scripts/beats.py` 测 BPM，`qa.py` 抽帧自查；每条事实必须有源 | MIT | `npx skills add Win-Hao/knowledge-video` 或 `/plugin marketplace add Win-Hao/knowledge-video` |
| **[qianrong-video-skill](https://github.com/yanghui960/qianrong-video-skill)** | 拆书 / 知识阐释短视频流水线，主打**机器可验收**：`audit_video.py` 把「PPT 感」「卡点不准」变成指标（镜头时长、镜头内运动量、拍点偏移毫秒、黑帧、推镜倍率） | 四种模式：15s 信息流广告 / 60s 极简 / 60s 密度流 22 组卡 / 60s 密度流+TTS 17 组；`npx hyperframes check` 必须 0 error | MIT | `git clone ... ~/.agents/skills/qianrong-video-skill` |
| **[opus-5-5-video-templates](https://github.com/lumian2015/opus-5-5-video-templates)** | 30 个复刻自爆款 Opus 5.5 视频的 motion-graphics 模板 + 一个改色改文案就出片的 skill | 全部 HyperFrames（HTML），文案与颜色都是变量；`new-video.mjs` 复制模板，`vars.mjs` 批量改值 | MIT；字体 OFL；GSAP 走 GreenSock 标准许可 | `npx skills add lumian2015/opus-5-5-video-templates` |
| **[short-video-script-skill](https://github.com/ShortVideo-AI/short-video-script-skill)** | 只做文案：8 个标题 + 5 个 3 秒钩子的 prompt 骨架，短句、先冲突后机制、结尾自测 | prompt-only，无渲染 | 见仓库 | 直接读 SKILL.md |
| **[rayskills](https://github.com/imraywang/rayskills)** | 9 个中文 skill：长文、译介、口播母稿、封面、公众号草稿、X 草稿、解说视频（复刻音色 + Whisper 逐字卡点 + 数字人主持） | 有门控：授权没落地就停在本地；发布类动作先停 | **CC BY-NC 4.0（非商业）** | `npx skills add` 或按其 README |

### 2.4 索引与工具

| 仓库 | 是什么 | 规模 | 许可 |
|---|---|---|---|
| **[awesome-opus-video-skills](https://github.com/ismoshushi/awesome-opus-video-skills)** | 只收开源可安装的视频类 skill，每条固定字段：一句话用途 / 渲染栈 / 安装命令 / 许可 / 是否点名 Opus 5.5 | 133 条，四类：用代码出片、产品片与剪辑、看视频转 skill、调外部视频模型 | MIT（只放链接） |
| **[video-use](https://github.com/browser-use/video-use)** | 用编码 agent 剪成片：精剪、字幕、调色、叠加动画 | 27.6k★ | MIT |

---

## 3. 索引仓里值得单独拎出来的（按索引口径，未逐个核 README）

| 仓库 | 一句话 | 星 | 许可 |
|---|---|---:|---|
| [Vincentwei1021/video-shotcraft](https://github.com/Vincentwei1021/video-shotcraft) | Remotion 电影感产品片：152 张镜头配方卡 + 209 个动效预览 + 生产级模板 | 9.9k | Apache-2.0 |
| [Vincentwei1021/mg-styles-15](https://github.com/Vincentwei1021/mg-styles-15) | 15 种 MG 风格，每支约 10 秒，附提示词与源码（非可安装 skill） | 818 | MIT |
| [alchaincyf/huashu-art-motion](https://github.com/alchaincyf/huashu-art-motion) | 美术史题材：35 种可动化艺术风格 + 9 种解说讲法 | 3.9k | MIT |
| [lemomo-ai/lemo-opuscar](https://github.com/lemomo-ai/lemo-opuscar) | 影片风格图册，按风格名生成 | 2.3k | MIT |
| [zenstory-ai/drama-skills](https://github.com/zenstory-ai/drama-skills) | 11 个 skill：AI 短剧全流程（剧本→分镜→提示词→成片） | 2.4k | MIT |
| [0xsline/OpenChatCut](https://github.com/0xsline/OpenChatCut) | 对话式剪辑器：Agent Skills + MCP + Remotion，多轨时间线 | 2.1k | AGPL-3.0 |
| [andyhuo520/digital-human-koubo](https://github.com/andyhuo520/digital-human-koubo) | 一张照片 + 一句话 → 数字人口播视频（文案、对口型、字幕、包装） | 1.6k | MIT |
| [mileson/chaojifeng-video-design](https://github.com/mileson/chaojifeng-video-design) | 视频主线/分镜/声画节奏方法论 + 交付验收 | 481 | MIT（样片 CC BY 4.0） |
| [smixs/visual-skills](https://github.com/smixs/visual-skills) | AI 导演技能：剪辑理论 + Seedance/Kling/Veo 提示词语法 | 455 | CC-BY-4.0 |
| [actionow-ai/vvv](https://github.com/actionow-ai/vvv) | 可复用婚礼视频模板 + 参考片拆解重建 | 499 | MIT（媒体另见 MEDIA_LICENSE） |
| [Barty-Bart/motion-graphics](https://github.com/Barty-Bart/motion-graphics) | 给成片加 motion-graphics B-roll | 338 | MIT |
| [lovisdotio/motion2code](https://github.com/lovisdotio/motion2code) | 把动效视频研究后重建成可编辑代码（内联 SVG + GSAP），逐帧对照源视频校验 | 307 | MIT |
| [Moessif/code-video-showcase](https://github.com/Moessif/code-video-showcase) | 纯代码卡点展示片：逐帧绘制、配乐纯合成、ffmpeg 合成，不调用生成模型 | 230 | MIT |
| [haidrrrry/claude-remotion-skill](https://github.com/haidrrrry/claude-remotion-skill) | 教 Claude 用 Remotion 做动态图形：剪辑、B-roll、字幕、配乐 | 225 | MIT |
| [win4r/video-director](https://github.com/win4r/video-director) | 代码成片的导演 skill：门控流程 + QA | 194 | MIT |
| [imraywang/rayskills](https://github.com/imraywang/rayskills) | 中文内容 + 解说视频全套（见 2.3） | 173 | CC BY-NC 4.0 |
| [makevoid/motion-graphics-music-video-skill](https://github.com/makevoid/motion-graphics-music-video-skill) | 一条音乐 + 一句 prompt → MG MV；需 FAL API key | 69 | MIT |
| [Kianzzz/xilo-opus-video](https://github.com/Kianzzz/xilo-opus-video) | 想法/文章/参考视频 → 多套方案预览 → 成片 | 104 | MIT |
| [howseen-ai/claude-motion-design](https://github.com/howseen-ai/claude-motion-design) | 纯代码动效：确定性 `seek(t)` + 节拍同步 + remake 复刻模式 | 105 | MIT |
| [klsoen/opus-js-animations](https://github.com/klsoen/opus-js-animations) | 导演式：brief → 配音 → 导演阐述 → JS 帧级精确 MP4 | 15 | MIT |
| [browser-use/video-use](https://github.com/browser-use/video-use) | 编码 agent 剪成片 | 27.6k | MIT |
| [Tejashmakwana/motionmaxxing](https://github.com/Tejashmakwana/motionmaxxing) | 把 AI 味重的动态图形修成像人做的 | 76 | Apache-2.0 |
| [iart-ai/motion-design-skills](https://github.com/iart-ai/motion-design-skills) | 运动设计基础（节奏/字体/色彩/构图）+ Remotion 引擎 | 39 | MIT |
| [Newuxtreme/watch-video-skill](https://github.com/Newuxtreme/watch-video-skill) | 教 AI「看」视频：学习、吸收、复刻、视觉反馈 | 70 | MIT |
| [Lum1104/video-to-skill](https://github.com/Lum1104/video-to-skill) | 把视频和课程转成有据可查的 skill | 31 | MIT |
| [tomascupr/reelql](https://github.com/tomascupr/reelql) | 视频链接 → typed JSON（章节/人物/情感弧线/逐字稿） | 28 | MIT |
| [Junhan2/video-lens](https://github.com/Junhan2/video-lens) | 量视频：UI 动画时序与 easing 还原成 CSS（Mac） | 6 | MIT |
| [liangdabiao/whiteboard-teacher-video](https://github.com/liangdabiao/whiteboard-teacher-video) | 讲解稿 → 手绘逐笔讲解视频，五套风格 | 20 | MIT |
| [sirioberati/YouTube-AI-Motion-Graphics](https://github.com/sirioberati/YouTube-AI-Motion-Graphics) | 74 个动画讲解板（图表/示意图），与解说语音同步 | 102 | MIT |
| [GroMarketing/remotion-qa](https://github.com/GroMarketing/remotion-qa) | Remotion 成片 QA：Reels/Shorts 安全区检查 | — | MIT |
| [midudev/better-claude](https://github.com/midudev/better-claude) | Claude Code 插件：图片预览、额度提示、提交体验 | — | 见仓库 |

> 上述描述摘自 [awesome-opus-video-skills](https://github.com/ismoshushi/awesome-opus-video-skills) 的字段（该仓声明逐仓复核过 README 与许可，抓取时间 2026-09-27 ~ 10-07）。**star 是当时的快照**；装之前请自己再看一眼 LICENSE 与最近提交。

---

## 4. 常见技术栈（决定你装完能不能渲染）

| 栈 | 代表仓 | 依赖 |
|---|---|---|
| **Remotion**（React 组件 = 帧） | weilanx-claude-videos、gold-noir、video-shotcraft、claude-remotion-skill | Node 18+、Chrome Headless Shell；商用需看 [Remotion 许可](https://www.remotion.dev/docs/license/pricing) |
| **HyperFrames**（HTML + GSAP → 逐帧） | opus-5-5-video-templates、knowledge-video、qianrong-video-skill | Node 22+、ffmpeg、Chrome；`npx hyperframes doctor` |
| **p5.js / Canvas 逐帧** | PDoomVideo、ClaudeAnimationBase、huashu 系列 | Playwright / puppeteer + ffmpeg |
| **Three.js / WebGL** | gold-noir、cinematic-film | WebGL 可用；渲染参数常需 `--gl=angle` |
| **纯 HTML + `seek(t)`** | claude-motion-design、launch-film、Kimeur 系列 | headless Chrome + ffmpeg，无框架许可负担 |
| **外部生成模型**（图/视频/配音） | makevoid MV、digital-human-koubo、drama-skills | 各家 API key，按量计费 |

---

## 5. 安装方式（三种，按工具选）

```bash
# A. skills CLI（最通用；支持它的仓都能这样装）
npx skills add <owner>/<repo>
npx skills add <owner>/<repo> -g        # 装到用户级

# B. Claude Code 插件市场（仓库自带 .claude-plugin/ 时可用）
/plugin marketplace add <owner>/<repo>
/plugin install <skill-name>@<marketplace-name>

# C. 手动（最稳，能控制放哪）
git clone https://github.com/<owner>/<repo>.git ~/.claude/skills/<skill-name>   # Claude Code
git clone https://github.com/<owner>/<repo>.git ~/.agents/skills/<skill-name>   # Codex / 共享技能目录
```

约定与坑：

1. 技能目录里必须有 `SKILL.md`；带 `agents/openai.yaml` 的通常同时支持 Codex。
2. 有子目录 skill 的仓（如 `skills/<name>/`、`motion-video-kit/business-motion-film`）要复制**那个子目录**，不是仓根。
3. 同一助手不要同时装用户级和项目级同名 skill，会出现重复入口。
4. 装完在**新会话**里才可见；用一句最小请求验证，例如「用 X 风格做一个 5 秒测试片」。
5. 有素材库的 skill（如 code-animation-prompts 约 75 MiB 视频）要整目录复制，只拷 `SKILL.md` 会丢库。

---

## 6. 许可与复用（最容易踩）

| 类型 | 含义 | 处理 |
|---|---|---|
| MIT / Apache-2.0 / ISC | 代码可商用，保留版权声明 | 直接用 |
| CC BY 4.0 | 可商用，必须署名 + 注明改动 | 片尾或简介写来源 |
| CC BY-NC 4.0 | **禁止商业使用**（含商单、广告、带货） | 商用前另行取得许可，否则只做学习 |
| 无 LICENSE | 默认保留所有权利 | 只读方法，不复制代码/素材 |
| 「免费分享」素材包 | 可免费用与转，但禁止打包售卖 / 做成付费课 | 遵守原作者附加条款 |

三条硬规则：

1. **代码许可不覆盖素材**。仓库里的音乐、图片、字体、旁人样片各自有许可，逐项核。
2. **公开可看 ≠ 可下载商用**。别人的成片、BGM、真人人声都要单独授权。
3. **AI 生成内容要标注**（平台有声明项就打开）；真人脸不要用 AI 伪造。

---

## 7. 选型决策树

```text
要不要口播？
├─ 不要 → 要不要卡音乐？
│         ├─ 要 → PDoomVideo（纯函数时间轴） / makevoid MV / code-music-video-skill
│         └─ 不要 → 知识讲解：knowledge-video / qianrong-video-skill / weilanx-claude-videos
└─ 要 → rayskills（复刻音色 + 逐字卡点）/ desk-video 类 skill / digital-human-koubo

是不是产品片？
├─ 是 → huashu-motion（一句话 + 指着改）/ opus-5-5-video-templates（改模板）/ video-shotcraft（152 镜头卡）
└─ 不是 → 风格优先？

风格从哪来？
├─ 已有参考片 → motion2code / video-to-skill / 各家 distill 类 skill
├─ 想挑编号 → code-animation-prompts（341）/ lemo-opuscar（59）/ mg-styles-15（15）
└─ 想抄镜头 → video-shotcraft / opus-video-prompts / awesome-opus5-5-videos

要不要自己写渲染代码？
├─ 要 → Remotion（weilanx / gold-noir / video-shotcraft）
└─ 不要 → HyperFrames（knowledge-video / templates）或整仓 skill（huashu / qianrong）
```

---

## 8. 链接总表（纯列表，便于脚本抓取）

```text
https://github.com/Azure12355/weilanx-claude-videos
https://github.com/XiaoyeCodes/code-animation-prompts
https://github.com/lemomo-ai/lemo-opuscar
https://github.com/yihui-dev/awesome-opus5-5-videos
https://github.com/joeseesun/opus-video-prompts
https://github.com/JohnHeibel/PDoomVideo
https://github.com/JohnHeibel/ClaudeAnimationBase
https://github.com/alchaincyf/huashu-motion
https://github.com/alchaincyf/huashu-art-motion
https://github.com/Win-Hao/knowledge-video
https://github.com/Win-Hao/code-video
https://github.com/cpp285/gold-noir-video-creator
https://github.com/yanghui960/qianrong-video-skill
https://github.com/lumian2015/opus-5-5-video-templates
https://github.com/ShortVideo-AI/short-video-script-skill
https://github.com/imraywang/rayskills
https://github.com/ismoshushi/awesome-opus-video-skills
https://github.com/Vincentwei1021/video-shotcraft
https://github.com/Vincentwei1021/mg-styles-15
https://github.com/browser-use/video-use
https://github.com/0xsline/OpenChatCut
https://github.com/zenstory-ai/drama-skills
https://github.com/andyhuo520/digital-human-koubo
https://github.com/mileson/chaojifeng-video-design
https://github.com/smixs/visual-skills
https://github.com/actionow-ai/vvv
https://github.com/Barty-Bart/motion-graphics
https://github.com/lovisdotio/motion2code
https://github.com/Moessif/code-video-showcase
https://github.com/haidrrrry/claude-remotion-skill
https://github.com/win4r/video-director
https://github.com/makevoid/motion-graphics-music-video-skill
https://github.com/Kianzzz/xilo-opus-video
https://github.com/howseen-ai/claude-motion-design
https://github.com/klsoen/opus-js-animations
https://github.com/Tejashmakwana/motionmaxxing
https://github.com/iart-ai/motion-design-skills
https://github.com/Newuxtreme/watch-video-skill
https://github.com/Lum1104/video-to-skill
https://github.com/tomascupr/reelql
https://github.com/Junhan2/video-lens
https://github.com/liangdabiao/whiteboard-teacher-video
https://github.com/sirioberati/YouTube-AI-Motion-Graphics
https://github.com/GroMarketing/remotion-qa
https://github.com/midudev/better-claude
```

工具与参考：

```text
https://www.remotion.dev/docs/
https://www.remotion.dev/docs/license/pricing
https://github.com/heygen-com/hyperframes
https://github.com/vercel-labs/skills
https://code.claude.com/docs/en/skills
```

---

_清单只做索引与技术判断，不保证任何仓库的稳定性、素材授权或商用合规；star 与目录结构以抓取当日（2026-11-06）为准，安装前请复核目标仓的 LICENSE 与最近提交。_
