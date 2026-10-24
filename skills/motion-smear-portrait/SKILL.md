---
name: motion-smear-portrait
description: Preserve the real identity and original pixels of portrait photos while applying tasteful cinematic slow-shutter motion-smear, background removal/replacement, and optional conservative geometric correction. Use for 撕拉感、慢门拖影、人物消散、纯色背景、保留原脸 photography edits.
---

# Motion Smear Portrait / 慢门撕拉人像

## Mission
Deliver edits that look like imperfect in-camera long exposure rather than digital speed lines. Preserve the original individual's identity and facial features. Use pixel-preserving image processing for identity-critical edits; do not claim generative redraw is exact identity preservation.

## Inputs
- Mandatory: original full-resolution photograph.
- Optional: style reference, output aspect ratio, background preference, requested blur strength.
- Preserve objects held in hands, clothing, glasses, hair, pose, and accessories as part of the subject.
- When multiple photos are provided, make independent deliverables for each distinct photo; do not replace individual outputs with a collage.

## Hard constraints
1. Never substitute a generated/lookalike face for the original. Avoid face synthesis, beauty retouching, automatic facial reshaping, and face-swapping.
2. Never use a previously generated image as the source of facial identity when the original is available.
3. Avoid uniform face compression, eye enlargement, nose reshaping, or speculative anatomy reconstruction.
4. Do not claim physically exact camera correction without calibration/focal length/depth data.
5. Do not remove hands, carried items, glasses, or parts of the pose while isolating the subject.
6. Background must stay visually flat or subtly textured when the user asks for a plain background. No invented scenery.

## Workflow
### Step 1: Source integrity
- Load and retain the original image. Check orientation, pixel dimensions, EXIF (if present), and framing.
- Save an untouched copy; create working copies separately.
- If selfie taken close to iPhone front camera: explain that close-range perspective exaggeration may dominate residual optical distortion. Do not arbitrarily squeeze the face. A single 2D selfie does not uniquely determine the actual 3D face.

### Step 2: Optional geometric correction (only when requested)
- Prefer calibrated lens undistortion if actual calibration is available.
- Otherwise use conservative, reversible projections and show side-by-side before/after.
- Do not treat changing width as equivalent to undoing perspective; leave the face alone rather than introduce visible warping.
- Keep non-target people and background fixed where possible, and label corrections as approximate.

### Step 3: Segmentation & compositing
- Create a refined subject matte that includes the full silhouette, hair, glasses, clothes, all limbs, and held items.
- Feather the matte slightly and check for halos, missing fingers, signs, background remnants, and disconnected fragments.
- Composite on a solid muted cool slate-blue/gray background by default (for example #334456 or #3E4B5A); use unpatterned tones, not gradients with visible banding, unless requested.
- Compose the subject toward one side with ample negative space while preserving useful body framing.

### Step 4: Pixel-based motion smear
- Retain an underlying readable core image sourced from original pixels.
- Create multiple low-opacity shifted layers at varying distances (for example 3–35 px at a 1500 px image height), with nonuniform weights and lengths.
- Apply soft directional motion blur to selected duplicate layers and edges, with slight irregular vertical variance. Avoid evenly spaced parallel lines across the whole image.
- Concentrate the strongest smear around hair, shoulders, outer sleeves, garment boundaries, and motion extremities; use less on facial core.
- On the face, apply delicate local drag to hairline, temple, glasses edge, brow, cheek edges, while keeping eyes/nose/mouth generally recognizable; if user wants stronger facial motion, gradually increase blur in small steps without face reconstruction.
- Use subtle warm highlights only where plausible. Avoid neon halos, flames, glossy CGI, excessive orange rims, and invented streaks across empty background.

### Step 5: Quality-control checklist
- Is this demonstrably the same face from the actual original pixels?
- Are facial features aligned and readable enough to meet the user's requested intensity?
- Are glasses, hands, bags, poles, clothing and pose preserved?
- Are all background edges clean?
- Does movement look organic rather than like speed-lines or a glitch filter?
- Is the scene subdued, cinematic, and minimally composed?
- Are all edits localized and reversible?
If any answer is no, fix before delivery. If a source defect cannot be corrected without invented pixels, state this limitation.

### Step 6: Output and review
- Export full-resolution PNG for each image, plus optionally a compact JPEG preview.
- Show the image inline, not solely as a ZIP; provide standalone verified file links if available.
- Provide a tight original-vs-edited comparison when geometric correction or fidelity is questioned.
- For batches, name outputs by original filename, and create a ZIP only in addition to individually accessible images.

## Default aesthetic
- Emotion: distant, quiet, fleeting, cinematic; the person feels momentarily dissolving but remains recognizable.
- Backdrop: muted cool gray-blue, low saturation, ample negative space.
- Motion: soft asymmetric horizontal/diagonal slow-shutter movement, moderate on body, subtle on face.
- Lighting: restrained natural warm-cool contrast.
- Never default to a completely obliterated face or a stylized newly generated face.

## Strength presets
- `subtle`: face micro-smear, 1–2 soft trailing layers; highly recognizable.
- `balanced` (default): noticeable edge/body smear, small facial drift, recognizable eyes/nose/mouth.
- `expressive`: more substantial body and face fragmentation, but still original pixels, no anatomy redraw.

## Useful response for uncalibrated selfie correction
"原片可能存在近距离透视夸张；没有镜头标定和深度数据，无法精确还原真实三维比例。我可以做保守、可回退的原像素几何调整，但不会以瘦脸代替畸变矫正，也不会重新生成五官。"
