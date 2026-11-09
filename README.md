# Image Prompt Reverse · GPT Image

从参考图反推可直接用于 **GPT Image 系列**的完整生图提示词，支持内容复刻、保留画风替换主体，以及根据实际出图结果修订提示词。具体出图版本按实际使用的平台选择。

本仓库是 [LunarXuan/image-prompt-reverse](https://github.com/LunarXuan/image-prompt-reverse) 的改写分支，基于上游提交 `4dead0a32e2312e56a14ebf3658ee75c9b865055`。aiua-dev 于 **2026-11-09** 调整了主 Skill、通用分析、分类规则、插画规则、界面元数据和本 README；保留上游来源及 GPL-3.0 许可证。

## 与上游默认行为的区别

- 面向 GPT Image 系列，不固定具体模型版本。
- 默认输出一份完整中文提示词；英文按需提供，不固定 450–700 字。
- 保留上游分类分析与插画“内容骨架 / 画风指纹”拆解，取消固定篇幅百分比。
- 必须保留项和必要排除要求整合进同一份成品，不默认另附英文 Negative Prompt。
- 区分仅提示词出图与附参考图出图；默认提示词可以在不附原图时独立使用。
- 文字、Logo 和主体身份按任务保留、替换或移除，不统一模糊化。
- 保留目标画面原有的柔焦、颗粒、暗部、粗糙与低细节，避免自动美化改变风格。
- 不猜测摄影设备、精确参数或 API 字段；不主动调用生图服务。

## 使用

在支持 `SKILL.md` 的客户端安装后，上传参考图并调用：

```text
使用 $image-prompt-reverse 反推这张图，输出可直接用于 GPT Image 的提示词。
```

默认按内容复刻、仅提示词出图处理。也可以说明要替换的主体、必须保留的特征，或最终生图时会一起上传参考图。用户指定语言、字段或输出格式时优先遵循。

这是一套提供给视觉模型的工作指令，不包含独立推理模型、生成服务或 API 凭据。需要宿主模型能读取参考图；最终效果还取决于出图模型与具体设置。仓库目前没有实图效果评测，不承诺找回原始提示词或精确复现。

## 安装

将本仓库放入客户端的技能目录。Codex 的常见个人目录为 `~/.codex/skills/image-prompt-reverse`；已有同名 Skill 时先核对，避免覆盖本地修改。

```sh
git clone https://github.com/aiua-dev/image-prompt-reverse.git ~/.codex/skills/image-prompt-reverse
```

在 Magpie 中，将本仓库作为 GitHub Skill 来源添加到 Library，再选择需要启用的客户端。也可以由 Magpie 管理本地 Git checkout，使用文件夹来源；同一客户端保留一个安装入口即可。

## 文件结构

```text
SKILL.md                         主入口、任务模式与 GPT Image 输出规则
references/analysis-framework.md 通用视觉分析
references/category-guides.md    按主体与媒介选择的专项规则
references/illustration-style.md 插画内容与画风拆解
agents/openai.yaml               Codex 界面元数据
LICENSE                          上游 GPL-3.0 许可证
```

## 维护与许可

本仓库维护 GPT Image 方向的改写；同步上游时需要复核差异，避免恢复上游默认的固定字数、强制双语和独立负面词输出。

GPT Image 的自然语言、参考图角色、文字与保留约束表达参考 [OpenAI 官方 Image prompting 指南](https://developers.openai.com/api/docs/guides/image-prompting)。具体版本、参数支持与效果应在实际使用时核对。

沿用上游的 [GNU GPL v3.0](LICENSE)。这份改写不代表上游作者或 OpenAI 的官方产品或认可。
