# git-iam

**Version: v1.0.0**

`git-iam` is a custom CLI helper tool built in Python to simplify and standardize your Git branching workflow. It provides commands for creating sprints, features, hotfixes, fixes, commits, and PR/MR operations using either GitHub CLI (`gh`) or GitLab CLI (`glab`).

---

## 🚀 Features

- Initialize Git project
- Create sprint branches (take from master)
- Create feature branches (take from sprint)
- Create hotfix (take from master)
- fix branches (take from anywhere except mater)
- Commit with validation
- Create Pull Requests (PR) or Merge Requests (MR) (only for github or gitlab)
- Visualize commit history
- Interactive CLI mode

---

## Instatalation

1. make sure you have Python 3.10+ installed on your system.

```bash
python3 --version

# macOS install if not install yet
brew update
brew install python
# Then Verify
python3 --version
pip3 --version

# Linux install if not install yet
sudo apt update
sudo apt install python3 python3-pip
# Then Verify
python3 --version
pip3 --version
```

2. copy this base script to your local machine, then save it as `git-iam` and make it executable.

```bash
curl -o /usr/local/bin/git-iam https://raw.githubusercontent.com/ilhamnoerr95/git-iam/master/git-iam
chmod +x /usr/local/bin/git-iam
```

## 📘 Example Workflows

Every command will be display prompt inputs when needed.

```bash
git-iam # Choice mode
git-iam init # Initialize Git project
git-iam sprint # create srpint branch from master
git-iam feature # create feature branch from spint branch
git-iam hotfix # Create hotfix branch from master by default
git-iam fix # Create fix branch not from master
git-iam commit # Input message (max 50 charactesrs)
git-iam pr  ##  Follow input prompts for PR creation
git-iam log # Interactive log visualization
```

## The branching rule follows a structured Git-iam:

1. Every sprint branch is created from the master branch.
2. Each feature branch must be created from its corresponding sprint branch.
3. After development, all feature branches are merged back into the sprint.
4. Once a sprint is complete, the sprint branch is merged into the development branch.
5. Finally, the development branch is merged into master after final review and testing.

✅ This ensures a clean and traceable workflow from feature development to production-ready code.
