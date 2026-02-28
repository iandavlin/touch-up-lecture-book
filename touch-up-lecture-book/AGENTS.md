When a message matches:

<bullet text> | <image path>

Automatically:

1) Target file: presentation.md
2) Mode: reference
3) Copy image into images/reference/
4) Slug filename from bullet text (lowercase, hyphenated)
5) Replace exact bullet:

- <bullet text>

With:

- [<bullet text>](#img-<slug>) <!-- img: images/reference/<slug>.<ext> | mode: reference -->

6) Append if missing:

---
<!-- _id: img-<slug> -->
![contain](images/reference/<slug>.<ext>)

7) Do not change anything else.
8) If bullet is ambiguous, ask which section.
Return only: Attached <slug>