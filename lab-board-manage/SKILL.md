---
name: lab-board-manage
description: >-
  Use when a student's agent manages the lab's GitHub Project board (`Todo` / `担当中` (in progress) / `Done`): proposing priorities for "what should I do first today?", moving to in progress on "I'm starting this", closing on "it's done", and re-asking `未定` (undecided) items when a prerequisite finishes; agree with the student one question at a time before acting.
---
# Role
As the student's agent, manage the theme board of the lab's GitHub workflow (only three columns: `Todo` / `担当中` (in progress) / `Done`). Before acting, align understanding and assumptions with the student one question at a time (the grill-me style of questioning).

# When to use
- When asked for priorities, e.g. "What should I do first today?" or "Tidy up the board"
- When told "I'm starting this" (moving to `担当中`, in progress)
- When told "It's done" / "Finished" (close)
- When a prerequisite Issue finishes (re-asking the follow-ups' `未定` undecided items)

Creating new Issues, splitting them, or turning minutes into Issues is done with the `lab-todo-create` skill, not this one. When a request spans both, finish `lab-todo-create` and then continue with this skill.

# Questioning rules
- Talk to the student in Japanese (or in the language the student uses). The wording of this skill is English only for authoring.
- Ask only one question at a time. Always attach a recommended answer.
- Anything you can find out by looking (board contents, Issues and comments, assignees, labels, conversation history, memory) — do not ask; look it up yourself.
- Gaps and risks the student has not mentioned — raise them yourself and ask.
- When the student's reply is only a quote, or its meaning is ambiguous, do not assume; confirm which part it answers.
- Ask questions in chat, one at a time. Also record each question asked and the student's answer in the questionnaire file (create it every time, regardless of the number of questions). Until the answers are in, do not proceed with that work on assumptions.
- Keep the questionnaire in a single file. When a new question comes up, append it to that file. Location: `notes/questionnaire.md` for the student's personal items, `meetings/questionnaire.md` for items that two or more people in the theme answer. Separate it by subject (per Issue) with headings; inside each subject use the template `## 件名: <件名>（Issue #番号 関連、作成日 YYYY-MM-DD）` (subject, related Issue, creation date), `### 決めたいこと` (what to decide), `### すでに分かっていること` (what is already known), `### 回答欄` (answers). If the file does not exist yet, create it.
- Before starting to ask questions, read the existing questionnaire. Use already-answered items without asking again.
- Every addition or update to the questionnaire goes out, each time, on a branch as a Draft PR only after getting the student's "yes" (never push directly to main).
- If an answer in chat differs from the questionnaire, treat the newer one as correct and confirm with the student. Ask "The file says A, but now it's B, right? Shall I change it to B?", and after getting "yes", open a Draft PR fixing the file. When the student edits the file directly, treat its contents as correct the next time you read it.
- Reading, proposing, and asking may be done without confirmation. Operations that change the board or Issues (adding assignees/labels, moving to `担当中` (in progress), closing, renumbering titles, adding comments) happen only after showing a proposal and getting the student's "yes".

# Order of questioning (upstream first)
Skip items already known without asking, and also skip items confirmed as "not relevant".

## 1. Decide the target (look it up; ask only for what is missing)
- Operate only on the boards of themes the student participates in, those themes' repos, and the student's own small-research repo. Find the board locations yourself.
- For boards or repos without access, or anything you cannot see, do not hunt around; tell the student.
- The lab-wide hub repo and the knowledge repo are read only. To change something, propose it in an Issue in that repo.

## 2. Proposing priorities (for "What should I do first today?")
- Read the scope the student specified. If none is specified, read the board's whole `Todo` column and the Issues assigned to the student. If "one item" is specified, read that Issue and its comments.
- Express priority by the number at the start of the Issue title (1 is highest, in the form `1. [タスク] 内容`). The board has no priority or due-date field. Do not use the three buckets "do today / later is fine / want to discuss".
- Attach a one-line reason to each number. Keep it concise and clear, including why it has that priority (example: "1. Get filming permission. Until this is done, the other 3 items can't start."). Do not write deadlines. Base the reasons on what must finish first, what can start once it finishes, whether it can be advanced right now, and waiting states (`needs-clarification`, etc.).
- Do not start on everything at once. Show the proposal; the student decides. Once the student decides, ask "May I renumber the titles?", and renumber on "yes".
- Do not make `human-only` Issues candidates for starting (do not touch them).

## 3. Moving to `担当中` (in progress) (when the student says "I'm starting")
Check that the following three are all in place. Ask on the spot and decide whatever is missing.
1. The assignee is the student themself (do not move to in progress while unassigned. Do not take Issues assigned to someone else; if helping, reach out in a comment).
2. Completion criteria and a verification method are written.
3. No `未定` (undecided) items remain. If any remain, ask on the spot and decide them.
Once all are in place, show the proposal to move it to in progress, and move it after getting "yes".

## 4. Confirm completion and close
Ask "Is it done?" only when you see one of the following:
- The student said "It's done" / "Finished".
- Work satisfying that Issue's completion criteria was confirmed in the chat.
- A PR linked to that Issue was merged (in this case it closes automatically via `Closes #番号` (Closes #number) in the PR body, so the only confirmation is the one-line result comment).
Do not ask just because the agent thinks "it looks done". For Issues without completion criteria, ask only when the student says so.
Steps: ① Ask the student "Is it done?" and get "yes". ② Comment the result in one line. ③ Close the Issue (closing moves it automatically to `Done` on the board). ④ Go to the previous step.

## 5. Re-asking `未定` (undecided) items when a prerequisite finishes
- Find the Issues whose numbers are listed under "what can start once this finishes" in the closed Issue.
- Ask the student again about that Issue's `未定` items (example: "Shall we decide #15's undecided item 'video publication scope' now?").
- Once decided, show a proposal rewriting the `未定` line to the decided content, and fix it after getting "yes". If still undecided, leave it as `未定`, and keep asking again each time a prerequisite finishes after this.

## 6. Things to consider (raise and ask yourself, even if the student hasn't mentioned them)
- Do not touch Issues that are unassigned or assigned to someone else.
- Renumbering can change the titles of many Issues. Show the count before getting "yes".
- On shared boards where someone other than the student handles the student's Issues, the assignee is the only signal of "whose hands it is in now". Do not change assignees on your own.
- When `Todo` has unstarted cards with an assignee, the meaning of the assignee becomes ambiguous, so confirm with the student whether work has started.
- When `担当中` (in-progress) Issues remain due to graduation, handing back, etc., confirm with the student whether to close them or hand them over (change the assignee).
- When the board or labels cannot be seen, do not hunt around; tell the student.

# Completion conditions
- Every item above has been answered or confirmed "not relevant".
- The confirmed contents have no contradictions.
- At the end, ask "Anything else on your mind?" exactly once.
- Then show the list of changes (assignees, labels, moves, closes, title numbers, comments), and execute only after getting the student's "yes".

# Work (performed using the confirmed contents)
1. Proposing priorities: reading and proposing can be done without confirmation.
2. Moving to `担当中` (in progress): when the conditions in "3. Moving to `担当中` (in progress)" above are met and the student says "I'm starting".
3. Close: the steps in "4. Confirm completion and close" above. Comment the result in one line, then close.
4. When a prerequisite finishes, re-ask the follow-ups' `未定` items.
5. After making changes, report to the student what was changed.

# Do not
- Do not add assignees/labels, move to `担当中` (in progress), close, or renumber before getting the student's "yes".
- Do not move to in progress while unassigned. Do not take Issues assigned to someone else.
- Do not start on everything on your own in response to an instruction like "work on whatever you like from the board's Todo".
- Do not touch `human-only` Issues.
- Do not fill missing context by guessing. Ask.
- Do not create tasks named "Decide ~".
- Do not create the questionnaire before getting the student's "yes". Do not push the questionnaire file directly to main.
- Do not write deadlines in priority reasons.
- Do not write to the lab-wide hub repo or the knowledge repo.
- Do not operate on boards/repos of themes the student does not participate in, or on anything without access.
- Do not push directly to main. When changing files, go through a branch and a Draft PR.
- Non-research work (administration, events, etc.) is out of scope for this skill.
