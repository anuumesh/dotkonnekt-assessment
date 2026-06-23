# Publishing This Repository

This repository is ready to share. Before publishing, confirm the repository name and GitHub organization you want to use.

Recommended repository name:

```text
dotkonnekt-delivery-head-assessment
```

Recommended visibility:

```text
Private if sharing with selected candidates
Public only if this assessment is intended to be broadly available
```

## Publish Commands

Run the commands below from the root of this assessment folder after creating the GitHub repository.

```bash
git init
git add .
git commit -m "Add DotKonnekt delivery assessment"
git branch -M main
git remote add origin https://github.com/dotkonnekt/dotkonnekt-delivery-head-assessment.git
git push -u origin main
```

After the repository is live, share the GitHub URL with candidates.

Before sharing, check that:

- The repository is public or candidates have access
- The templates are readable
- The submission instructions are clear
- Contact details are correct
- Any private client information has been removed

## Candidate Sharing Message

Use this message when sending the assessment:

```text
Hi,

Thank you for your interest in the Delivery Head role at DotKonnekt.

Please complete the assessment in this repository:
https://github.com/dotkonnekt/dotkonnekt-delivery-head-assessment

Submit your response as a pull request with your files under a folder named after you inside the submissions directory.

The assessment includes three written deliverables and one 15-minute executive presentation recording. The details, templates, and scoring rubric are included in the repository.

Regards,
DotKonnekt Hiring Team
```
