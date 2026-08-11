# Build plan

1. Scaffold the Node.js CLI project folder, npm init, .gitignore, README, LICENSE, .env.example, and initial test setup.
2. Implement GitHub API client module with authentication and repo creation endpoints, including error handling and tests.
3. Implement project file generator that writes cli_tool.js (json pretty printer), README.md, LICENSE, .gitignore, ISSUE_TEMPLATE.md, and test files.
4. Implement git utility wrapper that initializes the repo, commits files, and pushes code to remote.
5. Implement GitHub issue generation with formatted issue for next steps.
6. Implement the actual CLI tool (cli_tool.js) to pretty-print JSON files from CLI args or stdin, fully tested.
7. Implement the setup.js CLI orchestrator to parse inputs, invoke GitHub API, generate project files, git push, issue creation, and print summary.
8. Add validation, rich error handling, input sanitization, and logging in setup.js.
9. Add comprehensive unit tests for all modules and overall integration simulation.
10. Finalize documentation, usage instructions, and cleanup.
