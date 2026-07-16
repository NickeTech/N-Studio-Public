# Prompt Specification for Translation Agent

## 1. Task
Translate provided XAML string resources into multiple languages while preserving formatting rules, language ordering, and parent‑language inheritance behavior.

---

## 2. Output Format Requirements

### A. Separate code blocks by language
Each language must be output in its own code block, preceded by a language header, for example:

### Danish — da  
    ```xml
        <s:String ...>...</s:String>
    ```

### B. Preserve indentation
Indentation must match the original snippet exactly:

    <s:String x:Key="...">...</s:String>

### C. Preserve comments
The original comment must be included exactly as provided, with no added spaces:

    <!--Error • Missing drive-->

### D. Commenting rules
Languages that inherit from a parent must have their XAML entries commented out, with no spaces inside the comment tag:

Correct:

    <!--<s:String x:Key="...">Text</s:String>-->

Incorrect:

    <!-- <s:Stringg x:Key="...">Text</s:String> -->  (spaces before/after)

Additionally:

If a translation matches the English‑US source, it must be commented out because all languages ultimately inherit from English‑US.

---

## 3. Parent–Child Language Inheritance Rules

### Root language:
- English‑US (`en`)

### Inheritance chain:
- `pt` (Brazil) inherits from `en`
- `pt-PT` inherits from `pt` (Brazil)
- `en-GB` inherits from `en`
- `es-AR` inherits from `es`

### Commenting rule:
A language must be commented out if:
1. Its translation matches its parent language, OR  
2. Its translation matches the English‑US source.

---

## 4. Required Language Order

The agent must output languages in exactly this order:

1. da  
2. de  
3. el  
4. en-GB  
5. es  
6. es-AR  
7. fr  
8. ia  
9. it  
10. ja  
11. nl  
12. pt (Brazil)  
13. pt-PT  
14. ru  
15. sv  
16. zh-Hans  
17. zh-Hant  

No additions, no reordering.

---

## 5. Translation Requirements

- Try matching sentence size for small texts (small texts are usually used in buttons).
- Use standard UI terminology for each language.
- Avoid literal translations when a language has a conventional UI term (e.g., Dutch “station”, French “lecteur”, Japanese “ドライブ”).

---

## 6. Example Input

    <!--Error • Missing drive--> 
    <s:String x:Key="S.Errors.MissingDrive.Header">No drive</s:String>
    <s:String x:Key="S.Errors.MissingDrive.Message">The drive is unavailable or missing</s:String>

---

## 7. Example Output Pattern (shortened)

### English (UK) — en-GB  
    ```xml
        <!--Error • Missing drive-->
        <!--<s:String x:Key="S.Errors.MissingDrive.Header">No drive</s:String>-->
        <!--<s:String x:Key="S.Errors.MissingDrive.Message">The drive is unavailable or missing</s:String>-->
    ```

(…continue for all languages in required order)

---

## 8. Important
- Never add spaces inside comment tags.
- Never reorder languages.
- Always check inheritance and comment out matching translations.