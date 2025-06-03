# Making Changes, Committing, and Pushing to GitHub

Once you have a local Git repository (either by cloning an existing one or initializing a new one with `git init`), the typical workflow for saving your changes and sharing them with a remote repository (like one on GitHub) involves a three-step process: **Add**, **Commit**, and **Push**.

This cycle ensures that you have control over what changes are saved and when they are shared.

## Prerequisites:

*   **Git Installed and Configured:** Ensure Git is installed and your `user.name` and `user.email` are configured.
*   **Local Repository:** You should be working within a Git repository on your local machine. Use the `cd` command in your terminal to navigate to your project's root directory (the one containing the `.git` hidden folder).
*   **Remote Repository (for pushing):** To push changes, your local repository needs to be connected to a remote repository (e.g., on GitHub). If you cloned the repository, this connection (usually named `origin`) is already set up.

## The Add, Commit, Push Cycle

Here's a breakdown of each step:

### 1. Make Changes to Your Files

First, you'll make the necessary modifications to your project files using your preferred text editor or IDE. This could involve:

*   Writing new code.
*   Modifying existing code.
*   Deleting files or parts of files.
*   Adding new files.

Let's say you've edited `README.md` and created a new file `new_feature.py`.

### 2. Stage Changes (`git add`)

After making changes, you need to tell Git which of those changes you want to include in your next **commit**. This is called "staging."

*   **Stage specific files:**
    If you want to stage only particular files, you list them:
    ```bash
    git add README.md
    git add new_feature.py
    ```

*   **Stage all changes in the current directory and subdirectories:**
    To stage all modified and new files in your project's directory (from your current location downwards), the most common command is:
    ```bash
    git add .
    ```
    The `.` refers to the current directory.

*   **Stage all changes in the entire repository:**
    To stage all tracked files (modified or deleted) and untracked files (new) throughout the entire repository, regardless of your current directory within the repo:
    ```bash
    git add -A
    # or
    git add --all
    ```

**Why stage?** Staging allows you to selectively group related changes into a single commit. You might make many edits, but only want to group a subset of them into a logical snapshot.

**Check Status:** At any point, you can see the status of your files (what's modified, what's staged, what's untracked) using:
```bash
git status
```
Files listed under "Changes to be committed" are staged. Files under "Changes not staged for commit" or "Untracked files" are not.

### 3. Commit Changes (`git commit`)

Once you've staged the desired changes, you "commit" them. A commit is like taking a snapshot of your staged changes. Each commit has a unique ID and is accompanied by a commit message that describes the changes made.

The command is:
```bash
git commit -m "Your descriptive commit message"
```

*   `-m "Your descriptive commit message"`: The `-m` flag allows you to provide a commit message directly on the command line.
*   **Writing Good Commit Messages:**
    *   Keep them concise but descriptive.
    *   Use the present tense (e.g., "Add login feature" instead of "Added login feature").
    *   Explain *what* the commit does and *why* it was made, if necessary.
    *   If it's a more complex change, you can omit `-m` and Git will open your configured text editor for you to write a longer message.

**Example:**
```bash
git commit -m "Add initial version of new_feature.py and update README"
```

After committing, your changes are safely recorded in your *local* repository's history. They are not yet on the remote server (GitHub).

### 4. Push Changes to GitHub (`git push`)

The final step is to "push" your local commits to the remote repository on GitHub. This shares your changes with others (if it's a collaborative project) and backs them up on the server.

The command is typically:
```bash
git push
```

However, it's more explicit and often safer to specify the remote and the branch you're pushing to:

```bash
git push <remote_name> <branch_name>
```

*   `<remote_name>`: This is usually `origin` by default if you cloned the repository or added a remote named `origin`.
*   `<branch_name>`: This is the name of the branch you are currently working on and want to push (e.g., `main`, `develop`, `feature-branch`).

**Example (most common scenario):**
If you are on the `main` branch and your remote is `origin`:
```bash
git push origin main
```

**First Push for a New Branch:**
If you created a new branch locally and are pushing it for the first time, Git might instruct you to set an "upstream" tracking relationship. The command often looks like this:
```bash
git push --set-upstream origin your-new-branch-name
# or the shorthand:
git push -u origin your-new-branch-name
```
After this initial push for the new branch, subsequent pushes from that branch can usually just use `git push`.

**What happens during `git push`?**
Git uploads your committed changes to the specified remote branch. If other people have pushed changes to that same branch since your last `git pull`, Git might reject your push and ask you to first pull the latest changes, merge them, and then try pushing again.

## Summary of Commands:

1.  **Make your changes** (edit, add, delete files).
2.  **Stage them:**
    ```bash
    git add .  # Or list specific files
    ```
3.  **Commit them:**
    ```bash
    git commit -m "Your commit message"
    ```
4.  **Push them to the remote repository:**
    ```bash
    git push origin <branch-name> # e.g., git push origin main
    ```

Repeat this cycle as you work on your project. Regular commits help you track progress and make it easier to revert changes if something goes wrong. Pushing ensures your work is backed up and shared if needed.
