# git-iam

**Version: v1.1.6**

`git-iam` is a custom CLI helper tool built in Python to simplify and standardize your Git branching workflow. It provides commands for creating sprints, features, hotfixes, fixes, commits, and PR/MR operations using either GitHub CLI (`gh`) or GitLab CLI (`glab`).

---

## 🚀 Features

- Initialize Git project
- Create sprint branches (take from master)
- Create feature branches (take from sprint)
- Create hotfix (take from master)
- create fix branches (take from anywhere except mater)
- Commit with validation
- Create Pull Requests (PR) or Merge Requests (MR) (only for github or gitlab)
- Visualize commit history
- Interactive CLI mode
- push to remote
- sprint-finish & feature-finish for fast-forward without merge-request or pull request and automatically delete branch local and remote

> [!note]
> This tool is designed to work with GitHub and GitLab. If you are using a different version of Git or a different version of the Git CLI, you may need to adjust the commands accordingly.

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

3. Skip this step if you already have github/gitlab cli

```bash

# install git cli
# macOS install if not install yet
brew update
brew install gh
# Then Authentication
gh auth login

# install gitlab cli
# macOS install if not install yet
brew update
brew install glab
# Then Authentication
glab auth login

# -------------------------
# install in linux
# install `gh` in ubuntu/Debian
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
  && sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | \
  sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null

sudo apt update
sudo apt install gh

# install gh in Fedola /RHEL/ CentOs
sudo dnf install 'dnf-command(config-manager)'
sudo dnf config-manager --add-repo https://cli.github.com/packages/rpm/gh-cli.repo
sudo dnf install gh

#---------------
# install glab(gitlab CLI) in ubuntu/Debian:
curl -s https://api.github.com/repos/profclems/glab/releases/latest \
| grep "browser_download_url.*deb" | cut -d '"' -f 4 | wget -i -

sudo dpkg -i glab_*.deb

# install glab in Fedora/ RPM-based:
curl -s https://api.github.com/repos/profclems/glab/releases/latest \
| grep "browser_download_url.*rpm" | cut -d '"' -f 4 | wget -i -

sudo rpm -i glab_*.rpm

# check version
gh --version
glab --version

```

4. Update Version

```bash
curl -fsSL -o /usr/local/bin/git-iam https://raw.githubusercontent.com/ilhamnoerr95/git-iam/master/git-iam
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
git-iam push ## push to remote
git-iam log # Interactive log visualization
git-iam sprint-finish # finish sprint branch after merged into development, fast-forward to development without Pull request or merge request
git-iam feature-finish # finish feature branch after merged into sprint, fast-forward to sprint without Pull request or merge request
```

> [!note]
> sprint-finish and feature-finish are only for sprint and feature branch respectively, it will not create Pull request or merge request.
> it will ask prompt input for the target of branch that want to merge.
> if you want to create Pull request or merge request, use `git-iam pr` instead.

## The branching rule follows a structured Git-iam:

1. Every sprint branch is created from the master branch.
2. Each feature branch must be created from its corresponding sprint branch.
3. After development, all feature branches are merged back into the sprint.
4. Once a sprint is complete, the sprint branch is merged into the development/anything branch naming you want.
5. Finally, the development/anything branch is merged into master after final review and testing.

✅ This ensures a clean and traceable workflow from feature development to production-ready code.
