> 📎 Project Context: [paste project-context.md here / already in chat / read from file]
> ⚠️  If project-context is not attached, the AI will ask before proceeding.

---

## 🎯 TASK HEADER

| Field        | Value                                                        |
|--------------|--------------------------------------------------------------|
| **Task ID**  | TASK-[N]  ← increment from "Last Task ID" in CURRENT STATE  |
| **Name**     | [Short name — e.g. "Add email verification flow"]            |
| **Mode**     | [Feature / Bug Fix / Refactor / Performance / Security / Question] |
| **Priority** | [Critical / High / Medium / Low]                             |

---

## 🔗 CONTEXT

- **Depends on Task:** (TASK-XXX / None)
- **Continues from:** ([In Progress item name from Blueprint] / None)
- **Related Files:** [Files AI must READ for context — not modify]
- **Last Session Note:**
  [1–2 lines: where we left off / what changed since last time]
  [OR: "Fresh start — no prior session"]

---

## 📋 DESCRIPTION

[Write exactly what needs to be done here.]
[More detail = significantly better output from AI.]
[Vague description = vague code.]

---

## ✅ EXPECTED OUTPUT

[What must work correctly when this task is done.]
[  "API returns X with status 200"]
[  "UI shows Y when user clicks Z"]
[  "DB has new column in users table"]
[  "CLI prints W without error"]

---

## 🏁 ACCEPTANCE CRITERIA

- [ ] [Criterion 1 — specific and verifiable]
- [ ] [Criterion 2 — specific and verifiable]
- [ ] [Criterion 3 — specific and verifiable]

---

## 📁 FILES

### Files to Modify
- `path/to/file.ext`  →  [what changes and exactly why]
- `path/to/file.ext`  →  [what changes and exactly why]

### Files to Create
- `path/to/new-file.ext`  →  [purpose of this new file]

### Files to Delete
- `path/to/file.ext`  —  [reason for deletion]

### DO NOT TOUCH
- `path/to/file.ext`  —  [reason: e.g. "stable in production"]
- `path/to/file.ext`  —  [reason: e.g. "other team owns this"]

---

## ⚠️ EDGE CASES TO HANDLE

- [What if the input is null or empty?]
- [What if the user has no permission for this action?]
- [What if an external API call fails or times out?]
- [What if two users trigger this simultaneously?]
- [What if the list returned is empty?]

---

## 🚫 AVOID

- [Don't use X library for this — reason]
- [Don't restructure the Y folder — out of scope]
- [Don't modify the Z interface — other modules depend on it]
- [Don't add a migration without a rollback script]

---

## 🗃️ NEW DB CHANGES NEEDED

```
NEW TABLE / ALTERED TABLE: table_name
  column_name  TYPE  CONSTRAINTS
  column_name  TYPE  CONSTRAINTS

DROP TABLE: table_name

NEW INDEX:
  table_name(column_name) — reason

REMOVED INDEX:
  table_name(column_name) — reason

NEW RELATIONSHIP:
  table_a 1──* table_b (via table_b.foreign_key)

ROLLBACK PLAN:
  [Describe how to undo this migration if it fails]
```