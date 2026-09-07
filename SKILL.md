---
name: handdrawn-poster
description: 'Turn each user-supplied photo into an independent premium 3:4 hand-drawn collage poster with exactly two equal 50:50 regions: the preserved real photo above and a source-grounded pastel-crayon doodle and material-collage reinterpretation below. Use when the user invokes /handdrawn-poster or asks for 手绘海报, 手绘拼贴海报, 粉彩蜡笔涂鸦海报, 上实下绘海报, 用上面提示词做这张图, or batch processing where every photo must be output separately.'
---

# 手绘拼贴海报

Create one finished hand-drawn collage poster for each current user-supplied source photo. Treat `references/original-prompt.zh-CN.md` as the sole creative and aesthetic authority. Read it completely immediately before every generation.

## Core contract

- Output one source photo per poster. Never combine different source photos.
- Default canvas: portrait `3:4`.
- Use exactly two regions: reality on top and design below.
- Make the two regions exactly `50:50` in height. Never add a header, footer, third band, inset panel, grid, or contact sheet.
- Preserve the current source identity, subject relationships, structure, pose, natural light, and original atmosphere in the top region. Do not invent a different person, landmark, building, or scene.
- Reinterpret the same source in the lower region. Do not reuse subjects or wording from earlier images in the conversation.
- Keep the lower design sparse and editorial: small-scale visual stamp, generous intentional whitespace, pale paper ground, coarse pastel/crayon contours, restrained material collage, and only a few supporting doodle symbols.
- Create fresh artwork from the current original source. Never feed a previous hand-drawn poster result back as the source for a new transformation.

## Default behavior

When the user simply says “用上面提示词，做这张图” or invokes `/handdrawn-poster` with one image:

1. Use the current uploaded image as the only source.
2. Use `3:4`, top-bottom, exact `50:50` split.
3. Use sparse source-grounded editorial text only if text naturally improves the lower layout; otherwise keep text minimal.
4. Prefer Chinese or light Chinese-English mixing when the conversation is Chinese. Do not force a fixed slogan.
5. Generate immediately without asking setup questions unless a necessary requirement is genuinely ambiguous.

If the user explicitly asks for no text, output no text, pseudo-text, labels, logos, or decorative letters in the lower design.

## Generation workflow

### 1. Analyze only the current source

Identify the source's most memorable:

- core subject;
- subject relationship;
- structural direction or silhouette;
- mood and light;
- visual metaphor;
- 2–4 representative colors.

Do not write a long analysis to the user before generation unless they ask for it.

### 2. Read the canonical brief

Read `references/original-prompt.zh-CN.md` in full immediately before the image-generation call. Do not summarize or replace it with a shorter house style.

### 3. Generate

Use the available image-generation/editing route with the current source photo attached as the reference.

Prefer a single complete-canvas generation when it can reliably preserve the source and the exact two-region structure.

If exact split or source preservation is unreliable, generate the lower design separately and use `scripts/compose_panel.py` for deterministic final composition. The script may be used for exact sizing, 50:50 composition, or read-only auditing; never use it to invent the artwork.

### 4. Text behavior

Use only a small amount of source-grounded copy. Derive it from the image's place, memory, relationship, action, atmosphere, or visual metaphor.

- Keep copy quiet and editorial, not advertising-like.
- Avoid fixed title templates.
- Avoid slogans unrelated to the current source.
- Do not copy wording from a previous poster.
- If a source contains meaningful visible text or a landmark inscription, preserve its semantic identity; do not replace it with unrelated text.

### 5. Inspect before delivery

Use `references/acceptance-checklist.md` to verify the final result. Reject or regenerate obvious failures such as a third band, dense lower-half decoration, dark dirty paper, unrelated subjects, over-rendered realism in the lower half, or a non-50:50 split.

## Batch behavior

For multiple uploaded photos or an image directory:

- Treat the request as explicit batch intent.
- Process each source independently in stable order.
- Produce one isolated poster per source.
- Do not create an automatic collage or contact sheet.
- Re-run the source analysis for every image. Do not let the previous image's subject, palette, copy, or composition contaminate the next one.

## Deterministic composition helper

Use `scripts/compose_panel.py` only when exact raster composition is needed.

Examples:

```bash
python3 scripts/compose_panel.py --layout top-bottom --source original.png --design lower.png --canvas 3:4 --width 1536 --out final.png
python3 scripts/compose_panel.py --audit final.png
```

The canonical creative brief always outranks helper defaults.
