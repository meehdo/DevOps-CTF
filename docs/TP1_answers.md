# Lab 1 Report

**Course:** DevOps  
**University:** Amar El Telidj University

## Students

- ALLALI Mohammed Mehdi
- ELGUAIZI Mohamed
- GADOUAR Islam

[Github Repo](http://github.com/meehdo/DevOps-CTF/)

---

# Exercise 1

### (a) `ls -a` shows two files whose names start with a dot. What are their names?

**Answer:**

Git has the following two dot files:

- `.gitignore`
- `.git`

The repository already has `.env.example`.

On macOS, we also have the `.DS_Store` file. It was added to `.gitignore` as well.

### (b) What would happen if you use `cp -r .../ctf-scoreboard/*` instead (with a star at the end)? What is different?

**Answer:**

It wouldn't copy the hidden dot files.

### (c) Imagine that `.env` is already in a commit. Then you add `.env` to `.gitignore`. Why does this not protect the file?

**Answer:**

Because `.gitignore` only affects untracked files. If the file is already tracked, you would have to stop tracking it first.

---

# Exercise 2

### (a) Why can't Git merge these two changes automatically?

**Answer:**

Since they modify the same line in two different ways, the changes overlap and create a conflict.

### (b) How is that different from merging two changes to two different challenges in the same file?

**Answer:**

The difference is that the changes wouldn't conflict if they modified different, non-overlapping parts of the file.

### (c) A check for conflict markers can run automatically, so that nobody needs to remember the grep. Where can this check run?

**Answer:**

Before pushing, using CI, or locally using a pre-commit hook.

---

# Exercise 3

### (a) How many steps did `git bisect` need to search the 31 commits?

**Answer:**

5 runs.

### (b) Compare this number with `log₂(31)`

**Answer:**

`log₂(31) ≈ 4.9`, so the number of test runs matches.

### (c) Imagine that `check.sh` is inside the repository. What goes wrong?

**Answer:**

Checking out different commits can change or remove the script, so it may fail to run.

### (d) Imagine that the 31 commits are squashed into one commit. What does `bisect` return?

**Answer:**

It would identify the commit as the first bad commit, but since it contains many changes, we wouldn't know which change caused the issue.

---

# Exercise 4

### (a) Give the exit code of each scan

**Answer:**

- `gitleaks dir .` exited with code `0`.
- `gitleaks git -v .` exited with code `1`.

The directory scan found no leak in the current files.

The Git scan found one in the repository's history.

### (b) Give the name of the rule that matched

**Answer:**

`aws-access-token`.

### (c) Every commit stores the hash of its parent commit. Use this fact to explain why the second commit removes nothing

**Answer:**

The second commit has the first commit as its parent. It removes the key from the new commit's file snapshot, but it doesn't change the parent or erase the earlier commit.

The first commit and the key in it remain in the history, so the history scan still finds it.

### (d) Imagine that someone pushed a real key. List the first two steps your team takes, in order. Explain why this order

**Answer:**

1. Immediately deactivate or revoke the exposed key.
2. Remove the key from Git history by rewriting the history.

Revoking the key first prevents further unauthorized use. Rewriting the history then removes the exposed key from the repository's commit history.

---

# Exercise 5

### (a) People often see branch protection as a quality measure. Explain in three or four lines why it is also a security control

**Answer:**

It requires reviewed pull requests and passing checks before changes reach an important branch.

That makes unauthorized changes, planted backdoors, and tampering with sensitive code harder to merge because approval from other parties is required.

### (b) Name the attack that it makes harder

**Answer:**

It makes it harder for an attacker who has taken over an account to merge malicious code into a protected branch.

### (c) On a free GitHub account, the repository must be public for this part. Why?

**Answer:**

GitHub Free provides protected branch features for public repositories. Using them in a private repository requires a paid account.
