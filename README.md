# Northstar Exam Reviewer

An offline-first, local study site. Questions live in editable JSON files and attempt history lives in this browser's local storage. No account, database, or AI service is used during practice.

## Start the reviewer on a PC

1. Install Node.js if it is not already installed.
2. Open PowerShell in this project folder.
3. Run:

   ```powershell
   node server.js
   ```

4. Open [http://localhost:8000](http://localhost:8000) in a browser. Keep the PowerShell window open while using the reviewer.

The reviewer and its question files are served from your own PC. After the files are loaded, practice does not contact an internet service. The local server must be running when you open or refresh the page. The layout adapts to Android phone browsers too; for a phone on the same Wi-Fi, use the PC's local network address and port 8000.

## Question bank

Approved questions are in `data/english.json`, `data/math.json`, and `data/science.json`. Each file contains a JSON array. Keep each ID unique across all subjects. Use the provided `question-template.json` download from **Question review → Download JSON template** as a starting point. Required fields are:

```json
{
  "id": "MATH-009",
  "subject": "Mathematics",
  "topic": "Functions",
  "subtopic": "Function Evaluation",
  "difficulty": "Medium",
  "question": "If f(x) = x + 4, what is f(3)?",
  "choices": {"A":"5", "B":"7", "C":"8", "D":"12"},
  "answer": "B",
  "explanation": "Substitute 3 for x: f(3) = 3 + 4 = 7.",
  "concept": "Replace the input variable with the given value."
}
```

You can add questions to the subject JSON file and reload the reviewer, or use **Question bank → Add / review questions → Import JSON**. Imported questions enter drafts and do not appear in practice until approved. Review the question, choices, answer, and explanation; then approve, edit, or reject it. The import checks required fields and prevents duplicate IDs. When adding a new subject file, add its path to `SUBJECT_FILES` near the top of `js/app.js`.

For a review batch, check the boxes beside the questions you want, or choose **Select all**, then press **Approve selected**. The number on the button shows how many are selected. Only those selected drafts are moved into practice; the other drafts stay in the review queue.

The app does not generate questions. To prepare a future batch, supply the study materials and a requested subject/topic/count; create original questions in the same JSON shape, import them as drafts, and inspect and approve them. Existing question IDs should be left unchanged; new batches should use fresh IDs. The 24 original starter questions remain general high-school practice. The additional SASE set is based on the supplied checklist.

## Publish for phone access

The site is static and can be hosted with GitHub Pages. Put the files from this folder at the root of a GitHub repository, then enable **Settings → Pages** to publish from the `main` branch and root folder. GitHub will show a website URL that opens on phones and computers. A public Pages site can be opened by anyone with its link. Browser progress is saved locally per device and does not sync between phones or computers.

## Progress and backups

Attempt history, approved imported questions, and drafts are saved in this browser's local storage on this device. Use **Question review → Back up progress** to download a progress backup, and **Export bank** to back up approved questions. Also keep a copy of the project folder. Browser data is separate on each device and is not synced.

To reset attempt history and scores, use **Reset practice progress** on the dashboard. It keeps draft and approved questions. To also clear locally imported drafts and approved questions, open the reviewer and run `localStorage.removeItem('northstar-reviewer-v1'); location.reload();` in the browser's developer console. Questions in the JSON files are not removed.

## Current starter bank

There are 24 general starter questions and 52 new MSU-SASE-aligned draft questions in `data/msu-sase-drafts.json`. The draft batch follows topics listed in the supplied MSU-SASE checklist across science, mathematics, English, Filipino, and reading comprehension. The app loads these into **Question review** automatically; approve them there before they appear in practice. They are original practice items based on the checklist, not questions copied from the source guide. The bank is still below the original 500-question target; future batches can follow the same JSON format and review flow.

