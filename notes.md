# General Discussions

1. Git and github are different . Git is a software and github is a service.

2. Git is a version control system i.e it tracks file for changes. It tracks files not folders . So if there is no files in some folder then it will not be tracked by git. To solve this problem we make .gitkeep file inside such folders.

3. git -v or git --version to check git version. Git comes with great backward compatibility.

4. Repository: A folder having .git folder. inside it.

5. ls -la command shows all files whether hidden or not.

6. git status: check status

7. git init => Initialsie git repository.

8. git add . (Add all the files to staging area)

9. git commit -m "commit message" .(To commit the changes ). Commit acts as checkpoint . If you commit your changes then it will never get lost until the branch itself is deleted. commits are always stored in stack way using linked list.

10. git log : to check the commit history of a branch 
git log --oneline => to check the commit history of a branch in one line.

11. keep commits centric to one feature, one component or one fix . Commit message should be written like commands given to computer.

12. .gitignore: It is used to store the file that you dont want to track. It can be generated easily using gitignore generators.

13. Branch is an alternative timeline.

```bash
git checkout -b create-and-move-to-new-branch
git checkout "move to new branch" # It can be used to move to differernt branch as well as different commit ids
git branch # Used to see all the branches

```

14. Always commit or stash your changes before moving to differnt branch. If you are in some branch B1 and you have made some changes there:-
(a) If you have not commited those changes and moved to differnt branch your changes is now there in other branch and is lost from branch B1.

(b) If you have  commited those changes and moved to differnt branch then your changes d is not lost from branch B1.

(c) Whenever you create branch b1 from b0 then all the code in branch b0 goes to branch b1.

# Configuragtions:

```bash
git config --global user.name "Rahul"
git config --global user.email "codedevwap@gmail.com"
git config --global code.editor "code --wait"
git config --local user.name "Rahul"
git config --local user.email "codedevwap@gmail.com"
git config --local code.editor "code --wait"
```

# Merging the branches:

1. To merge branch b1 into the current branch use command :
```bash
git merge b1
```
If there are merge conflicts while merging branch b1 to your current branch then :-
(a) Resolve the conflicts manually (when you remove <<< etc symbol the github considers that merge conflict is resolved)
(b) git add files
(c) git commit -m "resolve merge conflicts"

2. git stash => stored uncommited changes
git stash pop => bring back those changes

git stash apply => bring back those chanhes and bring them in stash area.

3. Git Diff (informative command)
git diff (compare working with staging )
-> How to read diff
· a - file 1 R b- file 2 (same file over time) D --- file t
E indicates change in file
·
I
+ +
file s
·
changes in lines & little preview of it

4. Git rebase is an alternative way of merging and is a cleanup tool(as it rewrites history ). Never run git rebase on main branch . It should always be run on side branches. 

5. git reflog => Keeps track of where head is moving.

# Resolving merge conflicts:-

1. ```bash
git push -u origin main # setup an upstream that allows you to run future commmans i.e git push
```
2. Suppose you are in branch b1 and you wanted to push the changes to main branch . If while pushing and making pull request you get merge conflicts:-
```bash
git checkout main
git pull 

git checkout b1

git rebase main

# Resolve the conflicts manually

git add .
git rebase --continue

git commit -m "commit message"

git push -f

```

# Head


# Handling submodules


# Ways to contribute to open source project

1. Find a project

2. Fork the repository.

3. Clone the repository

4. make you changes and raise pr


# Branches 

```bash
git branch -d b1 # remove b1 from local if its merged

git branch -D b1 # remove branch b1 from lcoal

git push -u  orign b1 # push branch b1 from local to remote

git push origin --delete b1 # remove branch b1 from remote
```

# git cherry-pick command:

Here is a concise response to the query about the git cherry-pick command with an example:

## Using Git Cherry-Pick

The `git cherry-pick` command allows you to apply specific commits from one branch to another. This is useful for selectively incorporating changes without merging entire branches.

Here's an example of how to use `git cherry-pick`:

1. Ensure you are on the branch you want to apply the commit to:
   ```
   git checkout main
   ```

2. Find the commit you want to cherry-pick by checking the commit log:
   ```
   git log
   ```
   Let's say the commit you want to pick has the hash `a1b2c3d`.

3. Apply the commit to your current branch:
   ```
   git cherry-pick a1b2c3d
   ```

   This will create a new commit on the `main` branch that has the same changes as the original commit from the other branch.[1][2][3][4]

The key benefits of `git cherry-pick` are:

- **Selective Integration**: You can pick and choose specific commits to apply, rather than merging entire branches.
- **Fixing Mistakes**: If you accidentally commit to the wrong branch, you can cherry-pick the commit to the correct branch.
- **Backporting Fixes**: You can cherry-pick bug fixes from a development branch into a release branch.[5]

However, overusing `git cherry-pick` can lead to a messy commit history, so it's generally recommended to use `git merge` or `git rebase` instead, unless you have a specific need for the selective integration that `git cherry-pick` provides.


13. Code migration:

Migration changes:

Pull from Development.
Pull code from 4.1-Dev
create branch from 4.1-Dev.
checkout new branch
git merge Development --no-commit --no-ff
Pick Appropriate changes 
commit those changes
Push code
Raise Pull request from new branch to 4.1-Dev
Verify pull request. 
Ask for review
That is it.

14. 1. To add a submodule to a Git repository, you use the git submodule add command followed by the URL of the repository you want to include. This command allows you to incorporate one Git repository as a subdirectory within another, which is particularly useful for managing dependencies.

