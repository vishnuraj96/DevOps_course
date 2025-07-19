
# Git Practices

## Assignment 1: Branch Operations

### 1. Create a Branch in GitLab (Web UI)
1. Click “New Project”.
2. Click the “+” icon → “New branch”.
3. Enter branch name and select source branch (main/master).
4. Click “Create branch”.

### 2. Create a Merge Request (MR)
1. Go to “Merge Requests” → “New merge request”.
2. Select source and target branches.
3. Click “Compare branches and continue”.
4. Fill in details and click “Create merge request”.

### 3. Squash Commits in a Merge Request
1. Open the MR.
2. Scroll to merge section.
3. Check “Squash commits”.
4. Click “Merge”.

### 4. Revert a Commit via GitLab UI
1. Go to “Branches” under “Code”.
2. Find the commit → Click “Options” → “Revert”.
3. Confirm MR for revert.
4. Fill details and click “Create merge request”.

### 5. Delete a Merged Branch
1. Go to “Merge Requests”.
2. Find merged branch → Click three dots → “Delete branch”.
3. Confirm the deletion.

## Assignment 2: Repository Operations

### Clone and Branch
```bash
git clone https://gitlab.com/vishnuraj784-group/assignment.git
cd assignment
git checkout -b feature/my-feature
echo "My GitLab feature" > feature.txt
git add feature.txt
git commit -m "Add feature.txt in feature/my-feature"
git push -u origin feature/my-feature
```

### Merge and Conflict Resolution
#### Merge changes via UI and simulate conflict
```bash
# Main branch
git checkout main
echo "Line to cause conflict" > conflict.txt
git add conflict.txt
git commit -m "Edit line in conflict.txt from main"

# Conflict branch
git checkout -b conflict-branch
echo "Conflicting change" > conflict.txt
git add conflict.txt
git commit -m "Conflicting change from conflict-branch"

# Attempt to merge
git checkout main
git merge conflict-branch
```

#### Resolve conflict manually
Open `conflict.txt` and edit to resolve:
```
<<<<<<< HEAD
Line to cause conflict
=======
Conflicting change
>>>>>>> conflict-branch
```
Then run:
```bash
git add conflict.txt
git commit
```

### Rebase Workflow
```bash
git checkout main
git pull
git checkout -b rebase-branch
echo "Change for rebase" > rebase.txt
git add rebase.txt
git commit -m "Add change for rebase"
git rebase main
# On conflict
git add rebase.txt
git rebase --continue
git push --force origin rebase-branch
```

## Assignment 3: Collaboration

### Fork and Pull Request
```bash
git clone https://github.com/vishnuraj96/Assignment.git
cd Assignment
git checkout -b feature
git add .
git commit -m "Add new feature or fix"
git push origin feature
```
Open a Pull Request on GitHub → “Contribute” → “Open pull request”.

### Code Review
1. Go to Pull Requests tab.
2. Add inline comments.
3. Discuss constructively.

### Collaborative Workflow
```bash
git clone https://github.com/vishnuraj96/workflow.git
cd workflow
git checkout -b develop
git checkout -b add-user
git add .
git commit -m "Add user authentication"
git push -u origin add-user
```
Then submit a PR.

## Assignment 4: Advanced Git Concepts

### Git Hooks
Implement a `pre-commit` hook to check code style.

### Git Bisect
```bash
git bisect start
git bisect bad
git bisect good <commit_hash>
```
