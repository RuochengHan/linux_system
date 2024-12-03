# GitLab

1. For gitlab: https://www.youtube.com/watch?v=kFs2K6arfIw
2. Upload new project
```bash
cd $project
git init
git remote add origin https://gitlab_repo
git add .
git config --global user.email ...
git config --global user.name ...
git commit -m "project upload"
git branch -M main
git pull --rebase origin main
git push -u origin main
```
3. change back to the remote branch (before you need to backup)
```bash
git fetch origin
git reset --hard origin/main
# Clean up unnecessary files and optimize the local repository
git gc --prune=now --aggressive
```
