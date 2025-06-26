How it works for users:
Paste or load a Solidity contract in the web UI.
Click “Analyze Contract.”
Instantly see vulnerabilities, gas optimizations, and code quality issues, with severity and recommendations.
No login, no friction—just results.
Next steps:
You can further polish the UI or add more analyzers as needed.
When ready, deploy the frontend and backend for public access.


The frontend is now a beautiful, single-page app with a contract code editor, sample loader, and real-time results panel.
The backend exposes a public /api/analysis/public endpoint for contract analysis (no login needed).
The scanner engine is being improved to detect more vulnerabilities (reentrancy, tx.origin, weak randomness, etc.).
The UI is modern, responsive, and focused on the analysis experience.