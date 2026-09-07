# Acceptance checklist

Check every output before delivery.

## Structure

- Portrait 3:4 canvas.
- Exactly two regions only.
- Top and bottom are exactly 50:50 in height.
- No header, footer, third band, inset card, contact sheet, or multi-photo collage.

## Top region

- Uses only the current source photograph.
- Subject identity, structure, pose, and relationship remain recognizable and unchanged.
- Natural light and original atmosphere remain intact.
- Only restrained editorial color refinement is acceptable.
- No stretching or geometric distortion.

## Bottom region

- Clearly corresponds to the current source at first glance.
- Reinterprets rather than fully copies the source.
- Uses a small-scale stamp-like main subject and large intentional whitespace.
- Shows coarse pastel/chalk/crayon linework with dry grain and slight hand-drawn imperfection.
- Uses restrained paper/material collage, not decorative clutter.
- Uses only a few supporting doodle symbols.
- Background remains clean paper with visible but subtle fiber/grain.
- Source-derived 2–4 color palette remains warm, clear, and readable.
- Avoids photorealistic rendering, glossy vector art, 3D, children’s-template styling, commercial-ad styling, or dense decoration.

## Text

- Text is sparse and source-grounded.
- No fixed slogan unrelated to the source.
- No accidental carryover from a previous poster.
- No obvious pseudo-text when the user requested no text.

## Final audit

If the split is visually uncertain, run:

```bash
python3 scripts/compose_panel.py --audit final.png
```

Regenerate or deterministically compose again when the split or source preservation is clearly wrong.
