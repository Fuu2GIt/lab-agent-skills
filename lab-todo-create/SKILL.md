---
name: lab-todo-create
description: >-
  Use when a student's agent creates Issues (Todos) following the lab's GitHub workflow: turning meeting minutes or the student's requests into Issues, splitting a large Issue, setting labels, priority numbers, prerequisite links, and `未定` (undecided) items, or adding a small-research-repo Issue to the board; agree with the student one question at a time before creating anything.
---
# Role
As the student's agent, create Issues (Todos) following the lab's GitHub workflow (a Project board per theme + Issues). Before creating anything, align understanding and assumptions with the student one question at a time (the grill-me style of questioning).

# When to use
- When you want to turn work decided in meeting minutes into Issues
- When you want to turn work from the student's own words into Issues
- When you want to split a large Issue
- When you want to tidy an Issue's labels, number, prerequisite relations, or `未定` (undecided) items
- When you want to add a small-research-repo Issue to the board

Board priorities, moving to `担当中` (the in-progress column), and closing are done with the `lab-board-manage` skill, not this one. If, after creating Issues, the student wants to go on and set priorities, continue with `lab-board-manage`.

# Questioning rules
- Talk to the student in Japanese (or in the language the student uses). The wording of this skill is English only for authoring.
- Ask only one question at a time. Always attach a recommended answer.
- Anything you can find out by looking (repo contents, minutes files, existing Issues and labels, conversation history, memory) — do not ask; look it up yourself.
- Gaps and risks the student has not mentioned — raise them yourself and ask.
- When the student's reply is only a quote, or its meaning is ambiguous, do not assume; restate it and confirm.
- Ask questions in chat, one at a time. Also record each question asked and the student's answer in the questionnaire file (create it every time, regardless of the number of questions). Until the answers are in, do not proceed with that work on assumptions.
- Keep the questionnaire in a single file. When a new question comes up, append it to that file. Location: `notes/questionnaire.md` for the student's personal items, `meetings/questionnaire.md` for items that two or more people in the theme answer. Separate it by subject (per Issue) with headings; inside each subject use the template `## 件名: <件名>（Issue #番号 関連、作成日 YYYY-MM-DD）` (subject, related Issue, creation date), `### 決めたいこと` (what to decide), `### すでに分かっていること` (what is already known), `### 回答欄` (answers). If the file does not exist yet, create it.
- Before starting to ask questions, read the existing questionnaire. Use already-answered items without asking again.
- Every addition or update to the questionnaire goes out, each time, on a branch as a Draft PR only after getting the student's "yes" (never push directly to main).
- If an answer in chat differs from the questionnaire, treat the newer one as correct and confirm with the student. Ask "The file says A, but now it's B, right? Shall I change it to B?", and after getting "yes", open a Draft PR fixing the file. When the student edits the file directly, treat its contents as correct the next time you read it.
- Writes — creating or splitting Issues, adding labels/assignees, adding to the board, etc. — happen only after showing a proposal and getting the student's "yes". Reading, proposing, and asking may be done without confirmation.
- When the student replies with only a quote, confirm which part it answers.

# Order of questioning (upstream first)
Proceed in the following order. Skip items already known without asking, and also skip items confirmed as "not relevant".

