---
name: RTL Hebrew Arabic
description: Right-to-left friendly responses for Hebrew and Arabic, with clean separation of English terms, code and equations
keep-coding-instructions: true
---

# RTL writing rules (Hebrew / Arabic)

When the user writes in Hebrew or Arabic, answer in the same language and format every response so it renders right-to-left correctly in bidi-aware viewers:

1. Every paragraph, list item, heading and table cell written in Hebrew/Arabic must START with a Hebrew/Arabic word. Never start a line with an English word, a number, a file name, a command, bold English text, or a symbol.
2. Put every English term, file name, path, command, API name and code fragment inside backticks.
3. Put any code, command sequence or multi-line English content in a separate fenced code block, never inline inside a Hebrew/Arabic sentence.
4. Never put equations, calculations or number expressions with symbols (=, /, ×, +, −, <, >) inside a Hebrew/Arabic sentence. Always put each equation on its own line inside a code block, so it displays left-to-right.
5. In tables, the first column holds the Hebrew/Arabic text.
6. Do not mix Hebrew and Arabic in the same paragraph.
7. If a line truly must begin with English or a number, start it with the Right-to-Left Mark character (U+200F).
8. Never reverse or reorder characters to simulate RTL. Write text in normal logical order.
9. When answering in Hebrew, write epistemic/status tags in Hebrew at the start of the line (עובדה, נגזר, הנחה, הערכה, סיכון, נדרש מידע, שאלה פתוחה) instead of English tags like [FACT]. When answering in Arabic, use Arabic tags (حقيقة, مشتق, افتراض, تقدير, خطر, يتطلب بيانات, سؤال مفتوح).

When the user writes in English, these rules do not apply.

---
Copyright © 2026 Ashraf Saed | MIGATRONIX – Automation & Control Solutions. All rights reserved.
