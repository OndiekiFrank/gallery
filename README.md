# Milestone 1: Set up

## Instructions

1. **Fork and Clone**: Fork and clone the repository to your local machine.

   ```bash
   git clone https://github.com/your-username/repository-name.git
2. Update _config.js: Update the _config.js file with your MongoDB Atlas connection details.

3. Commit and Push: Commit and push the changes to your forked repository.

# Milestone 2: Basic Pipeline

This repository currently lacks tests, but we'll build our pipeline to automate the testing and deployment process.

### JenkinsFile Setup
- Make sure you have a JenkinsFile in your repository with the required instructions.
- The pipeline should trigger automatically whenever you push a new change to your repository.

### Pipeline Configuration
1. **Ensure Required Software**: 
   - Identify the required software for your project. This may include Node.js, npm packages, and any other dependencies.
   - Use `npm install` in your pipeline to ensure all required Node.js dependencies are installed.

2. **Deployment to Render**:
   - Configure the pipeline to deploy to Render. You can start the server using `node server`.

3. **Modify Landing Page**:
   - Make a change to the landing page of your website.
   - Add a big "MILESTONE 2" to the site to ensure it's clearly visible.

4. **Push Changes**:
   - Push all your changes to the repository.

5. **Verify Deployment**:
   - Check the website deployed via Render to ensure that it displays "MILESTONE 2" prominently on the landing page.

 # MILESTONE 3 

## Introduction

This repository contains the source code for the project "Darkroom". Darkroom is a web application for managing photos.

## Testing

### Running Tests Locally

1. Make sure you have switched to the `test` branch.
2. Run `npm install` to install dependencies.
3. Run `npm test` to execute the tests.

### Expected Test Results

After running the tests locally, you should see test results similar to the screenshot provided (`darkroom_test.png`).

## Jenkins Pipeline Integration

1. Merge the `test` branch with the `main` branch.
2. Update the `Jenkinsfile` to include the execution of tests in the pipeline.
3. If the tests fail during the pipeline execution, an email notification will be sent.

## Website Changes

1. Make a change to the landing page of the website.
2. Add a big "MILESTONE 3" to the site to indicate the milestone.
3. Ensure that the website visible through Render shows both "MILESTONE 2" and "MILESTONE 3".

# Milestone 4 

## Introduction

This repository contains the source code for the project "Darkroom". Darkroom is a web application for managing photos.

## Slack Integration with Jenkins

### Setting Up Slack Integration

1. Follow the instructions at [Slack Integration Documentation](https://slack.com/intl/en-ke/help/articles/115005265063-Integrate-Jenkins-with-Slack) to integrate Jenkins with Slack.
2. Create a Slack channel called `YourFirstName_IP1` and invite your TM to it.

### Updating Jenkins Pipeline

1. Update your Jenkins pipeline to send a Slack message on successful deploy.
2. The message should include the build ID and the link to Render where the site is uploaded.
3. Utilize environment variables to include dynamic information in the message.

## Website Changes

1. Make a change to the landing page of the website.
2. Add a big "MILESTONE 3" to the site to indicate the milestone.
3. Push all your changes to the repository.
4. Ensure that the website visible through Render shows "MILESTONE 2", "MILESTONE 3", and "MILESTONE 4".




