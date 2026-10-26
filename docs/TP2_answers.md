
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

A pr gives the ability to test the changes as if it had been merged with target branch unlike push which would usually run test on the branch that received the push

### (b) Why does lint run before tests?

**Answer:**

Linting is faster than tests so its more efficient to run it first because if the code fails it will do so quickly giving the developer an opportunity to fix the issue instead of waiting for lengthy tests only for it to fail on a simple linting issue

### (c) Our test suite takes 3 seconds. Why is this order more important for a test suite that takes 20 minutes?

**Answer:**

Waiting 20 minutes only for it to fail at quick a test that could have been run first would be a waste of time

---

# Exercise 2

### (a) In lab sheet 1, you ran gitleaks yourself. A pre-commit hook can also run it before each commit. Which command skips such a hook?

**Answer:**

`git commit --no-verify`

### (b) Now the pipeline scans every change for secrets. Who can still put a secret on main, a secret that the pipeline detects?

**Answer:**

A repository administrator or a user with "Bypass branch protection" permissions can push directly to main or merge a pull request even if the pipeline detects it and it fails the checks.

---

# Exercise 3

### (a) Copy the error line from the log

**Answer:**
`
ImportError while loading conftest '/home/runner/work/DevOps-CTF/DevOps-CTF/tests/conftest.py'.
tests/conftest.py:17: in <module>
    from scoreboard.app import create_app
E   ModuleNotFoundError: No module named 'scoreboard'
`

### (b) Use the term src layout to explain why the tests cannot import scoreboard without that line

**Answer:**

this project uses src layout , the project code is in the `src/` instead of the root
With a src layout the package is in `src/scoreboard/` instead of the repository root. When tests run, Python doesn’t automatically search inside `src/`, so `import scoreboard` fails

`pip install -e .` registers the project’s `src` directory with the Python environment, allowing the tests to import `scoreboard`

### (c) On your computer, you never typed this command. Which command ran it for you?

**Answer:**

`make install`

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

The vulnerable package is a direct dependency

### (b) How did you find out? Give the command

**Answer:**

`cat requirements.txt`
