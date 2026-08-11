# Architecture

## Components

- **setup.js**: The orchestration CLI script for creating a repo, generating project files, initializing and pushing git, and creating GitHub issues.
- **lib/github.js**: GitHub REST API client functions for repo and issue creation with authentication and error handling.
- **lib/projectGen.js**: Generates local project files - CLI tool source, README, LICENSE, .gitignore, tests.
- **lib/gitUtil.js**: Wraps git CLI commands for init, add, commit, push.
- **cli_tool.js**: The small real-world problem solver CLI (a unique utility that formats JSON files in a pretty layout).

## Folder structure

```
root/
├── cli_tool.js              # The CLI tool solving the real-world problem
├── setup.js                 # The orchestrator CLI tool
├── lib/
│   ├── github.js
│   ├── projectGen.js
│   └── gitUtil.js
├── tests/
│   ├── test_cli_tool.js
│   └── test_github.js
├── README.md
├── LICENSE
├── .gitignore
├── package.json
├── ISSUE_TEMPLATE.md
├── .env.example
└── requirements.txt (none since Node.js?)
```

## Data flow

- User calls `node setup.js --repo <name> --description <desc> [--private]` with `GITHUB_TOKEN` env variable set.
- setup.js calls github.js to create the remote repository.
- projectGen.js generates local source files, including cli_tool.js with a JSON pretty printer utility.
- gitUtil.js initializes local git repo, adds files, commits, and pushes to GitHub.
- github.js creates a starter issue on the new repository.
- User can clone and run `cli_tool.js` independently for JSON formatting.

## Key decisions

- Use Node.js due to rich ecosystem for CLI tools and GitHub API libraries.
- Use native fetch API (node-fetch) for HTTP requests.
- Use commander for parsing CLI args.
- Use execa for git command execution.
- Make GitHub token mandatory via env variables for security.
- Single repository containing all configuration and CLI tool code.
- Tests use tap runner and mocks where needed.
- Real-world problem: a JSON file pretty formatter CLI tool (small, useful for developers).
