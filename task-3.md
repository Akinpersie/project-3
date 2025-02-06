## Task 3: Automate Code Quality and Deployment
### CI/CD Integration: To ensure code quality and rapid iteration, the team wants to integrate Git with a Continuous Integration/Continuous Deployment (CI/CD) pipeline. You are tasked with setting up automated tests that run every time a new feature branch is pushed.
### Use tools Using GitHub Actions to set up the pipeline. Ensure that the pipeline automatically runs unit tests, checks for code quality, and deploys changes to a staging environment when they pass.

### Deliverable: Implement a CI/CD pipeline using Git integration. Provide documentation that explains how the pipeline works, how to trigger tests, and how to deploy new code.

- Set up the Git Repository
    - First, ensure that your code is stored in a Git repository. If you don't have a repository, create one on a platform like GitHub.
    - configure the ci/cd tool
    - create a <code>.github</code> directory
    > <code>mkdir -p .github/workflows</code>

    - create a workfile:
    inside the <code>.github/workflows</code> directory, create a file named <code>ci-cd-pipeline.yml</code>

 > name: CI/CD Pipeline

    on:
    push:
    branches:
     - main
 
    pull_request:
    branches:
     - main

    jobs:
    build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test

      - name: Build the project
        run: npm run build

        deploy:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Deploy to server
        run: |
          ssh user@server 'bash -s' < deploy.sh

- Explanation
    - Name: The name of the workflow
    - on: Defines the events that trigger the workflow, such as pushing code or creating a pull request.
    - jobs: Defines the tasks to perform.
    - build: This job installs dependencies, runs tests, and builds the project.
    - deploy: This job deploys the code to the server.
- Triggering Test
Tests are automatically triggered when you push new code or create a pull request on the main branch. The npm test command runs the test suite.
- Deploying New Code: After the tests pass and the code is built, thr deploy job is triggered. you can customize the <code>deploy.sh</code> script to dep;oy your code to the server.
- Deployment Script (<code>deploy.sh</code>): create a <code>deploy.sh</code> script with the following contents.

>  <code>bin/bash</code>

    # Pull latest code
    cd /path/to/your/project
    git pull origin main

    # Install dependencies and restart the service
    npm install
    npm run build
    pm2 restart your-app-name

+  Documentation 
    + How the pipeline works:
        + The pipeline is triggered on code push or pull request.
        + It checks out the code, sets up the environment, installs dependencies, runs tests, builds the project, and deploys the code.
    + How to trigger tests:
        + Tests are automatically triggered on code push or pull request to the main branch.
    + How to deploy new code:
        + Deployment is part of the CI/CD pipeline and is automatically triggered after the build job completes successfully. The deploy.sh script handles the deployment process.