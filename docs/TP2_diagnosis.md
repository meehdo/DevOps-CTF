| Defect | Gate that failed | Name in the log | One-line cause | How it failed |
| :--- | :--- | :--- | :--- | :--- |
| Test 1 | tests | `test_last_decaying_solve_is_one_step_above_the_floor` | Expected 150 points but got 100 | Assertion |
| Test 2 | tests | `test_average_of_an_empty_competition_is_zero` | `ZeroDivisionError` in `average_score` `return sum(totals) / len(totals)` | Exception |
| Credential | secret scan | `gitleaks` | Found 2 leaks | Detection |
| Dependency | dependency audit | `pip-audit` | `pyyaml 5.3.1` has known vulnerabilities | Detection |
