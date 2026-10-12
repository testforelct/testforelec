# ELECTRANS website

Static website for **ELECTRANS**, a research project funded by the French National Research Agency (ANR) and devoted to the 2027 French elections. The site presents the project and its open call for survey question proposals. Proposals (.docx, .odt or .rtf) are submitted through a **Huma-Num ShareDocs upload link**, with email as a fallback (button on the How to Submit page); the site itself does not collect any data.

The site is plain HTML and CSS: no database, no build step, no frameworks. It is published with **GitLab Pages** (Huma-Num GitLab).

---

## Pages

| File | Page | Contents |
|---|---|---|
| `index.html` | Home | Summary banner with key dates, links to every page, and the call-for-proposals text |
| `about.html` | About | Project description, partner institutions, principal investigators (photos, short bios, links) |
| `panel.html` | The Panel | The ELECTRANS panel (Ipsos, ~10,000 respondents, four waves from January 2027) |
| `how-to-submit.html` | How to Submit | Submission instructions, template download, and the "Upload your proposal" button (ShareDocs link) |
| `faq.html` | FAQ | Questions grouped into five sections, shown as expandable answers |
| `news.html` | News and Announcements | Empty for now ("No announcements yet") |
| `contact.html` | Contact Us | Email contacts and subject-line codes for each type of question |

## Files and folders

```
electrans-website-official/
├── index.html, about.html, panel.html, how-to-submit.html,
│   faq.html, news.html, contact.html   ← the seven pages
├── style.css                           ← all colors, fonts and layout (shared by every page)
├── ELECTRANS_template.docx             ← submission template, downloadable from How to Submit
├── images/headshots/                   ← original square headshots of the investigators
├── .gitlab-ci.yml                      ← tells GitLab how to publish the site (do not delete)
└── README.md                           ← this file
```

Notes:
- **Investigator photos are embedded directly inside `about.html`**, so the About page works even if the `images` folder is missing. The files in `images/headshots/` are kept as originals.
- `.gitlab-ci.yml` is a hidden file. On a Mac, press **Cmd + Shift + .** in Finder to see it.
- Files such as `.DS_Store` or `.Rhistory` are created automatically by macOS/RStudio and can be ignored or deleted.

---

## Editing the website

All text is written directly in the HTML files. Open a file in any text editor (TextEdit in plain-text mode, VS Code, or GitLab's built-in editor), find the sentence, change it, and save.

- **Text** sits between tags, e.g. `<p>This is a paragraph.</p>`. Only change the words between the tags.
- **Special characters**: you can type accented letters (é, à) directly. Some existing text uses codes such as `&rsquo;` (apostrophe) or `&ndash;` (dash); leave these as they are.
- **Navigation menu**: the menu is repeated at the top of every page. If you add, remove or rename a page, update the menu in **all seven** files.
- **Colors and fonts**: change the values at the top of `style.css` (the `:root` section), e.g. `--navy` and `--accent`.

### Common edits

| Task | Where |
|---|---|
| Change the contact email address | `contact.html` (three times) and the fallback address in `how-to-submit.html`. Change both the visible address and the `mailto:` link |
| Change the upload link | In `how-to-submit.html`, replace the address in the `href="..."` of the "Upload your proposal" button |
| Post news | In `news.html`, replace the "No announcements yet" box with your announcement text |
| Edit an FAQ | In `faq.html`, each question is a `<details>` block: the question is in `<summary>`, the answer follows it |
| Change key dates | In `index.html`, the "Key dates" list (`<span class="when">` = date, `<span class="what">` = description) |
| Replace the template | Overwrite `ELECTRANS_template.docx`, keeping the same file name |
| Change an investigator photo | Save a square photo in `images/headshots/`. In `about.html`, find that person's `<img src="data:image/jpeg;base64,...">` and replace everything inside the quotes with the file path, e.g. `images/headshots/bol.jpg`. Then make sure the `images` folder is uploaded too |

**Preview your changes** by double-clicking any `.html` file to open it in your browser. Press **Cmd + Shift + R** to reload after saving.

---

## Publishing (GitLab Pages, Huma-Num)

1. Sign in to the Huma-Num GitLab and open the website project (or create a new project).
2. Upload **all** files to the root of the project, including `.gitlab-ci.yml`, `style.css` and the template. (Add file → Upload file, or drag and drop.)
3. Every time a change is committed to the main branch, GitLab publishes the site automatically. Follow progress under **Build → Pipelines**.
4. The site address appears under **Deploy → Pages**.
5. Under **Settings → General → Visibility**, set **Pages** to "Everyone" so applicants can see the site without logging in.

When updating the site, upload only the files you changed, but remember that layout changes usually involve **both** the HTML page and `style.css`.

---

## Open items

- [ ] Principal investigator bios were drafted from their official web pages: to be approved by the team
- [ ] FAQ answers expanded beyond the original document (multiple proposals, French/English questionnaire) to be confirmed by the team
- [ ] Post announcements on the News page as they come