2. Agar submodule me ek jagah change hoga to wo saare jagah reflect karega jab hum latest changes un saare jagah pull karenge tab.

3. git reset HEAD~3 uncommit last 3 commits

4. The `git submodule deinit` command is used to unregister a submodule from your Git repository. It removes the submodule configuration from the `.gitmodules` file and optionally removes the submodule directory from your local file system.

The syntax for deinitializing a submodule is:

```
git submodule deinit [-f | --force] [--all] [--] [<path>...]
```

- **`<path>`**: Specifies the path of the submodule you want to deinitialize.
- **`--all`**: If specified, deinitializes all registered submodules.



To deinitialize a specific submodule, run:

```
git submodule deinit <submodule_path>
```

This command will remove the submodule configuration from the `.gitmodules` file and the `.git/config` file. However, it does not remove the submodule directory from your local file system.


If you want to completely remove the submodule directory from your local file system, you can use the `-f` or `--force` option:

```
git submodule deinit -f <submodule_path>
```

This command will deinitialize the submodule and remove the submodule directory.


To deinitialize all registered submodules, you can use the `--all` option:

```
git submodule deinit --all
```

This command will deinitialize all submodules and remove their configurations from the `.gitmodules` and `.git/config` files.


- **Removing Submodule Files**: After deinitializing a submodule, you may still have files related to the submodule in your working directory. To remove these files, you can use `git rm --cached <submodule_path>`.

- **Committing Changes**: After deinitializing and removing a submodule, you need to commit the changes to the `.gitmodules` file and the removal of the submodule directory.

- **Submodule Tracking**: If you have any branches or tags that track the submodule, they will become invalid after deinitializing the submodule. You may need to update or remove these references.



The `git submodule deinit` command is useful for removing submodules from your Git repository. It allows you to unregister submodules and optionally remove their directories from your local file system. However, it's important to carefully manage submodule dependencies and ensure that your project still functions correctly after deinitializing a submodule.

5. The `git submodule update` command is used to synchronize your submodules with the versions specified in your main repository. This command ensures that your submodules are checked out to the correct commit that is recorded in the parent repository.


The syntax for updating submodules is:

```
git submodule update [options] [--recursive] [<path>...]
```


1. **Basic Update**:
   To update all submodules to the commit specified in the parent repository, simply run:

   ```bash
   git submodule update
   ```

   This command will check out the specific commit of each submodule as recorded in the parent repository.

2. **Updating to the Latest Commit**:
   If you want to update the submodules to the latest commit on their respective branches (assuming you have set up tracking branches), you can use the `--remote` option:

   ```bash
   git submodule update --remote
   ```

   This command fetches the latest changes from the remote repositories for each submodule and checks them out.

3. **Recursive Update**:
   If your submodules themselves contain submodules (nested submodules), you can update them recursively with the `--recursive` option:

   ```bash
   git submodule update --recursive
   ```

   This ensures that all levels of submodules are updated to their respective commits.

4. **Updating a Specific Submodule**:
   If you want to update a specific submodule, you can specify the path to that submodule:

   ```bash
   git submodule update <submodule_path>
   ```


- **Initialization**: If you clone a repository that contains submodules, you need to initialize them first before updating. This can be done with:

  ```bash
  git submodule update --init
  ```

  or, if you want to initialize and update all submodules in one command:

  ```bash
  git submodule update --init --recursive
  ```

- **Committing Changes**: If you make changes within a submodule (e.g., you want to move it to a different commit), you need to commit those changes in the submodule itself and then update the parent repository to point to the new commit.


The `git submodule update` command is essential for managing submodules in your Git projects. It ensures that your submodules are in sync with the main repository, allowing for consistent builds and development environments. By using the appropriate options, you can easily manage updates for both simple and nested submodules.

6. To add a submodule to a Git repository, you use the `git submodule add` command followed by the URL of the repository you want to include. This command allows you to incorporate one Git repository as a subdirectory within another, which is particularly useful for managing dependencies.

The syntax for adding a submodule is:

```
git submodule add <repository_url> [<subdirectory>]
```

- **`<repository_url>`**: This is the URL of the Git repository you want to add as a submodule.
- **`<subdirectory>`** (optional): This specifies the directory where the submodule will be cloned. If not provided, Git will create a directory named after the repository.


For example, to add a library called "DbConnector":

```
git submodule add https://github.com/chaconinc/DbConnector
```

This command will clone the "DbConnector" repository into a directory named "DbConnector" within your current repository. 


When you add a submodule, Git performs several actions:

1. **Cloning the Submodule**: The specified repository is cloned into the designated directory.
2. **Creating the `.gitmodules` File**: A new file named `.gitmodules` is created in the root of your repository. This file tracks the submodule's URL and path. For example:

   ```
   [submodule "DbConnector"]
   path = DbConnector
   url = https://github.com/chaconinc/DbConnector
   ```

3. **Staging Changes**: The new submodule and the `.gitmodules` file are staged for commit. You need to commit these changes to finalize the addition of the submodule:

   ```
   git add .gitmodules DbConnector
   git commit -m "Added DbConnector submodule"
   ```


- **Updating Submodules**: After adding a submodule, you can update it to the latest commit using:

  ```
  git submodule update --remote
  ```

- **Initializing Submodules**: If you clone a repository that contains submodules, you need to initialize and update them with:

  ```
  git submodule update --init --recursive
  ```

This command ensures that all submodules are properly set up and synchronized with the parent repository.

Using submodules effectively allows you to manage external dependencies within your projects while keeping them organized and version-controlled.

