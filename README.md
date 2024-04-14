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

