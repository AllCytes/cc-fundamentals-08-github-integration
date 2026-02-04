# GitHub Integration & Mobile Workflows

> Work from anywhere. Let Claude handle tasks while you're away from your computer.

## Make It Your Own

After cloning, remove the original remote and create your own GitHub repository:

**Windows (PowerShell)**
```powershell
git remote remove origin
gh repo create cc-fundamentals-08-github-integration --public --source=. --remote=origin --push
```

**Mac / Linux**
```bash
git remote remove origin
gh repo create cc-fundamentals-08-github-integration --public --source=. --remote=origin --push
```

> **Prerequisite:** Install the [GitHub CLI](https://cli.github.com/) — `winget install GitHub.cli` (Windows) or `brew install gh` (Mac), then run `gh auth login` once.

---

## Before the Purpose

You don't always have access to your development machine. Maybe you're on your phone, commuting, or just away from the keyboard. GitHub Integration solves this.

With Claude's GitHub App installed, you can:
- Create issues from your phone describing what you need
- Tag `@claude` to start work
- Check back later to see completed code and PRs
- Review and merge when you're ready

This module teaches you to set up that workflow.

---

## Purpose

GitHub Integration enables:

```
Phone/Tablet                    GitHub                         Claude
     │                            │                              │
     │  Create issue              │                              │
     ├───────────────────────────►│                              │
     │                            │                              │
     │  Comment: @claude          │      Trigger workflow        │
     ├───────────────────────────►│─────────────────────────────►│
     │                            │                              │
     │                            │    Read issue, work on it    │
     │                            │◄─────────────────────────────┤
     │                            │                              │
     │                            │      Create commits, PR      │
     │                            │◄─────────────────────────────┤
     │                            │                              │
     │  Review results            │                              │
     │◄───────────────────────────┤                              │
     │                            │                              │
Desktop: Review code, merge      │                              │
```

---

## Prerequisites

Before using `/install-github-app`, you need:

1. **GitHub CLI installed and authenticated** (see [GitHub CLI Setup](guides/github-cli-setup.md))
2. **Repository admin access** (you must own or be admin of the repo)
3. **Active Claude subscription** (Pro or Max)

---

## What's Included

### Guides

| Guide | Description |
|-------|-------------|
| [GitHub CLI Setup](guides/github-cli-setup.md) | Install and authenticate GitHub CLI |
| [Install GitHub App](guides/install-github-app.md) | Step-by-step /install-github-app walkthrough |
| [Claude in Issues](guides/claude-in-issues.md) | Using @claude to work on issues |
| [Claude in PRs](guides/claude-in-prs.md) | Automatic PR reviews with @claude |
| [Mobile Workflow](guides/mobile-workflow.md) | The complete phone-to-merge workflow |

### Examples

| Example | Description |
|---------|-------------|
| [Workflow Examples](examples/github-workflow-examples.md) | Real-world issue and PR scenarios |

### Commands

| Command | Description |
|---------|-------------|
| `/EA-prime` | Understand the codebase |
| `/EA-handoff` | Save session state |
| `/EA-pickup` | Resume from handoff |
| `/EA-install` | Install commands globally or to a project |

---

## Quick Start

### Step 1: Install GitHub CLI

**Windows PowerShell:**
```powershell
winget install GitHub.cli
```

**Mac:**
```bash
brew install gh
```

**Linux:**
```bash
sudo apt install gh
```

### Step 2: Authenticate

```bash
gh auth login
```

Follow the prompts:
- Select: **GitHub.com**
- Select: **HTTPS**
- Select: **Login with a web browser**
- Copy the code, paste in browser, authorize

### Step 3: Get This Repo (Make It Yours)

```bash
# Clone the template
git clone https://github.com/[org]/08-github-integration.git my-project
cd my-project

# Remove the original remote
git remote remove origin

# Create your own repo and push
gh repo create my-project --public --source=. --push
```

Now you're the admin of your own copy.

### Step 4: Install GitHub App

```bash
claude
```

Then run:
```
/install-github-app
```

Follow the prompts (detailed in [Install GitHub App guide](guides/install-github-app.md)).

### Step 5: Test It

1. Go to your repo on GitHub
2. Create a new issue: "Add a hello world function"
3. Comment: `@claude please implement this`
4. Watch Claude work in the issue comments
5. Click the PR link when Claude is done
6. Review and merge

---

## The Mobile Workflow

```
┌─────────────────────────────────────────────────────────────┐
│ MOBILE (Phone/Tablet)                                       │
├─────────────────────────────────────────────────────────────┤
│ 1. Open GitHub app or mobile browser                        │
│ 2. Create issue: "Add dark mode toggle to settings"         │
│ 3. Comment: "@claude please implement this"                 │
│ 4. Close phone, go about your day                           │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│ CLAUDE (Runs Automatically)                                 │
├─────────────────────────────────────────────────────────────┤
│ • Reads the issue                                           │
│ • Creates a todo list in comments                           │
│ • Works through each step                                   │
│ • Commits changes                                           │
│ • Posts link to create PR                                   │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│ LATER (Phone or Desktop)                                    │
├─────────────────────────────────────────────────────────────┤
│ • Check issue comments to see Claude's work                 │
│ • Review the PR                                             │
│ • Merge when ready                                          │
│ • Nothing deployed without YOUR approval                    │
└─────────────────────────────────────────────────────────────┘
```

---

## Two GitHub Workflows

When you run `/install-github-app`, you can install two workflows:

### 1. Claude Code (Issues)

**Triggers when**: You comment `@claude` on an issue

**What it does**:
- Reads the issue description
- Creates a plan
- Implements the feature/fix
- Commits code
- Provides PR link

### 2. Claude Code Review (PRs)

**Triggers when**: A new PR is opened

**What it does**:
- Reads all changes in the PR
- Reviews for: Code Quality, Bugs, Performance, Security
- Posts review with checkmarks/concerns
- You can ask follow-up questions with `@claude`

---

## Folder Structure

```
08-github-integration/
├── .claude/
│   └── commands/          # EA-* commands
├── guides/                # Documentation
│   ├── github-cli-setup.md
│   ├── install-github-app.md
│   ├── claude-in-issues.md
│   ├── claude-in-prs.md
│   └── mobile-workflow.md
├── examples/              # Real-world examples
│   └── github-workflow-examples.md
├── specs/
│   ├── todo/
│   ├── done/
│   └── handoffs/
└── README.md
```

---

## Key Takeaways

1. **Admin access required** - You must own or be admin of the repo
2. **GitHub CLI first** - Install and authenticate before `/install-github-app`
3. **Clone → Own workflow** - Clone template, remove origin, push to your own repo
4. **Mobile-friendly** - Start work from anywhere, review when ready
5. **You control merges** - Nothing deploys without your approval

---

## Troubleshooting

### "Not a repository admin"
You can't install the GitHub App on repos you don't own. Use the Clone → Own workflow to create your own copy.

### "gh: command not found"
GitHub CLI isn't installed. Follow [GitHub CLI Setup](guides/github-cli-setup.md).

### "Authentication required"
Run `gh auth login` and complete the browser authentication.

### Claude doesn't respond to @claude
1. Check the GitHub Action ran (Actions tab in your repo)
2. Verify the workflow files exist (`.github/workflows/`)
3. Make sure you merged the setup PR from `/install-github-app`

---

## Next Steps

1. Read [GitHub CLI Setup](guides/github-cli-setup.md)
2. Follow [Install GitHub App](guides/install-github-app.md)
3. Try the [Mobile Workflow](guides/mobile-workflow.md)
4. Reference [Workflow Examples](examples/github-workflow-examples.md)

---

*Work from anywhere. Review when ready. Ship with confidence.*
