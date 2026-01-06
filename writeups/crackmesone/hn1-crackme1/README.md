# HN1’s Crackme 1 — Get The Password (Windows x86)

## Summary
This crackme validates a 10-character password using per-position ASCII constraints.
Because most checks are inequalities rather than strict equality, multiple valid passwords exist.

## Goal
Trigger the success message:
`Password is correct! ;)`

## Behavior
The program prompts:
`Enter password:`

It prints either:
- `Wrong password.`
- `Password is correct! ;)`

## Verification logic
The password must be exactly 10 characters. Each position is checked independently.

Constraints:
1. s[0] > 'G'
2. s[1] < 'm'
3. s[2] == 'V'
4. s[3] >= 'f'
5. s[4] <= '3'
6. s[5] > 'y'
7. s[6] >= '8'
8. s[7] < 'N'
9. s[8] != 'R'
10. s[9] == '2'

## Solutions
Any string satisfying the constraints is accepted. Examples confirmed:
- `HaVf0z8AQ2`
- `ZbVf1z8AQ2`

## Proof
See [proof.png](./proof.png) for a successful run.
