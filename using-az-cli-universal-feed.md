Azure Artifacts allows you to host and share packages, such as NuGet, npm, Maven, and Python packages, within your organization. To set up a universal feed using Azure Artifacts and manage it via PowerShell and Azure CLI, follow these steps:

### Prerequisites:

1. Install Azure CLI: [https://docs.microsoft.com/en-us/cli/azure/install-azure-cli](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)
2. Install Azure DevOps extension for Azure CLI:

   `az extension add --name azure-devops`

3. Log in to Azure CLI:

   `az login`

4. Connect to your Azure DevOps organization:

   `az devops configure --defaults organization=https://dev.azure.com/YourOrganizationName`

### Steps to Create Universal Feed:

1. **Set up the default project**: Replace `YourProjectName` with the name of your Azure DevOps project.

   `az devops configure --defaults project=YourProjectName`

2. **Create a new universal feed**: Replace `YourFeedName` with the desired name of your feed.

   `az artifacts universal create-feed --feed YourFeedName`

3. **Publish packages to the feed**: Assuming you already have a universal package to publish, use the following commands to do so:

   a. **Publish a universal package**: Replace `<path_to_package>` with the path to your universal package and `<version>` with the version of your package.

   `az artifacts universal publish --feed YourFeedName --name PackageName --version <version> --description "Package Description" --path <path_to_package>`

4. **Install and use packages**: To consume the packages, you would need to install the `AzureArtifacts` tool and connect to the feed. Remember to set up authentication to access the feed, if required.
5. **Delete a universal feed (Optional)**: If you ever need to delete the feed you created:

   `az artifacts universal delete-feed --feed YourFeedName --yes`

### Tips:

- Always ensure you have the required permissions to create or manage feeds in Azure DevOps.
- Set up proper authentication if you're working in a secured environment. This can include personal access tokens (PATs) or other authentication mechanisms supported by Azure DevOps.
