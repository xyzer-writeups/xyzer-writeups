# Memory Me (Windows x86-64)

## Summary
This crackme is a runtime memory-edit challenge.  
It prints an address and asks you to set the boolean stored there to `true`.  
Solving it is done by changing the byte at the given address from `00` to `01` while the process is running.

## Goal
Trigger the success message:
`Good job! flag{this_is_not_the_correct_flag}`

## File Integrity
SHA256 (test.exe):
`0d250e26582003df908be6ed61face3df7d5d995ec1b42a52613b8e0ef9133c4`

## Behavior
When executed, the program prints:
`Your task: make the bool at address 00007FF7XXXXXXXXB0B8 true`

Notes:
- The printed address is a **runtime address** (it may change between runs due to ASLR).
- The task is always “make that bool true”.

## Solution (x64dbg)
1. Open `test.exe` in x64dbg and run (`F9`) until the task message appears.
2. Go to **Dump 1**.
3. Press **Ctrl+G** (Follow expression) and paste the printed address (example: `00007FF74DA5B0B8`).
4. At that address, patch the byte:
   - `00` → `01`
5. Continue execution (`F9`).

## Result
After patching the byte to `01`, the program prints:
`Good job! flag{this_is_not_the_correct_flag}`

## Notes
The output contains `flag{this_is_not_the_correct_flag}`, which strongly suggests this is a **dummy/success marker** rather than a real CTF flag (the string literally says it is not the correct flag).

## Proof
Add your successful-run screenshot here, e.g.:
- `proof.png`
