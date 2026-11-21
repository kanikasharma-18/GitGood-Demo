# GitGood-Demo

GitGood-Demo is a demonstration project for [`git-good-guard`](https://www.npmjs.com/package/git-good-guard) version 0.1.0.

It shows how to add the GitGood CLI to a Node.js repository and use Git hooks to add safety checks before or during commits. This repository demonstrates GitGood's behavior; it is not the source code or main development repository for GitGood.

## What GitGood checks

GitGood provides several checks to help prevent common Git mistakes:

- **Secret detection:** Looks for sensitive values in staged files, such as API keys and other credentials.
- **Large-file detection:** Identifies files that may be too large to commit. The included `.gitgoodrc.json` sets the maximum file size to 5 MB.
- **Commit-message validation:** Checks commit messages against GitGood's configured rules.
- **Protected-branch warnings:** Warns when you try to work directly on protected branches. The demo configuration protects `main`, `master`, `production`, and `develop`.

GitGood does not guarantee that every secret or unsafe commit will be detected. It is a useful first line of defense, not a replacement for code review or dedicated secret-scanning tools.

## Installation

Install GitGood from npm in the demo repository:

```bash
npm install git-good-guard
```

The `git-good` CLI is available through `npx` or, when installed locally, through the npm package's executable.

## Initialize GitGood

Create the GitGood configuration file:

```bash
npx git-good init
```

This command creates `.gitgoodrc.json`, where options such as `maxFileSize` and `protectedBranches` can be configured.

## Install Git hooks

Install the Git hooks into this repository:

```bash
npx git-good hooks install
```

After installation, GitGood can run automatically when Git commands trigger the configured hooks. Review the Git status and hook behavior in a development branch before relying on them in a team workflow.

## Run safety checks manually

Run the GitGood checks without waiting for a Git hook:

```bash
npx git-good check
```

This command checks the current repository according to `.gitgoodrc.json`.

## Example workflow

```bash
# Create or change to a development branch
git switch -c feature/demo-check

# Stage the files you want to inspect
git add .

# Run GitGood manually
npx git-good check

# Commit your staged changes
git commit -m "feat: add demo example"
```

Example commands for hook and configuration setup:

```bash
npm install git-good-guard
npx git-good init
npx git-good hooks install
npx git-good check
```

## Package and source

- Published npm package: [git-good-guard on npm](https://www.npmjs.com/package/git-good-guard)
- Original GitHub source: [kanikasharma-18/GitGood](https://github.com/kanikasharma-18/GitGood)
- Demonstration repository: [kanikasharma-18/GitGood-Demo](https://github.com/kanikasharma-18/GitGood-Demo)
