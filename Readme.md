# Gym Git Exercise Solutions

## Bundle 1 - Exercise 1

Project repo: <https://github.com/F3anny/gym-git-basics>

```bash
git init
git add .
git commit -m "feat: initial commit"
git branch -m master main
git branch -m main master
git branch -m master main
git remote add origin <your-repo-url>
git push -u origin main
git checkout -b dev
git checkout -b test
git checkout dev
git branch -d test
```

## Bundle 1 - Exercise 2

```bash
git add home.html
git stash save "Home page changes"


git add about.html
git stash save "about page changes"


git add team.html
git stash save "team page changes"

git stash list

git stash pop stash@{1}
git stash pop stash@{1}

git commit -m "feat: add home and about pages"
git push origin main

git stash pop

git reset --hard HEAD
```
## Bundle 2 - Exercise 1

```bash
git checkout main
git pull origin main

git checkout -b ft/bundle-2


git add services.html
git commit -m "feat: add services page"
git push -u origin ft/bundle-2
```
PR opened on GitHub: `ft/bundle-2` → `main`, reviewed, merged.

## Bundle 2 - Exercise 2

```bash
git checkout main
git pull origin main

git checkout -b ft/service-redesign

# edited services.html — changed <h1> to "Our Redesigned Services"
git add services.html
git commit -m "feat: redesign services heading"
git push -u origin ft/service-redesign
```
PR opened on GitHub: `ft/service-redesign` → `main` (left open, not merged).

```bash
git checkout main

# edited services.html directly — changed same <h1> line to "Premium services"
git add services.html
git commit -m "feat: update services heading on main"
git push origin main
```
Refreshed the open PR — GitHub showed a merge conflict.

```bash
git checkout ft/service-redesign
git diff main
git merge main
```
Conflict appeared in `services.html`:
```html
<<<<<<< HEAD
<h1>Our Redesigned Services</h1>
=======
<h1>Premium services</h1>
>>>>>>> main
```
Resolved manually in VS Code, keeping one final `<h1>` line and removing the conflict markers.

```bash
git add services.html
git commit -m "fix: resolve merge conflict between service-redesign and main"
git push origin ft/service-redesign
```
PR merged successfully into `main` after conflict resolution.
## Bundle 3 - Exercise 1

```bash
git checkout main
git pull origin main
git checkout -b ft/team-page


git add team.html
git commit -m "feat:add team page"
git push -u origin ft/team-page
```
PR opened on GitHub: `ft/team-page` → `main`.

```bash
git checkout main
git checkout -b ft/contact-page

git checkout ft/team-page
git log --oneline
```
Copied last commit hash on `ft/team-page`: `ee57d37fee0039e077097bb45c189d4ba1a8c749`

```bash
git checkout ft/contact-page
git cherry-pick ee57d37fee0039e077097bb45c189d4ba1a8c749
```
Result: new commit `d2174a8` created on `ft/contact-page`, bringing in `team.html`.

```bash
git add contact.html
git commit -m "feat: add contact page"
git push -u origin ft/contact-page
```
PR opened on GitHub: `ft/contact-page` → `main`.

```bash
git checkout ft/contact-page
git checkout -b ft/faq-page

git add faq.html
git commit -m "feat: add faq page"
git push -u origin ft/faq-page
```

```bash
git checkout ft/team-page
git revert ee57d37fee0039e077097bb45c189d4ba1a8c749
git push origin ft/team-page
```
Revert commit added on top of the original `feat:add team page` commit, removing `team.html` again. Pushed to the existing `ft/team-page` PR (updates automatically rather than creating a second PR for the same branch).
