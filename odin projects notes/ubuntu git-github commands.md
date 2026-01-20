**Create / Clone Repos**
- `git init` – initialize a repo
- `git clone https://github.com/user/repo.git` – clone a repo
**Basic Workflow**
- `git status` – check repo status
- `git add file.txt` – stage a file
- `git add .` – stage all changes
- `git commit -m "message"` – commit changes
- `git push` – push to GitHub
- `git pull` – pull latest changes
**Branches**
- `git branch` – list branches
- `git branch new-branch` – create branch
- `git checkout branch-name` – switch branches
- `git checkout -b new-branch` – create + switch
- `git merge branch-name` – merge branch
**Remotes**
- `git remote -v` – view remotes
- `git remote add origin https://github.com/user/repo.git` – add remote
**Logs & Undo**
- `git log` – commit history
- `git diff` – view changes
- `git restore file.txt` – undo unstaged changes
- `git reset --hard HEAD` – reset to last commit

- **commit** whenever you finish a small meaningful change, 
- **push** when you want it backed up or shared,  
- **pull** before starting work (or when collaborating) to make sure you’re up to date.
