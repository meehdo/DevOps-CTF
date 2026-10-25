
# Lab 2 Report

**Course:** DevOps  
**University:** Amar El Telidj University

## Students

- ALLALI Mohammed Mehdi
- ELGUAIZI Mohamed
- GADOUAR Islam

[Github Repo](http://github.com/meehdo/DevOps-CTF/)

---

# Exercise 1

### (a) The pipeline runs on pull_request and also on push. What does pull_request give you that push cannot give?

**Answer:**

### (b) Why does lint run before tests?

**Answer:**

### (c) Our test suite takes 3 seconds. Why is this order more important for a test suite that takes 20 minutes?

**Answer:**

---

# Exercise 2

### (a) In lab sheet 1, you ran gitleaks yourself. A pre-commit hook can also run it before each commit. Which command skips such a hook?

**Answer:**

### (b) Now the pipeline scans every change for secrets. Who can still put a secret on main, a secret that the pipeline detects?

**Answer:**

---

# Exercise 3

### (a) Copy the error line from the log

**Answer:**

### (b) Use the term src layout to explain why the tests cannot import scoreboard without that line

**Answer:**

### (c) On your computer, you never typed this command. Which command ran it for you?

**Answer:**

---

# Exercise 4

| Defect | Gate that failed | Name in the log | One-line cause | How it failed |
| :--- | :--- | :--- | :--- | :--- |
| Test 1 | tests | `test_last_decaying_solve_is_one_step_above_the_floor` | Expected 150 points but got 100 | Assertion |
| Test 2 | tests | `test_average_of_an_empty_competition_is_zero` | `ZeroDivisionError` in `average_score` `return sum(totals) / len(totals)` | Exception |
| Credential | secret scan | `gitleaks` | Found 2 leaks | Detection |
| Dependency | dependency audit | `pip-audit` | `pyyaml 5.3.1` has known vulnerabilities | Detection |

---

# Exercise 5

### (a) Is the vulnerable package a direct or a transitive dependency?

**Answer:**

### (b) How did you find out? Give the command

**Answer:**
