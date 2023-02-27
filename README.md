# SA-MP Server Workflow with Ngrok

This GitHub Actions workflow sets up an SA-MP server and exposes it to the internet using Ngrok.

## Usage

1. Fork this repository
2. Create an account on [ngrok.com](https://ngrok.com/) and get an auth token
3. Go to the "Settings" tab of your forked repository and add the following secrets:
    - `NGROK_AUTH_TOKEN`: Your Ngrok auth token
    - `GIT_USERNAME`: Your GitHub username
    - `GIT_PAT`: A [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) with permission to push to your forked repository
4. Modify `samp03svr/server.cfg` to your liking
5. Commit and push the changes to your forked repository
6. Go to the "Actions" tab of your forked repository and click the "SA-MP Server Workflow with Ngrok" workflow
7. Click the "Run workflow" button
8. Wait for the workflow to finish running (this may take a while)

## Workflow

This workflow consists of three jobs:

- `install-ngrok`: Downloads and installs Ngrok
- `samp-server`: Starts the SA-MP server and exposes it to the internet using Ngrok
- `save-and-push`: Saves any changes made during the workflow and pushes them to the forked repository

## Workflow Configuration

The workflow is triggered by a `workflow_dispatch` event on the `main` branch of the repository. You can also trigger the workflow manually from the "Actions" tab of your forked repository.

The workflow uses the `ubuntu-latest` runner.

The `samp-server` job requires the following environment variables to be set:

- `NGROK_AUTH_TOKEN`: Your Ngrok auth token
- `GIT_PAT`: A personal access token with permission to push to your forked repository

The `samp-server` job performs the following steps:

1. Checks out the repository
2. Downloads and installs Ngrok
3. Starts Ngrok and exposes port 7777 on the internet
4. Gets the public URL of the Ngrok tunnel
5. Starts the SA-MP server with the Ngrok URL as the server IP
6. Runs the SA-MP server for 2 hours
7. Stops the SA-MP server and Ngrok

The `save-and-push` job performs the following steps:

1. Checks out the repository
2. Saves any changes made during the workflow
3. Commits and pushes the changes to the forked repository

The workflow uses Ubuntu as the operating system for the jobs, so you will need to ensure that your SA:MP server files are compatible with Ubuntu.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
