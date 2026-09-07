# 手绘拼贴海报 / Handdrawn Poster

一个开源 ChatGPT Skill，用于把单张照片转换为高级 3:4 手绘拼贴海报：

- 上半部分保留真实原图，占画面 50%；
- 下半部分根据原图重构为粉彩蜡笔涂鸦 + 材料拼贴，占画面 50%；
- 强调大面积有意识留白、浅色纸张肌理、少量编辑性文字；
- 每张照片单独输出，不进行多图拼接。

## 调用示例

```text
/handdrawn-poster 用这张图做海报
/handdrawn-poster 用上面提示词，做这张图
/handdrawn-poster 做这张图，不要文字
/handdrawn-poster 批量处理这些照片，每张单独输出
```

## 目录结构

```text
handdrawn-poster/
├── SKILL.md
├── agents/openai.yaml
├── assets/icon.svg
├── references/
│   ├── original-prompt.zh-CN.md
│   └── acceptance-checklist.md
└── scripts/compose_panel.py
```

## 安装

将整个 `handdrawn-poster` 目录打包为 `skill.zip`，然后上传到支持自定义 Skill ZIP 的 ChatGPT Skills 界面。对于基于文件系统的 Skill 环境，将 `handdrawn-poster` 目录放入对应的 Skills 目录即可。

## 说明

`references/original-prompt.zh-CN.md` 是完整中文创作母提示词，也是视觉风格的最高依据。`SKILL.md` 负责定义重复执行流程和验收规则；`scripts/compose_panel.py` 仅用于精确尺寸、50:50 拼接与成图审计，不负责创作视觉内容。

## License

MIT. See `LICENSE`.
