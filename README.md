# Claude RTL Writing Rules — Hebrew & Arabic

A set of rules that makes Claude and `Claude Code` write Hebrew and Arabic that display correctly right-to-left (RTL): no mixing with English, no reversed equations.

**Engineering & Development:** Ashraf Saed | MIGATRONIX – Automation & Control Solutions

---

## The problem

When you write to Claude in Hebrew or Arabic, the answer is sometimes displayed scrambled:

- A paragraph that starts with an English word, a number or a tag such as `[FACT]` is displayed entirely left-to-right.
- An equation inside a Hebrew/Arabic sentence is displayed reversed. The correct calculation:

```
3600 / 12 = 300
```

is displayed inside a Hebrew sentence as:

```
300 = 12 / 3600
```

**Why:** apps and browsers decide the direction of each paragraph from its first strong character (the Unicode Bidirectional Algorithm). The text Claude writes is correct; only its display is scrambled. These rules teach Claude to write in a way the display will lay out correctly.

---

## The rules

1. Every paragraph, list item, heading and table cell starts with a Hebrew/Arabic word — never with an English word, number, file name, command or symbol.
2. English terms, file names, commands and code fragments go inside backticks.
3. Code and multi-line English content go in a separate code block.
4. Equations and calculations always go on their own line inside a code block.
5. In tables, the first column holds the Hebrew/Arabic text.
6. Hebrew and Arabic are not mixed in the same paragraph.
7. Characters are never reversed to simulate RTL.
8. Status tags are written in the answer's language:

| English | Hebrew | Arabic |
|---|---|---|
| `[FACT]` | עובדה | حقيقة |
| `[DERIVED]` | נגזר | مشتق |
| `[ASSUMPTION]` | הנחה | افتراض |
| `[ESTIMATE]` | הערכה | تقدير |
| `[RISK]` | סיכון | خطر |
| `[REQUIRES DATA]` | נדרש מידע | يتطلب بيانات |
| `[OPEN QUESTION]` | שאלה פתוחה | سؤال مفتوح |

---

## What's in the package

| File | Purpose |
|---|---|
| `memory/rtl-rules.txt` | Text to paste into a Claude chat so the rules are saved to Claude's memory |
| `output-styles/rtl-hebrew-arabic.md` | Output Style file for `Claude Code` installed on your computer |
| `test/test-prompt.txt` | A Hebrew test prompt to verify the rules work |
| `CHANGELOG.md` | Versions and changes |
| `LICENSE` | Terms of use |

---

## Installation — Option A: Claude app and cloud sessions (recommended)

Works in the Claude desktop and mobile apps, on `claude.ai`, and in `Claude Code` cloud sessions.

1. Open a new chat in Claude.
2. Open `memory/rtl-rules.txt` and copy all of its text.
3. Paste it into the message box and press Enter.
4. Wait for Claude to confirm the rules were saved.
5. Verify: open **Settings → Memory → Preferences** and scroll to the end of the list. The rules should appear there.

**Note:** Output Styles are not available in `Claude Code` cloud sessions, so in the cloud use this option only.

---

## Installation — Option B: `Claude Code` installed on your computer

### Windows

1. Open PowerShell.
2. Create the folder:

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\output-styles"
```

3. Copy `output-styles/rtl-hebrew-arabic.md` into:

```
C:\Users\<USERNAME>\.claude\output-styles\
```

### macOS / Linux

From the package folder, run:

```bash
mkdir -p ~/.claude/output-styles
cp output-styles/rtl-hebrew-arabic.md ~/.claude/output-styles/
```

### Activate

1. Close and reopen `Claude Code`.
2. In the `Claude Code` message box, type the following and press Enter:

```
/output-style RTL Hebrew Arabic
```

---

## Testing

1. Open a new chat.
2. Copy the content of `test/test-prompt.txt`, paste it into the message box and press Enter.
3. Check the answer:

| Check | Correct when |
|---|---|
| Line starts | Every line, heading and list item starts with a Hebrew word |
| English terms | Terms such as `CAPEX` and `OPEX` appear inside a grey code box |
| Calculation | The calculation is in a separate block and reads left-to-right |
| Table | The right-most (first) column is in Hebrew |
| Arabic | The Arabic summary sentence is in its own paragraph |
| Tags | Tags appear in Hebrew (e.g. הנחה, סיכון), not `[FACT]` |

The calculation in the answer should look like this:

```
Payback = 450,000 / 180,000 = 2.5 years
```

---

## Updating the rules

When you find a new display problem:

1. **Document** — take a screenshot of the scrambled spot.
2. **Phrase a rule** — write a new rule in English, one clear sentence.
3. **Update the files** — add the rule to both `memory/rtl-rules.txt` and `output-styles/rtl-hebrew-arabic.md`.
4. **Changelog** — add an entry to `CHANGELOG.md` with a new version number, date and description.
5. **Update memory** — paste the new rule into a Claude chat and ask Claude to save it to memory permanently. Then verify it appears under **Settings → Memory → Preferences**.
6. **Update your computer** — if you use Option B, copy the updated file again into `.claude/output-styles`.
7. **Re-test** — run the test prompt again.

---

## Limitations

- **Writing only:** the rules change how Claude writes, not how the screen displays text.
- **Terminals without bidi support:** terminals that do not implement bidirectional text (for example Windows Terminal or the VS Code integrated terminal) may still show mixed text. Use the Claude app or the VS Code chat panel instead.

---

## Copyright

© 2026 Ashraf Saed | MIGATRONIX – Automation & Control Solutions. All rights reserved.

See `LICENSE` for full terms.
