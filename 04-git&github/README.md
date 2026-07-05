# 🌿 Module 04 — Git & GitHub

Version control is one of the most important skills for developers and DevOps engineers. It allows us to track changes, collaborate with others, and safely manage the history of a project.

This module documents my journey of learning Git and GitHub—from basic commands to branching, merging, and working with remote repositories.

---

## 📂 Module Contents

| File                    | Description                                                                       |
| ----------------------- | --------------------------------------------------------------------------------- |
| `git-basics.md`         | Installing Git, configuration, repositories, commits, logs, and everyday commands |
| `branching-merging.md`  | Creating branches, switching branches, merging, and resolving conflicts           |
| `github-workflow.md`    | Working with GitHub, remotes, pushing, pulling, cloning, and collaboration        |
| `undoing-changes.md`    | Restoring files, resetting commits, reverting changes, and recovering work        |
| `gitignore.md`          | Using `.gitignore` to exclude files and directories                               |
| `ssh-authentication.md` | Connecting GitHub using SSH keys                                                  |

---

# What is Git?

Git is a **distributed version control system** that keeps track of changes made to files over time.

Instead of creating multiple copies of a project like:

```text
Project/
Project_Final/
Project_Final_v2/
Project_Final_Final/
Project_Really_Final/
```

Git stores the complete history of your project, allowing you to revisit previous versions whenever needed.

---

# What is GitHub?

GitHub is a cloud platform that hosts Git repositories.

While Git tracks changes on your local machine, GitHub allows you to:

* Store repositories online
* Collaborate with other developers
* Share code publicly or privately
* Review changes through Pull Requests
* Back up your projects

> **In short:** Git is the version control tool, while GitHub is a platform for hosting and collaborating on Git repositories.

---

# Understanding Tracked, Untracked, and Staged Files

One of the first concepts I learned in Git was that every file has a **state**.

Instead of thinking about files as simply "existing," Git classifies them based on whether it knows about them and whether they're ready to be committed.

The easiest way for me to remember this is with a **school assignment analogy**.

---

## 📄 Untracked Files

Imagine your teacher asks you to submit an assignment.

You've just created a brand-new notebook.

The teacher doesn't even know this notebook exists yet.

That's exactly what an **untracked file** is.

Git sees that the file exists in your project folder, but it isn't being monitored yet.

```text
New File
    │
    ▼
Untracked
```

Example:

```bash
touch notes.txt
git status
```

Git will show:

```text
Untracked files:
notes.txt
```

---

## 📄 Tracked Files

Now imagine you've submitted your notebook once.

From this point onward, your teacher knows that this notebook belongs to you.

Any future changes can now be noticed.

This is a **tracked file**.

Git now monitors the file and knows whenever it changes.

```text
Git knows this file
        │
        ▼
Tracked
```

---

## 📄 Staged Files

Suppose you've finished editing your assignment.

Before the teacher grades it, you place it into the submission tray.

The submission tray is like Git's **staging area**.

You're telling Git:

> "These are the changes I want to include in my next commit."

Only the files placed in the staging area will become part of the next snapshot.

```text
Modified File
       │
git add
       │
       ▼
Staging Area
       │
git commit
       │
       ▼
Repository History
```

---

# The Complete Journey of a File

Every file typically moves through these states:

```text
Create File
      │
      ▼
Untracked
      │
git add
      │
      ▼
Staged
      │
git commit
      │
      ▼
Tracked
      │
Edit File
      │
      ▼
Modified
      │
git add
      │
      ▼
Staged
      │
git commit
      │
      ▼
Tracked (Updated Version)
```

---

# Why Does Git Use a Staging Area?

At first, I wondered why Git doesn't simply commit every modified file automatically.

The staging area gives us control.

Suppose I modify three files:

```text
README.md
app.py
notes.txt
```

I may only want to commit changes to:

```text
README.md
app.py
```

while leaving `notes.txt` for later.

Using `git add`, I can decide exactly which changes belong in the next commit.

This makes commits cleaner, more organized, and easier to understand.

---

## 🎯 Learning Objectives

After completing this module, I aim to understand:

* How Git tracks changes
* The lifecycle of files in Git
* Creating and cloning repositories
* Staging and committing changes
* Viewing project history
* Working with branches
* Resolving merge conflicts
* Connecting local repositories to GitHub
* Collaborating using remote repositories

---

> **Learning Note:** These notes reflect my current understanding of Git and GitHub. As I work on more projects, I'll continue expanding this module with practical workflows, troubleshooting tips, and best practices.
