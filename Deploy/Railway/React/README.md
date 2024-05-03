
# Deploying to Railway


Fullstack Pokemon API deployment on railway Paas

Considerations:

    .-Use Node.js version 16.
    .-If the build script doesn't work locally, use "NODE_OPTIONS=--openssl-legacy-provider" as shown in step 9.

## Steps

    1.-Fork and clone the project from https://github.com/JuanPa90Cap/ci-test.git into our GitHub repository, then locally.

    2.-Navigate to the project path in a new terminal and try deploying locally. Install all dependencies with "npm i", then run "npm eslint" (if your code is messy, you can clean it with the eslint command), followed by "npm run build", and "npm run start".

    3.-By default, the application runs on port 5000 on localhost. The Express framework serves the static files in a development server. This is important because Railway only serves applications and does not serve static files.

    4.-If everything is correct, you can proceed to the next steps.

    5.-Install the Railway CLI with "npm i -g @railway/cli", then log in to Railway with "railway login"; enter your credentials. After that, initialize the project with "railway init"; enter the project name and press Enter.

    6.-Go to the Railway website, log in, and open your recently created project. Once you are in the project, create a token in the settings. To build the workflow, you will need the project token and the service name.

    7.-The project has a /.github/workflows directory where you can find the pipeline.yml file to modify. Scroll to the bottom of the file to the 'deploy' section where you need to change some lines. (Refer to the example pipeline in this repository; you need to create a secret with the project token and replace it if you changed the name, and specify the service name because it varies according to the person). Action used: https://github.com/bervProject/railway-deploy.git

    8.-At the root directory, create the file "nixpacks.toml". This file contains the configuration to build the Nixpack application. Railway uses this builder to execute all the necessary commands for deployment. (You can view the structure of this file in this repository).

    9.-To build the application for deployment, Nixpacks defaults to using Node.js version 18. However, this can cause issues with OpenSSL (for more information, you can investigate). It is recommended to use Node.js version 16. To do this, change the Nixpacks configuration with the package.json file. Modify the development script build, and add "NODE_OPTIONS=--openssl-legacy-provider" as shown in the file in this repository.

    10.-Commit, push, and review the deployment.