# Set Up the Development Environment

## Audience

This topic is for entry-level developers who want to run and test the Sport Comment Web Application locally.

## Purpose

Setting up the development environment allows you to run, test, and debug the application on your local machine before making changes or deploying updates.

## Prerequisites

Before you begin, make sure you have the following:

- Node.js (LTS version) installed
- A code editor such as Visual Studio Code
- A Google Cloud account for external sports API access
- A Firebase account for database visualization and authentication
- Access to the project repository on GitHub

To verify that Node.js is installed, run:

```bash
node -v
```
# Set Up the Development Environment

## Steps

```bash
# Step 1: Clone the repository
git clone <repository-url>

# Step 2: Navigate to the project folder
cd <project-folder-name>

# Step 3: Open the project in your editor
code .

# Step 4: Install project dependencies
npm install

# Step 5: Create a local environment configuration file
touch .env.local

# Example configuration for .env.local
SPORTSDATAIO_KEY=your_api_key
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_PRIVATE_KEY=your_private_key
FIREBASE_CLIENT_EMAIL=your_client_email

# Do not commit .env.local to GitHub.

# Step 6: Verify setup
# Check that the following exists in the project directory
node_modules/
.env.local
package.json
```

## Result

If setup is successful:

- Dependencies install without errors
- The `node_modules` folder appears
- Environment variables are configured
- The application is ready to run locally
