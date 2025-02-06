### Task 2: Implement Git Workflows for a Team Project
Scenario: Assume the team is developing a new web application. Developers need to work on multiple features simultaneously while maintaining a stable main branch.
Implement a Git workflow that supports the following:
Feature branching
Pull requests for code reviews
Integration testing before merging code into the main branch
Deliverable: Document a Git workflow guide for your team. Include branching strategies, how to handle pull requests, and best practices for merging and rebasing. Ensure that you describe how this workflow facilitates collaboration in a distributed team.
### Git Workflow Guide
-  Branching Strategy: Using a consistent branching strategy helps manage development efficiently. We will use Feature Branching and a variant of GitFlow:

Main Branch (<code>main</code>): This is the stable branch. Only merge changes that have passed all tests and code reviews.

Develop Branch (<code>develop</code>): This branch contains the latest delivered development changes for the next release.

Feature Branches: Create these for each feature or bug fixes. The naming convention could be <code>feature/feature-name</code> or bugfix/bug-description.

- Branching command example:


> <code>git checkout -b feature/feature-name</code>
- Pull Requests for Code Reviews
    - Creating a Pull Request:
        + When a feature or fix is complete, push your branch to the remote repository.
        > <code>git push origin feature/feature-name</code>
        + Create a pull request (PR) from your feature branch to the develop branch on your Git platform (e.g., GitHub).
    - Code Review:
        + Assign reviewers to your PR. Reviewers should provide feedback and request changes if necessary. Once approved, the PR can be merged.
    - Handling Pull Request Comments:
        + Address any feedback and commit changes to the same branch. This will update the PR automatically.
        > <code>git commit -m "Addressed review comments"

        > <code>git push origin feature/feature-name</code>

- Integration Testing
    - Continuous Integration (CI): Set up a CI pipeline to run automated tests on all branches. Common CI tools include Jenkins, Travis CI, CircleCI, GitHub Actions, and GitLab CI/CD.
    - Running Tests: Tests should run automatically when a PR is created or updated. Ensure that all tests pass before merging the code to the develop branch.
- Merging and Rebasing
    - Merging to Develop: Once the PR is approved and all tests pass, merge the feature branch into the develop branch.
    - Use the Squash and Merge option on the PR if your team prefers a cleaner commit history.
    - Rebasing Feature Branch: If the develop branch has updates, you may need to rebase your feature branch to include those changes.

    > <code>git fetch origin</code>

    > <code>git rebase origin/develop</code>
    - Merging to Main: Periodically, merge the develop branch into the main branch.
        + Ensure all integration tests pass before merging.
    
    > <code>git checkout main</code>

    > <code>git merge develop</code>

    > <code>git push origin main</code>

### Best Practices
- Commit Often: Make frequent, small commits with clear messages.
- Pull Frequently: Pull from the develop branch regularly to keep your branch up to date.
- Code Review: Provide constructive feedback and review code thoughtfully.
- Automate Tests: Ensure thorough test coverage and automate testing as much as possible.

### How This Workflow Facilitates Collaboration in a Distributed Team
- Clear Branching Strategy: Provides a clear structure for development and helps prevent conflicts.
- Code Reviews: Encourages collaboration and knowledge sharing among team members.
- Continuous Integration: Ensures that code is always tested and stable before merging.
- Communication: Regular updates through pull requests and reviews foster better communication and coordination.
 
 