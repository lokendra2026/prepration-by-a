# Git & GitHub Commands — Complete Documentation

> Ye documentation Adarsh ke liye banayi gayi hai — sabhi important Git/GitHub commands, category-wise, saath me Hinglish explanation aur example usage.

---

## Table of Contents

1. [Setup Commands](#1-setup-commands)
2. [Repository Basics](#2-repository-basics)
3. [Staging & Committing](#3-staging--committing)
4. [Branching](#4-branching)
5. [Remote / GitHub Interaction](#5-remote--github-interaction)
6. [Undo & Fix Commands](#6-undo--fix-commands)
7. [History & Inspection](#7-history--inspection)
8. [Stashing](#8-stashing)
9. [Tags](#9-tags)
10. [GitHub CLI (`gh`) Commands](#10-github-cli-gh-commands)
11. [Merge Conflicts](#11-merge-conflicts)
12. [Useful Extras](#12-useful-extras)
13. [Typical Workflow (Feature Branch Flow)](#13-typical-workflow-feature-branch-flow)

---

## 1. Setup Commands

Ye commands ek baar setup karne ke liye hote hain, jab naya machine ya naya Git install karte ho.

| Command | Purpose (Hinglish) |
|---|---|
| `git config --global user.name "Adarsh"` | Tumhara naam set karta hai jo har commit ke saath attach hoga. |
| `git config --global user.email "you@example.com"` | Tumhara email set karta hai — GitHub commits ko is email se match karta hai. |
| `git config --list` | Saare configured settings dikhata hai (name, email, editor, etc). |
| `git config --global core.editor "code --wait"` | Default text editor set karta hai commit messages likhne ke liye (VS Code example). |
| `git --version` | Check karta hai ki Git install hai ya nahi, aur konsa version hai. |

---

## 2. Repository Basics

| Command | Purpose (Hinglish) |
|---|---|
| `git init` | Current folder ko Git repository bana deta hai. Naya project start karte waqt. |
| `git clone <url>` | GitHub se poora repo (history sahit) local machine pe copy karta hai. |
| `git clone <url> <folder-name>` | Clone karte waqt custom folder name dete ho. |
| `git status` | Batata hai kaunsi files modified/staged/untracked hain. Sabse zyada use hone wala command. |

---

## 3. Staging & Committing

| Command | Purpose (Hinglish) |
|---|---|
| `git add <file>` | Specific file ko staging area me daalta hai (commit ke liye ready). |
| `git add .` | Sabhi changed/new files ek saath stage karta hai. |
| `git add -p` | Interactively choose karte ho ki file ka kaunsa part (hunk) stage karna hai. |
| `git commit -m "message"` | Staged changes ko history me permanently save karta hai, ek message ke saath. |
| `git commit -am "message"` | Tracked files ko directly add + commit kar deta hai (new/untracked files ke liye nahi chalega). |
| `git diff` | Working directory aur last commit ke beech ka difference dikhata hai (line by line). |
| `git diff --staged` | Staged changes ka diff dikhata hai (jo abhi commit hone wale hain). |

---

## 4. Branching

| Command | Purpose (Hinglish) |
|---|---|
| `git branch` | Sabhi local branches ki list dikhata hai. |
| `git branch <name>` | Naya branch banata hai, but switch nahi karta. |
| `git checkout <branch>` | Existing branch pe switch karta hai. |
| `git switch <branch>` | Same as checkout — naye Git versions ka recommended tarika. |
| `git checkout -b <branch>` | Naya branch banake usi pe switch bhi kar deta hai (feature start karte waqt sabse common). |
| `git switch -c <branch>` | Same as upar wala, newer syntax. |
| `git branch -d <branch>` | Branch delete karta hai (safe delete — sirf jab merge ho chuka ho). |
| `git branch -D <branch>` | Force delete karta hai, chahe merge hua ho ya nahi. |
| `git merge <branch>` | Kisi branch ke changes ko current branch me le aata hai (combine karta hai). |
| `git branch -m <old> <new>` | Branch ka naam rename karta hai. |

---

## 5. Remote / GitHub Interaction

| Command | Purpose (Hinglish) |
|---|---|
| `git remote add origin <url>` | Local repo ko ek GitHub repo se link/connect karta hai. |
| `git remote -v` | Konse remotes connected hain (origin, upstream, etc) dikhata hai. |
| `git push origin <branch>` | Local commits ko GitHub pe upload karta hai. |
| `git push -u origin <branch>` | Upstream set karta hai — agli baar sirf `git push` likhne se kaam ho jayega. |
| `git push --force` | Forcefully remote history overwrite karta hai — **bahut careful use karo**, team projects me risky hai. |
| `git pull` | Remote se latest changes fetch karke current branch me merge kar deta hai. |
| `git fetch` | Sirf changes download karta hai, merge nahi karta — safe way hai dekhne ka ki remote pe kya naya hai. |
| `git remote remove <name>` | Kisi remote ko disconnect karta hai. |

---

## 6. Undo & Fix Commands

| Command | Purpose (Hinglish) |
|---|---|
| `git reset --soft HEAD~1` | Last commit undo karta hai, but changes staged hi rehte hain. |
| `git reset --mixed HEAD~1` | Last commit undo karta hai, changes working directory me aa jate hain (unstaged). |
| `git reset --hard HEAD~1` | Last commit + uske changes dono permanently delete — **data loss ho sakta hai, careful raho**. |
| `git revert <commit-hash>` | Purana commit delete nahi karta, balki naya commit banata hai jo uske changes undo karta hai. Team projects me safer option hai. |
| `git checkout -- <file>` | Kisi file ke uncommitted changes discard karke last commit wali state me le aata hai. |
| `git restore <file>` | Newer syntax, same purpose — file ko discard/restore karta hai. |
| `git commit --amend` | Last commit ka message ya content edit karta hai (push karne se pehle use karo). |

---

## 7. History & Inspection

| Command | Purpose (Hinglish) |
|---|---|
| `git log` | Commit history dikhata hai (author, date, message). |
| `git log --oneline` | Compact one-line summary me history dikhata hai. |
| `git log --oneline --graph --all` | Sabhi branches ka visual tree dikhata hai — samajhne me help karta hai konsa branch kahan se diverge hua. |
| `git blame <file>` | Batata hai file ki har line kisne aur kab likhi — debugging me useful. |
| `git show <commit-hash>` | Kisi specific commit ke exact changes dikhata hai. |

---

## 8. Stashing

| Command | Purpose (Hinglish) |
|---|---|
| `git stash` | Current uncommitted changes temporarily side me rakh deta hai (jab branch switch karna ho but commit ready na ho). |
| `git stash list` | Sabhi stashed changes ki list dikhata hai. |
| `git stash pop` | Latest stash wapas apply karta hai aur stash list se remove kar deta hai. |
| `git stash apply` | Stash apply karta hai but stash list se remove nahi karta. |
| `git stash drop` | Kisi stash ko permanently delete karta hai. |

---

## 9. Tags

Tags usually releases (v1.0, v2.0) mark karne ke liye use hote hain.

| Command | Purpose (Hinglish) |
|---|---|
| `git tag` | Sabhi tags ki list dikhata hai. |
| `git tag v1.0` | Current commit pe ek naya tag banata hai (release marking ke liye). |
| `git push origin v1.0` | Tag ko GitHub pe push karta hai. |

---

## 10. GitHub CLI (`gh`) Commands

GitHub CLI se browser khole bina terminal se hi GitHub operations kar sakte ho.

| Command | Purpose (Hinglish) |
|---|---|
| `gh repo clone <owner/repo>` | Terminal se seedha repo clone karta hai. |
| `gh repo create` | Naya GitHub repo terminal se hi create karta hai. |
| `gh pr create` | Pull Request create karta hai, bina browser khole. |
| `gh pr list` | Sabhi open Pull Requests dikhata hai. |
| `gh pr view <number>` | Kisi specific PR ka detail dikhata hai. |
| `gh issue create` | Naya issue terminal se create karta hai. |
| `gh issue list` | Sabhi open issues dikhata hai. |

---

## 11. Merge Conflicts

Jab do branches me same line change ho jaaye, tab Git confuse ho jaata hai — isko "merge conflict" kehte hain.

**Steps to resolve:**
1. `git merge <branch>` chalane ke baad agar conflict aaye, Git conflict wali files ko mark kar deta hai.
2. File open karo — Git conflict markers dikhega: `<<<<<<<`, `=======`, `>>>>>>>`.
3. Manually decide karo kaunsa code rakhna hai, markers delete karo.
4. `git add <file>` — resolved file ko stage karo.
5. `git commit` — merge complete karo.

---

## 12. Useful Extras

| Command / File | Purpose (Hinglish) |
|---|---|
| `.gitignore` | File hai (command nahi) — jisme specify karte ho konsi files/folders track nahi karni (e.g. `node_modules`, `.env`). |
| `git clean -fd` | Untracked files aur folders ko delete karta hai (careful — permanent hai). |
| `git rm <file>` | File ko repo se aur disk se dono jagah se remove karta hai. |
| `git mv <old> <new>` | File rename/move karta hai aur Git ko track karwata hai. |
| `git cherry-pick <commit-hash>` | Kisi specific commit ko doosre branch pe copy karta hai, bina poora branch merge kiye. |

---

## 13. Typical Workflow (Feature Branch Flow)

Ye workflow tumhare MERN stack projects (TripConnect, Luna, etc) ke liye typical hai:

```bash
# 1. Latest code lao
git checkout main
git pull origin main

# 2. Naya feature branch banao
git checkout -b feature/user-auth

# 3. Code likho, changes stage aur commit karo
git add .
git commit -m "feat: add JWT-based user authentication"

# 4. Branch ko GitHub pe push karo
git push -u origin feature/user-auth

# 5. GitHub pe (ya gh CLI se) Pull Request banao
gh pr create

# 6. Review ke baad main branch me merge karo
git checkout main
git pull origin main
git branch -d feature/user-auth
```

---

*Ye documentation ek quick-reference cheat sheet hai — daily Git/GitHub use ke liye best practices ke saath.*