# motion-vocab ｜ 动效词汇台

![motion-vocab](screenshots/header.jpg)

**把说不出口的动效，拆成一个词。**

你跟 AI 说“高级一点、柔和一点、有科技感”，它给你灰底圆角卡、同款阴影、匀速淡入；你说“遮罩停点 24%→58%、1.1s `cubic-bezier(.4,0,.2,1)`、`scale 1→1.08`、`opacity .75`”，它一次就对。

**形容词没有落点，名词自带参数。** 这个 Skill 做的，就是把那些你叫不出名字的效果，拆成有名字、有参数、有边界的词，再立成一册能照着抄的词汇册。

> MIT 许可 · 可以用、可以改、可以商用 · 保留版权声明即可

## 30 秒装上

```bash
git clone https://github.com/AlphEJ/motion-vocab.git
```

**Claude Code**

```bash
mkdir -p ~/.claude/skills && cp -r motion-vocab ~/.claude/skills/motion-vocab
```

**Codex / 其他支持 skills 的 agent**

```bash
mkdir -p ~/.codex/skills && cp -r motion-vocab ~/.codex/skills/motion-vocab
```

装好后直接说一句：

```
用 motion-vocab 拆 https://example.com，再立一册
```

详细安装、验收与排错见 [`docs/INSTALL.md`](docs/INSTALL.md)。

## 它解决什么

| 你说的 | AI 听到的 | 结果 |
|---|---|---|
| “高级一点、丝滑一点、有科技感” | 没有可匹配的对象，只能猜成最常见的样式 | 灰底圆角卡、均匀阴影、匀速淡入——也就是常说的“AI 味” |
| “收边 1.1s、`cubic-bezier(.4,0,.2,1)`、停点 24%→58%、`scale 1→1.08`” | 一整套现成的参数与曲线 | 一次就能对上 |

你要的那句“再柔一点”，本质是把某个参数挪一格。**能叫出名字，才改得动。**

## 五个入口

| 入口 | 你给它 | 它给你 |
|---|---|---|
| **A 拆解** | 一个项目 / 站点 / 视频 | 六栏拆解稿：来源与许可、骨架分层、模块全量清单、动效清单、视觉风格、可搬元素。每条形效都标 `实测 文件:行` 或 `估`，不混着写 |
| **B 领域** | 一个主题（滚动驱动 / 纵深 / 版式…） | 横评稿：≥5 个可核来源、≥2 个真分歧点、≥1 个当场跑通；凑不齐**不立册**，只进待验清单 |
| **A′ 立册** | 拆解稿或横评稿 | 十节册 html：12 张术语卡、四条边界、速查表、可复制提示词、可拖动的读数和自检 |
| **C 设计** | 一句需求（做个简历站 / 落地页 / 看板） | 按词库给出动效方案，产出能跑的页面 |
| **查词** | “这个效果叫什么” | 词名 + 参数锚点 + 用错的例子 |

## 仓库里有什么

| 位置 | 内容 |
|---|---|
| `SKILL.md` | 主入口：五个入口怎么走、硬规格、验收口径、署名规则 |
| `references/` | `teardown`（六栏）· `booklet`（十节骨架与视觉配方）· `words`（查重与参数锚点）· `intent`（需求判读）· `survey`（横评七段）· `sources`（21 条来源与许可） |
| `scripts/` | 六个校验：结构、JS 语法、样式纪律、窄屏溢出、隐私扫描、一键跑全 |
| `assets/` | 两册**随包分发**的样例（03 起步骨架 / 12 拆解全规格） |
| `booklets/` | 仓库附带的 2 册成品 |
| `docs/INSTALL.md` | 安装、验收、排错 |

## 验收

```bash
# 十节册（12）——完整规格
python scripts/run_all.py "booklets/12-路径与轨道词汇册.html" --section 10 --deny-file "scripts/deny-sample.txt"

# 起步骨架（03）——只有 3 个 section，--section 必须给 3
python scripts/run_all.py "booklets/03-版式与组件词汇册.html" --section 3 --deny-file "scripts/deny-sample.txt" --target-dir "booklets"
```

两册都是 **5/5**。注意 `--section` 要跟册子的真实节数对齐：拿 `--section 10` 去跑只有 3 节的 03，结构项必然 FAIL——那是口径错，不是册子坏。

五项通过 = 结构 / JS 语法 / 样式纪律 / 窄屏不溢出 / 隐私扫描。缺 `playwright` 时溢出项会打印 `SKIP` 并返回退出码 3，**SKIP 不算通过**。

`booklets/03` 与 `assets/样例-03` 是**同一份文件的副本**（字节相同），一个是给读者打开看的，一个是给 Skill 内部引用的。

## 只带两册

`booklets/` 里只有 **03 与 12** 两册，其余 14 册（01–02、04–11、13–16）不随仓库分发。

`SKILL.md` 与 `references/words.md` 里的编号 1–16 是作者本地册库的号；在本仓库里查不到对应的册，就按“索引里没有”处理，**不要编**。完整册目见 [`booklets/索引.md`](booklets/索引.md)。

## 许可

[MIT](LICENSE)。

- **可以**：下载、阅读、修改、二次分发，**也可以商用**——做课程、做付费工具、给客户交付都行。
- **唯一要求**：保留版权声明与本许可文本。
- 想合作或想署名也可以找我：抖音 / 小红书 / 微信公众号 **@Alpha_领域**。

## 作者

- 抖音：[@Alpha_领域](https://www.douyin.com/)
- 小红书：@Alpha_领域
- 微信公众号：@Alpha_领域

用本 Skill 做出的产出物（册子、页面、拆解稿）**不带这些 ID**，只有本仓库与这条 README 署名——产出的东西是给用的人署名的，不是给我打广告的。

