# 00_Inbox

## Purpose
This folder is a **temporary holding area** for papers whose **primary contribution
is not yet identified**.

Inbox exists to make uncertainty explicit, not to postpone classification forever.

---

## What goes into Inbox

- Papers saved by **title only**
- Papers not yet read beyond abstract
- Papers with **ambiguous or mixed contributions**
- Papers that look important but are not yet understood
- Papers added for future triage

---

## What does NOT belong here

- Papers whose main contribution is already clear
- Papers that have been seriously read or reviewed
- Papers used in experiments or implementations
- Survey / Tutorial papers (→ 99_Surveys_Tutorials)

Inbox is not an archive.

---

## Required Metadata (minimum)

Every paper in Inbox should have a small sidecar file:

<paper>.todo

Example:

```yaml
status: unread
first_impression: "ViT + frequency domain?"
suspected_contribution:
  - architecture
  - training_strategy
suspected_task:
  - face_anti_spoofing
added_at: 2026-01-29
```

This metadata answers one question:
Why is this paper still here?

## Exit Rules (Promotion Rules)

A paper must leave Inbox as soon as any one of the following is true:

1. Abstract + Figure 1 have been read
2. The main idea can be explained in one sentence
3. The primary contribution can be named

At that point, move the paper to exactly one of:

- 01_Loss_Objective/
- 02_Architecture/
- 03_Training_Strategy/
- 04_Dataset_Protocol/
- 05_Theory_Math/
- 99_Surveys_Tutorials/

One paper → One folder.

## Time Limit

- Inbox is reviewed weekly
- Inbox should be empty monthly
- No paper stays longer than 30 days

If a paper stays longer, it must be either:

- Classified
- Or removed
