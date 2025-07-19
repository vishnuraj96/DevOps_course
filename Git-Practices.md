
# Git Practices

## Assignment 1: Branch Operations

### Create Branch

**1. How do you create a new branch in GitLab using the web interface?**

- Step 1: Click on “New Project” to create a new project.  
- Step 2: Click on the “+” icon, then under “This repository”, click on “New branch” to create a new branch.  
- Step 3: Enter a branch name and select the source branch (typically main or master).  
- Step 4: Click “Create branch”.

**2. What steps do you follow to create a Merge Request (MR) in GitLab via the GUI?**

- Step 1: Go to your GitLab project and click on “Merge Requests” in the left menu.  
- Step 2: Click on “New merge request”.  
- Step 3: Select the source branch (the one you want to merge) and the target branch (usually main).  
- Step 4: Click “Compare branches and continue”.  
- Step 5: Fill in the title, description, and optionally assign reviewers or labels.  
- Step 6: Click “Create merge request”.

**3. How can you squash commits in a Merge Request before merging in GitLab?**

- Step 1: Open the Merge Request.  
- Step 2: Scroll down to the merge section.  
- Step 3: Check the box labelled “Squash commits when merge request is accepted.”  
- Step 4: Click “Merge” when ready.

**4. What is the process to revert a commit using the GitLab web interface?**

- Step 1: Go to your GitLab project and click on “Branches” from the “Code” dropdown in the left menu.  
- Step 2: Find the commit you want to revert.  
- Step 3: Click “Options” in the top right and select “Revert.”  
- Step 4: GitLab will prompt you to create a new merge request for the revert — confirm the options and proceed.  
- Step 5: Fill in the title, description, and optionally assign reviewers or labels.  
- Step 6: Click “Create merge request.”

**5. How do you delete a merged branch in GitLab using the GUI?**

- Step 1: Go to your GitLab project and click on “Merge Requests” from the “Code” dropdown in the left menu.  
- Step 2: Select the branch you want to delete.  
- Step 3: If it has already been merged, click “Delete branch” from the three dots on the right side.  
- Step 4: A confirmation message will appear, click “Yes, delete branch.”

## Assignment 2: Repository Operations

### Clone and Branch: 

**1. Clone a remote Git repository.**
- Step 1: Go to your GitLab project and click on “Repository” from the “Code” dropdown in the left menu.
- Step 2: Click Code and copy the HTTPS or SSH URL.
- Step 3: In terminal:
	```bash
 	git clone https://gitlab.com/vishnuraj784-group/assignment.git
	cd assignment
 	```
 
**2. Create a new branch for a specific feature or bug fix.**
	```bash
 	git checkout -b feature/my-feature
 	```
  
**3. Make changes in the new branch.**

	```bash
 	echo "My GitLab feature" > feature.txt
	git add feature.txt
	git commit -m "Add feature.txt in feature/my-feature"
 	```

**4. Push the branch to the remote repository.**

	```bash
	git push -u origin feature/my-feature
 	```
 
### Merge and Conflict Resolution: 
**1. Merge the changes from the feature branch into the main branch.**
- Step 1: Go to your GitLab project and click on “Merge Requests” in the left menu.
- Step 2: Click on “New merge request”.
- Step 3: Choose feature/my-feature → main.
 
- Step 4: Submit the merge request, then Merge it using the UI or command line.
  
**2. Simulate a merge conflict intentionally (modify the same line in both branches).**
**Create conflict:**
A) In the main branch
```bash
git checkout main
echo "Line to cause conflict" > conflict.txt
git add conflict.txt
git commit -m "Edit line in conflict.txt from main"
```

B) In a new branch
```bash
git checkout -b conflict-branch
echo "Conflicting change" > conflict.txt
git add conflict.txt
git commit -m "Conflicting change from conflict-branch"
```

C) Try merging into main:
```bash
git checkout main
git merge conflict_branch
```
 
3. Resolve the conflict and complete the merge.
```bash
	vim conflict.txt (Open conflict.txt)
<<<<<<< HEAD
Line to cause conflict
=======
Conflicting change
>>>>>>> conflict-branch
```

After resolving:
```bash
git add conflict.txt
git commit
```

Rebase: 
1. Create a new branch.
```bash
git checkout main
git pull
git checkout -b rebase-branch
```

3. Make some changes.
echo "Change for rebase" > rebase.txt
git add rebase.txt
git commit -m "Add change for rebase"
 
4. Rebase the new branch onto the main branch.
git checkout rebase-branch
git rebase main
 
5. Resolve any conflicts that may arise during the rebase.
Step 1: Git will pause on a conflict.
Step 2: Open and fix the conflict.
Step 3: 
	git add rebase.txt
git rebase –continue
	Step 4: Push Rebased Branch to GitLab
		git push --force origin rebase-branch
 
Assignment 3: Collaboration
Fork and Pull Request: 
1. Fork a repository on GitHub.
	Step 1: Go to a GitHub project repository
Step 2: Click the "Fork" button in the upper-right corner to copy the repo to your GitHub account.
2. Clone the forked repository to your local machine.
git clone https://github.com/vishnuraj96/Assignment.git
cd Assignment
 
3. Create a new branch and make changes.
git checkout -b feature
git add .
git commit -m "Add new feature or fix"
 
4. Push the branch to your fork.
	git push origin feature
 
5. Open a pull request to merge your changes into the original repository.
	Step 1: Go to your forked repo on GitHub.
	Step 2: Start the Pull Request, click “Contribute” → “Open pull request”.
	Step 3: Fill in Pull Request Details like Title and Description. Click the “Create pull request”
 
Code Review: 
1. Review a pull request in a repository.
	Step 1: Go to a repository where you have permission to review PRs.
Step 2: Click on the Pull Requests tab.
Step 3: Select a PR to review.
2. Provide constructive feedback on the changes.
	Step 1: Use GitHub’s review tools to add comments to specific lines.
Step 2: Highlight:
•	Code clarity issues
•	Logic or functionality bugs
•	Styling or formatting improvements
3. Discuss improvements or changes with the author.
Step 1: Engage politely in the conversation tab.
Step 2: Ask questions if needed, and suggest alternatives.
Step 3: Be respectful and clear.
Collaborative Workflow: 
1. Set up a repository collaboratively with a partner.
	Step 1: Go to GitHub, Click + (top right) → New repository.
	Step 2: Name your repo and choose settings (public/private, README, etc.)
	Step 3: Click Create repository.
	Step 4: On the repo page, go to Settings → Collaborators.
	Step 5: Click Add people.
	Step 6: Enter your partner’s GitHub username, full name or email.
	Step 7: Click Add to repository
2. Establish a workflow for making changes, creating branches, and merging.
	Step 1: Clone the repo and set up.
		git clone https://github.com/vishnuraj96/workflow.git
		cd workflow
		git checkout -b develop
 
Step 2: Create a Branch.
		git checkout -b add-user
 
	Step 3: Make changes and commit.
		git add .
		git commit -m "Add user authentication"
 
	Step 4: Push branch
		git push -u origin add-user
 
	Step 5:  Pull Request (PR)
		Go to your forked repo on GitHub.
		Start the Pull Request, click “Contribute” → “Open pull request”.
		Fill in Pull Request Details like Title and Description. Click the “Create pull request”


## Assignment 4: Advanced Git Concepts

### Git Hooks

**1. Write a pre-commit hook that checks for code style violations before allowing a commit.**

*(Implementation not provided in source document)*

### Git Bisect

**1. Simulate a bug in your project history.**  
**2. Use `git bisect` to find the commit where the bug was introduced.**
