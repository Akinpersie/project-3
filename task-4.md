### Task 4: Enforce Security Best Practices
- Scenario: With distributed teams, securing the source code repository is critical. You need to enforce security measures that ensure that sensitive data is protected and unauthorized changes cannot be made to the codebase.
- Implement security best practices in Git, including setting up user access controls, managing SSH keys, enforcing branch protection, and using signed commits for critical code changes.

- Ensure that there is a mechanism for auditing changes, so all code changes can be tracked and verified.

- Deliverable: Set up security best practices in your Git repository. Document how you configured access controls, enabled branch protection, and enforced commit signing. Explain how this ensures the security and integrity of the codebase.

- Security Best Practices for Git Repositories
    - Configure Access Controls: Access control ensures that only authorized users can access and modify your codebase. Follow these steps to configure access controls:
        -  Create Teams and Roles:
            - Organize your contributors into teams based on their responsibilities.
            - Assign roles with appropriate permissions to each team (e.g., Admin, Maintainer, Developer).
        - Set Repository Permissions
            - Navigate to the repository settings.
            - Under the "Manage Access" section, invite users or teams and assign them roles (e.g., Write, Read, Admin).
        - Enable Two-Factor Authentication (2FA):
            - Require all users to enable 2FA for their accounts to add an extra layer of security.
    - Enable Branch Protection
        - Branch protection rules ensure that only specific conditions are met before changes can be merged into important branches like <code>main</code> or <code>master</code>. follow these steps: 
            - Set Up Branch Protection Rules:
                -  Go to the repository settings and select "Branches."
                - Click on "Add rule" and specify the branch name pattern (e.g.,<code>main</code>)
            - Configure Protection Options:
                - Require pull request reviews before merging.
                - Require status checks to pass before merging
                - Require signed commits.
                - Restrict who can push to the branch.

    - Enforce Commit Signing
        - Commit signing ensures the authenticity of the code changes by verifying the identity of the committer. Follow these steps to enforce commit signing:
            - Generate a GPG Key:
            - Add GPG Key to GitHub Account:
                - Go to your GitHub account settings and navigate to "SSH and GPG keys."
                - Add your generated GPG key.
            - Configure Git to Sign Commits: Run the following commands in your terminal:

                - > <code>git config --global user.signingkey YOUR_GPG_KEY_ID
                git config --global commit.gpgSign true
    
- How This Ensures Security and Integrity
    + Access Controls: By controlling who can access and modify the repository, you minimize the risk of unauthorized changes and data breaches.
    + Branch Protection: Branch protection rules ensure that code changes are thoroughly reviewed and tested before being merged, maintaining the quality and stability of the codebase.
    + Commit Signing: Signed commits verify the identity of contributors, preventing malicious actors from impersonating legitimate contributors and ensuring the authenticity of the code changes.
