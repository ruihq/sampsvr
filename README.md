# SA:MP Server Workflow with Ngrok

This is a GitHub workflow that starts an SA:MP server and tunnels it using Ngrok. It then pushes any changes made during the session to the repository after the server has been running for 2 hours.

## Getting Started

To use this workflow, you will need to fork this repository to your own GitHub account. Once you have forked the repository, you will need to add the following secrets to your repository:

- `GIT_USERNAME`: Your GitHub username.
- `GIT_PASSWORD`: A personal access token or password that has permissions to push to the repository.
- `NGROK_AUTH_TOKEN`: Your Ngrok auth token.

You can create a personal access token on GitHub by going to your account settings and navigating to "Developer settings" > "Personal access tokens". You should generate a new token with "repo" permissions.

To add the secrets to your repository, navigate to the repository settings and select "Secrets" from the left-hand sidebar. Click the "New secret" button and enter the name and value for each of the three secrets.

## Workflow

The workflow is triggered when you push changes to the `main` branch of your repository. It consists of three jobs:

1. `install-ngrok`: This job installs Ngrok on the Ubuntu environment.
2. `samp-server`: This job starts the SA:MP server and tunnels it using Ngrok. The server runs for 2 hours before it is stopped and the changes are pushed to the repository.
3. `save-and-push`: This job pushes any changes made during the SA:MP session to the repository.

The workflow uses Ubuntu as the operating system for the jobs, so you will need to ensure that your SA:MP server files are compatible with Ubuntu.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
