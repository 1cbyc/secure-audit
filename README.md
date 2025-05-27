# secure-audit

okay, today is a new day on my one project daily aim, and i am trying to build a smart contract audit tool. i noticed people i taught in 2021 became a big deal in just 18 months of work. the universe rewards those who put in their efforts and try their best.

to be honest, i have to perfect everything with the yarn setup and then i setup docker for this to work efficiently.

finally, the vuln scanner is working fine without errors. but i think it is not detecting vulnerabilities, gas optimizations or coe quality issues, because i intentionally used bad code from one hack for this. but i think this is because some detection methods i used are still stubs and need more robust AST traversal logic.

maybe because i am not much of a ui guy, so i want to perfect the vuln detection method before doing anything about the frontend/backend integration or even the UI itself. 

So, I will implement tx.origin usage detection, unchecked external calls, weak randomness sources, missing access control, and dangerous delegatecall usage before i sleep.