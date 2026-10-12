# Photo to Character · 照片转极简角色插画

可放到 GitHub 保存、下载后在本地重复使用的指令型 Skill。主要面向猫咪和其他宠物：柔和实线勾勒主要轮廓，大面积闭合色块，极简提取特征，便于继续制作表情包和动画原型。

仓库：[Mengyao-L/photo-to-character](https://github.com/Mengyao-L/photo-to-character)。技能入口：[SKILL.md](skills/photo-to-character/SKILL.md)。

本版本根据“优化小猫插画风格”对话中可读取的文字要求重新编写。原照片、手绘稿与旧 Skill 附件未包含在可读取内容中，因此本包没有捏造或附带角色参考图。要更精确复现原画风，请使用时同时提供满意的插画样张。

## 包含内容

```text
photo-to-character/
├── README.md
├── .gitignore
└── skills/
    └── photo-to-character/
        ├── SKILL.md
        ├── agents/openai.yaml
        └── references/
            ├── character-bible.md
            └── animation-assets.md
```

安装的是内层 `skills/photo-to-character` 文件夹。它不依赖本仓库之外的指令文件，且不包含 API 密钥或自动上传逻辑。

## Windows 本地安装

当前机器的已有个人技能位于 `%USERPROFILE%\.codex\skills`。若沿用这个现有环境，在本仓库根目录打开 PowerShell，执行下列代码；如设置了 CODEX_HOME 则优先使用它。遇到同名技能会停止，避免覆盖修改。

```powershell
$skillRoot = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME 'skills' } else { Join-Path $env:USERPROFILE '.codex\skills' }
$skillTarget = Join-Path $skillRoot 'photo-to-character'
if (Test-Path -LiteralPath $skillTarget) { throw "目标已存在，请先比较版本：$skillTarget" }
New-Item -ItemType Directory -Path $skillRoot -Force | Out-Null
Copy-Item -LiteralPath '.\skills\photo-to-character' -Destination $skillTarget -Recurse
```

对于按新版官方目录布局配置的 Codex，可将上面 `$skillRoot` 改为 `Join-Path $env:USERPROFILE '.agents\skills'`。仅在项目使用时，复制到该项目的 `.agents/skills/photo-to-character`。同一环境只选择一个位置，以免重复出现。官方说明：本地技能支持按描述匹配，未出现新技能时可重启 Codex。参见 [OpenAI 技能文档](https://learn.chatgpt.com/docs/build-skills)。

## 使用

上传照片，然后输入：

```text
使用 $photo-to-character，把这张猫咪照片转换为极简平涂插画。
保留趴着看我的动作，柔和实线轮廓，大面积色块，减少毛发细节。
```

复用同一角色：

```text
使用 $photo-to-character。第一张是已认可的角色标准图，第二张是新姿态照片。
沿用第一张的比例、五官、花纹和画风，只从第二张提取动作。
```

制作动作表：

```text
使用 $photo-to-character，以这张标准图生成开心、委屈、疑惑、困困、探头、蹭蹭六个关键姿势。
保持同一角色、线宽和色板，统一画布与留白，便于后续动画制作。
```

跨对话复用时，附上角色档案与已认可的标准图。档案模板在 `references/character-bible.md`；私人素材建议另存于项目的 `private/` 中。

这是生成规范，不是训练好的模型，也不是独立离线转换程序。实际出图需要宿主的图像生成能力；没有图像工具时会提供可复用提示词。文字规范能约束画风，但仍需要视觉参考与检查，不能保证每次像素级一致。单张 PNG 不等于 SVG、可编辑图层或可播放动画。

## 从 GitHub 获取与复用

使用 GitHub 的 Code 菜单下载 ZIP，解压后按上面的本地安装步骤使用。也可克隆仓库：

```text
git clone https://github.com/Mengyao-L/photo-to-character.git
```

也可向支持该能力的 Codex 说明：

```text
使用 $skill-installer，从 https://github.com/Mengyao-L/photo-to-character 安装 skills/photo-to-character。
```

包内不附原照片；`.gitignore` 忽略 private/、work/、outputs/ 和常见密钥文件。若要开放许可供他人分发修改，请选择合适的 LICENSE。

## 验证范围

已提供标准 SKILL.md 元数据、相对路径引用和可移植资源结构。文本与结构检查不代表已完成出图效果测试；后续应以一张实际照片和一张满意的风格参考图进行首轮视觉验收。
