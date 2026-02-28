# Attach image to bullet (one-liner)

Input format:
<bullet text> | <image path>

Defaults:
- Target markdown: notes/outline.md
- Image destination folder: images/
- Action: copy (never move)
- Mode tag: reference (metadata only)

Procedure:
1) Ensure images/ exists.
2) Copy the image into images/ using a safe filename:
   - lowercase
   - hyphen slug based on bullet text
   - keep extension
3) In notes/outline.md find the bullet line whose visible text equals <bullet text>.
   - If multiple matches, ask which section heading it’s under.

4) Link handling:
   - If the bullet text is NOT already a markdown link, convert it to:
     - [<bullet text>](#img-<slug>)
   - If the bullet text IS already a markdown link:
     - Ask ONE question: "Overwrite link or append image metadata only?"
     - Overwrite = replace existing link target with #img-<slug>
     - Append-only = leave the existing link as-is and ONLY append/refresh the img metadata comment.

5) Append/refresh metadata comment at end of the bullet:
   <!-- img: ../images/<filename> | mode: reference -->

   NOTE: The path in the comment must be correct relative to notes/outline.md:
   use ../images/<filename>

6) Ensure an anchor + image block exists (GitHub-compatible):
   Append at end of notes/outline.md if missing:

   ---
   <a id="img-<slug>"></a>

   ![contain](../images/<filename>)

7) Do not change any other content.

Return only:
- Attached <slug>
- dest: images/<filename>
- md: notes/outline.md
