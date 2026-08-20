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