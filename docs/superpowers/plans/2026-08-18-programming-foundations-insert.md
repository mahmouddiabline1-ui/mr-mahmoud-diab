# Programming Foundations Insert Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a seven-slide bilingual programming-foundations sequence between Programming Language and `print()`.

**Architecture:** Keep the single-file static site architecture. Add one focused CSS block for the new visual diagrams, seven `<section class="slide">` elements, and one small interaction function for the Syntax slide. Insert the sequence before the current `#s9` slide so the existing Python basics remain in their current order after it.

**Tech Stack:** HTML, CSS, vanilla JavaScript, GitHub Pages.

## Global Constraints

- Modify only `C:\Users\MEGA TECH\Desktop\برمجه تانيه ثانوي\index.html` for the website feature.
- Preserve the existing dark theme, scroll snapping, animations, mobile breakpoint, RTL Arabic layout, carousels, and fixed badge.
- Do not show source links in any student-facing slide.
- Use concise bilingual copy suitable for second-secondary students.
- Keep existing slides and their interactions intact.

---

### Task 1: Add slide-specific presentation styles

**Files:**
- Modify: `C:\Users\MEGA TECH\Desktop\برمجه تانيه ثانوي\index.html` in the final style block before `</head>`

**Interfaces:**
- Produces: CSS classes `program-path`, `comparison-grid`, `level-card`, `tool-card`, `translation-flow`, `syntax-editor`, and `syntax-result`.

- [ ] **Step 1: Add a responsive visual system for the seven slides**

Add CSS for dark bordered cards, language chips, a two-column comparison grid, an RTL translation flow, and a correct/incorrect code panel. Include `@media(max-width:980px)` rules that convert comparison layouts to one column.

- [ ] **Step 2: Check CSS structure**

Run: `rg -n "program-path|comparison-grid|translation-flow|syntax-editor" index.html`

Expected: every class appears in the style block.

- [ ] **Step 3: Commit**

Run: `git add index.html && git commit -m "style: add programming foundations visuals"`

### Task 2: Insert the conceptual programming slides

**Files:**
- Modify: `C:\Users\MEGA TECH\Desktop\برمجه تانيه ثانوي\index.html` immediately before `<section class="slide coding-slide" id="s9">`

**Interfaces:**
- Consumes: CSS classes from Task 1.
- Produces: slides `#prog-compare`, `#language-levels`, `#binary-why`, `#code-where`, and `#ide`.

- [ ] **Step 1: Insert Programming vs Programming Language**

Use two bilingual cards: Programming as planning/writing a solution, and Programming Language as the words and rules used to write it. Include language chips for Python, Java, JavaScript, and C++.

- [ ] **Step 2: Insert High-Level vs Low-Level Languages**

Use side-by-side cards. State that high-level languages are easier for people to read and learn, and low-level languages are closer to the computer. Give Python/Java/JavaScript and Assembly/Machine Language as examples.

- [ ] **Step 3: Insert Why don’t we write 0 and 1?**

Show a short binary string beside the reasons: hard to read, hard to type, and easy to make mistakes. Finish with the idea that programming languages make this easier for people.

- [ ] **Step 4: Insert Where do we write code? and IDE**

Explain that code can be typed in a text editor, but a code editor/IDE is better for programming. Define IDE as a place to write, run, and find code errors; use VS Code and PyCharm as examples.

- [ ] **Step 5: Validate order and IDs**

Run: `rg -n 'id="prog-compare"|id="language-levels"|id="binary-why"|id="code-where"|id="ide"|id="s9"' index.html`

Expected: the five new IDs occur before `s9`, in that order.

- [ ] **Step 6: Commit**

Run: `git add index.html && git commit -m "feat: add programming concepts slides"`

### Task 3: Insert translation and syntax slides

**Files:**
- Modify: `C:\Users\MEGA TECH\Desktop\برمجه تانيه ثانوي\index.html` immediately before `#s9`, after Task 2’s slides

**Interfaces:**
- Consumes: `translation-flow`, `syntax-editor`, and `syntax-result` styles from Task 1.
- Produces: slides `#code-translation` and `#syntax` plus function `checkSyntax(button)`.

- [ ] **Step 1: Insert How the computer understands code**

Use an RTL flow: كتابة الكود → Compiler / Interpreter → لغة الآلة 0 و1 → تنفيذ → النتيجة. Explain that a compiler/interpreter translates programmer-friendly code into a form the computer can execute.

- [ ] **Step 2: Insert Syntax**

Define syntax as the writing rules of a programming language. Show `print("Hello")` as correct and `print("Hello)` as incorrect. Add a “Check the code” button with an initially empty result area.

- [ ] **Step 3: Add the interaction**

Add this function to the existing final script block:

```js
function checkSyntax(button){
  const result=button.closest('.syntax-editor').querySelector('.syntax-result');
  result.textContent='Syntax Error: علامة التنصيص الأخيرة مفقودة. اكتبها هكذا: print("Hello")';
  result.classList.add('show');
}
```

- [ ] **Step 4: Validate markup and JavaScript hook**

Run: `rg -n 'id="code-translation"|id="syntax"|function checkSyntax|onclick="checkSyntax' index.html`

Expected: the two slide IDs and matching function/button hook are present.

- [ ] **Step 5: Commit**

Run: `git add index.html && git commit -m "feat: explain code translation and syntax"`

### Task 4: Verify and publish

**Files:**
- Modify: `C:\Users\MEGA TECH\Desktop\برمجه تانيه ثانوي\index.html` only if verification identifies a structural defect.

**Interfaces:**
- Consumes: all slides and `checkSyntax(button)` from prior tasks.
- Produces: a deployed GitHub Pages update.

- [ ] **Step 1: Validate document structure**

Run: `powershell -NoProfile -Command "$h=Get-Content -Raw index.html; [pscustomobject]@{Sections=([regex]::Matches($h,'<section\\b')).Count;ClosingHtml=$h.Contains('</html>');NewSlides=([regex]::Matches($h,'id=\\\"(prog-compare|language-levels|binary-why|code-where|ide|code-translation|syntax)\\\"')).Count} | Format-List"`

Expected: `ClosingHtml` is `True` and `NewSlides` is `7`.

- [ ] **Step 2: Check changed-file quality**

Run: `git diff --check`

Expected: no output.

- [ ] **Step 3: Run one local visual pass**

Open the page in a local browser and confirm the seven new slides fit on desktop and mobile, the Arabic flow is RTL, and clicking “Check the code” reveals the syntax explanation.

- [ ] **Step 4: Publish**

Run: `git add index.html && git commit -m "feat: complete programming foundations sequence" && git push`

Expected: push completes to `origin/main`; GitHub Pages builds the new commit.

- [ ] **Step 5: Confirm deployment**

Run: `gh run list --repo mahmouddiabline1-ui/mr-mahmoud-diab --limit 1`

Expected: latest `pages build and deployment` run is `completed success`.
