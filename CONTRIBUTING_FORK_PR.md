# Contributing to Other Repositories: Fork & Pull Request Workflow

When you want to contribute to a project on GitHub that you don't have direct push access to (which is most open-source projects or projects owned by others), the standard workflow is to "Fork" the repository, make your changes in your fork, and then submit a "Pull Request" (PR) to the original (often called "upstream") repository.

This process allows project maintainers to review your proposed changes before merging them into their codebase.

Here's a step-by-step guide:

## 1. Fork the Repository

*   **Navigate to the Original Repository:** Go to the GitHub page of the project you want to contribute to (the "upstream" repository).
*   **Click the "Fork" Button:** In the top-right corner of the repository page, you'll see a "Fork" button, often with a number next to it representing how many times the project has been forked. Click it.
*   **Choose Where to Fork:** GitHub will ask you where you want to fork the repository. This will typically be your own GitHub account. If you're part of organizations, you might have other options. Select your account.

GitHub will then create a copy of the entire repository (including all files, branches, and commit history) under your account. This is your personal fork (e.g., `github.com/YourUsername/original-repo-name`). You have full administrative rights to your fork.

## 2. Clone Your Fork to Your Local Machine

Now that you have a fork on your GitHub account, you need to clone *your fork* (not the original repository) to your local machine to make changes.

*   **Go to Your Fork on GitHub:** Navigate to the page of your forked repository on GitHub.
*   **Get the Clone URL:** Click the green "< > Code" button and copy the HTTPS or SSH URL for *your fork*.
*   **Clone it:** Open your terminal or Git Bash and use the `git clone` command:
    ```bash
    git clone <URL_of_your_fork>
    # Example:
    # git clone https://github.com/YourUsername/original-repo-name.git
    ```
*   **Navigate into the directory:**
    ```bash
    cd original-repo-name
    ```

## 3. Configure a Remote for the Original ("Upstream") Repository (Optional but Recommended)

To keep your fork updated with changes from the original project, it's good practice to add the original repository as a remote. This remote is conventionally named `upstream`.

*   **Get the Original Repository URL:** Go to the GitHub page of the *original* (upstream) repository and copy its clone URL (HTTPS or SSH).
*   **Add the Upstream Remote:** In your terminal, inside your cloned fork's directory, run:
    ```bash
    git remote add upstream <URL_of_the_original_repository>
    # Example:
    # git remote add upstream https://github.com/OriginalOwner/original-repo-name.git
    ```
*   **Verify Remotes:** You can check your configured remotes:
    ```bash
    git remote -v
    ```
    You should see `origin` (pointing to your fork) and `upstream` (pointing to the original repository).

## 4. Create a New Branch for Your Changes

Before making any changes, it's crucial to create a new branch. This isolates your work and makes it easier to manage multiple contributions or update your PR later.

*   **Ensure Your Main Branch is Up-to-Date (Optional, but good practice):**
    If you added the `upstream` remote, you can update your local `main` branch (or whatever the default branch is) from the original repository:
    ```bash
    git checkout main  # Or your default branch name
    git fetch upstream
    git merge upstream/main # Or upstream/master, or the original repo's default branch
    git push origin main # Update your fork's main branch on GitHub
    ```
*   **Create and Switch to a New Branch:**
    Choose a descriptive name for your branch (e.g., `fix-typo-in-readme`, `add-new-feature-x`).
    ```bash
    git checkout -b your-descriptive-branch-name
    # Example:
    # git checkout -b fix-readme-typo
    ```
    This command creates the new branch and immediately switches you to it.

## 5. Make Your Changes

Now, work on the code! Use your text editor or IDE to make the desired changes to the files in your local repository (which is on your new branch).

## 6. Commit Your Changes

Once you're happy with your modifications, stage and commit them with clear commit messages.

*   **Stage changes:**
    ```bash
    git add .  # Or specify individual files
    ```
*   **Commit changes:**
    ```bash
    git commit -m "Your descriptive commit message for the changes"
    # Example:
    # git commit -m "Fix typo in README installation section"
    ```
    You can make multiple commits to your branch if needed.

## 7. Push Your Changes to Your Fork on GitHub

Push your new branch (with your commits) from your local machine to *your fork* on GitHub.

```bash
git push origin your-descriptive-branch-name
# Example:
# git push origin fix-readme-typo
```
If it's the first time pushing this branch, you might use `git push --set-upstream origin your-descriptive-branch-name`.

## 8. Open a Pull Request (PR)

This is where you propose your changes to the original repository.

*   **Go to Your Fork on GitHub:** Navigate to your forked repository on GitHub.
*   **GitHub often prompts you:** If you've recently pushed a new branch to your fork, GitHub will usually display a prominent banner with a "Compare & pull request" button for that branch. Click it.
*   **Alternatively, go to the "Pull requests" tab:**
    *   Go to the original (upstream) repository on GitHub.
    *   Click on the "Pull requests" tab.
    *   Click the "New pull request" button.
*   **Configure the Pull Request:**
    *   **Base Repository and Branch:** GitHub will try to automatically select the original repository and its default branch (e.g., `main` or `master`) as the `base` repository. This is where you want your changes to be merged.
    *   **Head Repository and Branch:** Select your fork (`YourUsername/original-repo-name`) as the `head repository` and choose the branch you just pushed (e.g., `fix-readme-typo`) as the `compare` branch. This is the branch containing your changes.
    *   **Review Changes:** GitHub will show you a diff of the changes between the base branch and your compare branch. Make sure these are the changes you intend to submit.
    *   **Title and Description:**
        *   Write a clear and concise **title** for your Pull Request (e.g., "Fix typo in README installation section").
        *   Provide a detailed **description** of the changes you made, why you made them, and any relevant context. If your PR addresses a specific issue, link to it (e.g., "Closes #123").
    *   **Allow edits by maintainers:** There's usually a checkbox that allows maintainers of the upstream repository to make changes to your PR branch. This can be helpful for them to make small fixes or updates. It's generally good to leave this checked.

*   **Click "Create pull request".**

## 9. Discussion and Review

Once the PR is open:

*   **Automated Checks:** The project might have automated checks (CI/CD) that run against your PR. Make sure these pass.
*   **Code Review:** Project maintainers and other contributors may review your code, ask questions, and suggest further changes.
*   **Make Further Changes (if needed):** If you need to make more changes based on feedback:
    1.  Make the changes on your local branch (e.g., `fix-readme-typo`).
    2.  Stage and commit them locally: `git add .`, `git commit -m "Incorporate feedback"`.
    3.  Push the new commits to the same branch on your fork: `git push origin fix-readme-typo`.
    The Pull Request on GitHub will automatically update with your new commits.
*   **Be Responsive:** Engage in the discussion and respond to feedback.

## 10. PR Merged or Closed

*   **Merged:** If the maintainers are happy with your contribution, they will merge your Pull Request into the original repository! Your changes are now part of the project.
*   **Closed:** Sometimes PRs are closed without merging if they are not aligned with the project's goals or have other issues.

Congratulations! You've successfully contributed to another project using the fork and pull request workflow. Remember to delete your feature branch from your fork after the PR is merged (you can do this via GitHub or locally with `git branch -d branch-name` and `git push origin --delete branch-name`). You can also sync your fork's main branch with the upstream repository to keep it up-to-date for future contributions.
