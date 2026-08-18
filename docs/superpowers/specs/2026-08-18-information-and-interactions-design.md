# Information and Interactions Update

## Goal

Make the opening ICT concepts clearer for students, remove the ASCII & Unicode slide, and add concise interactive examples to the remaining early concept slides.

## Changes

1. Remove the `#s4` ASCII & Unicode slide entirely and renumber subsequent numbered ICT slides to close the gap.
2. Rework `#s1` as **Information & Digital Data / المعلومات والبيانات الرقمية**. It will separately define information (meaningful words, pictures, and sounds) and digital data (the computer-readable form used for storage and processing), then offer three buttons—word, picture, sound—that demonstrate conversion to binary-like data.
3. Update `#s2` Binary so it automatically alternates every 1.2 seconds between `0 — OFF` and `1 — ON`; the text and visual color change together.
4. Add a character selector to `#s3` Character Encoding. Selecting English `A`, Arabic `م`, or emoji `😀` updates the displayed character and its numerical/code-point representation.
5. Extend `#s5` Hexadecimal with color buttons that update both a swatch and its matching hexadecimal color code.
6. Extend `#s6` Algorithm with a step-through control that highlights one everyday tea-making step at a time.

## Constraints

- Preserve the current bilingual, dark, RTL-ready style and existing interactions.
- Keep the explanations appropriate for second-secondary students.
- Do not add source links or external dependencies.
- Retain local images and existing GitHub Pages behavior.

## Verification

Check slide removal and numbering, JavaScript syntax, each interaction’s DOM hook, local page structure, and a successful GitHub Pages build after publishing.