## 1. Decide the target (look it up; ask only for what is missing)
- Which theme repo, which small-research repo. → Target only the themes the student participates in and the student's own small-research repo. Find the repo and board locations yourself.
- For repos or boards you cannot see or have no access to, do not hunt around; tell the student.
- What to create from (a minutes file, the student's words, splitting an existing large Issue).

## 2. Read the material (do it yourself without asking)
- When creating from minutes: read the minutes file the student specified. The location differs per repo, so check the repo (often `minutes/YYYY-MM-DD.md`, with materials in `meetings/YYYY-MM-DD/`).
- Read existing Issues and the board, and look for duplicates and Issues likely to be prerequisites.
- Show a list of candidate work items from the minutes and ask "Shall I turn these N items into Issues?" (recommended: only decided work as candidates).

## 3. Decide each Issue's contents, one at a time
- Give it a single purpose. If there are multiple purposes, propose a split (see "Split" below).
- Write the completion criteria and verification method now, or before moving to `担当中` (in progress)? → Ask every time you create one. Recommended: "At the Todo stage write only purpose and background; write them before moving to in progress." The policy has two statements — "one purpose per Issue; completion criteria are required" and "it's fine to place items broadly and shallowly; completion criteria may be absent for now" — and this approach contradicts neither.
- Are there undecided points (remaining questions) in the decisions the student stated? If so, go to the `未定` (undecided) procedure below.

## 4. What the agent decides and puts in the proposal (decide without asking; show it in the proposal so the student can correct it)
- Purpose label: pick the closest one of `spike` (investigation), `task` (non-coding work), `feature` (adding/changing functionality), `bug` (defect).
- Agent labels (`human-only`, `agent-ok`, `needs-split`, `needs-clarification`): attach only if they already exist in the repo. If not, do not create them; tell the student. Meanings: `human-only` — done only by humans (operating experimental equipment, handling participants, verbal agreements with faculty, university procedures, etc.). `agent-ok` — the agent may proceed through investigation, drafting, implementation, and PR creation. `needs-split` — still a lump that needs splitting. `needs-clarification` — waiting for answers to questions.
- What must finish first (prerequisite Issue numbers) and what can start once this finishes (follow-up Issue numbers).
- Only when you cannot decide, ask one question.

## 5. `未定` (undecided) items and remaining questions
- Do not leave remaining questions written in comments or the body; the agent asks the student on the spot.
- Ask the student "Shall I also add a task to resolve that question?"
- Do not create tasks named "Decide ~". Decide such things with the student on the spot.
- If it can't be decided, mark it `未定` (undecided). Write it as one line in the body of the Issue that cannot proceed until it's decided (the follow-up), in the form `未定：〜（#番号 が終わったら再確認）` ("undecided: ~ (recheck when #number is done)"). In the prerequisite Issue, do not write the undecided item; write only the numbers under "what can start once this finishes".
- When a prerequisite Issue finishes, re-asking the follow-up's `未定` is the job of `lab-board-manage`.

## 6. Priority number
- Express priority by the number at the start of the title (1 is highest). The board has no priority or due-date field, so use only the number.
- For Issues you create too, look at existing Issues, decide the number, and include it in the proposal. Write the reason concisely and clearly, including why it has that priority. Do not write deadlines.
- Renumber existing Issues only after getting the student's "yes".

## 7. Split (when there is a large Issue)
- Show the student a split proposal (one purpose per child Issue), and create the child Issues only after getting "yes".
- Link parent and children using GitHub sub-issues (the parent/child feature).
- The pre-split lump card may get `needs-split` (only if the label exists).

## 8. Adding to the board
- Theme-repo Issues are added to the board automatically, so do not ask.
- Small-research-repo Issues are not added automatically. After creating one, ask "Shall I also add it to the board?", and after getting "yes", add it to the theme board via the equivalent of the Issue's Projects field.

## 9. Things to consider (raise and ask yourself, even if the student hasn't mentioned them)
- Is there already an Issue with the same content? (If so, don't create it; tell the student.)
- Is the assignee the student themself? Do not take Issues left unassigned or assigned to someone else.
- Are prerequisite and follow-up Issues reversed, or do the numbers form a cycle?
- When writing completion criteria, is the location of the deliverable (path or link) decided?
- Agent labels missing from the repo; boards that cannot be seen.

# Completion conditions
- Every item above has been answered or confirmed "not relevant".
- The confirmed contents have no contradictions.
- At the end, ask "Anything else on your mind?" exactly once.
- Then show the Issue proposals as a list (title, body, labels, prerequisites and follow-ups, `未定` items, whether to add to the board), and create them only after getting the student's "yes".

# Work (performed using the confirmed contents)
1. Titles use the form `番号. [接頭辞] 内容` (number. [prefix] content). Prefixes are `[調査]` (spike), `[タスク]` (task), `[機能]` (feature). There is no prefix for bug, so when not using one, use `[タスク]`. Example: `2. [タスク] 動画から特徴量を取り出す` (extract features from the videos).
2. The body uses the following template.
   - Purpose
   - Background (write richly: what is known / not known, failed attempts, option A/option B, related links)
   - Completion criteria (if decided not to write them yet, one line: "write before moving to `担当中` (in progress)")
   - Verification method
   - References
   - What must finish first (Issue numbers)
   - What can start once this finishes (Issue numbers)
   - Undecided (only when present: `未定：〜（#番号 が終わったら再確認）`)
3. The purpose label also guides the completion criteria. `spike`: one of "possible / not possible / possible with conditions" plus evidence. `task`: the location of the deliverable (path or link). `feature`: the PR is merged and it works per the verification method. `bug`: it no longer reproduces with the reproduction steps.
4. The assignee is the student themself (the agent acts with the student's account).
5. After creating an Issue, report its number and title to the student. For a small-research repo, also say whether it was added to the board.
6. Unless the student specified minutes, do not go read minutes on your own.

# Do not
- Do not create or split Issues, add labels or assignees, add to the board, or renumber before getting the student's "yes".
- Do not fill missing context by guessing. Ask.
- Do not create tasks named "Decide ~".
- Do not create the questionnaire before getting the student's "yes". Do not push the questionnaire file directly to main.
- Do not leave the assignee empty. Do not take Issues assigned to someone else.
- Do not write deadlines in priority reasons.
- Do not create agent labels without permission.
- Do not write to the lab-wide hub repo or the knowledge repo (read only; to change something, propose it in an Issue in that repo).
- Do not operate on boards/repos of themes the student does not participate in, or on anything without access.
- Do not push directly to main. When changing files, go through a branch and a Draft PR.
- Non-research work (administration, events, etc.) is out of scope for this skill (it is managed with a different tool).
