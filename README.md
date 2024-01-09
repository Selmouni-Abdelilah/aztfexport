# Azure Terraform Export Tool :)

This Jenkins pipeline automates the process of exporting Azure resources using Aztfexport and generating a Terraform plan for a specific resource group.

## Pipeline Overview

This pipeline consists of the following stages:

1. **Checkout:**
   - Checks out the source code from the GitHub repository (`https://github.com/Selmouni-Abdelilah/aztfexport`).
   - Specifically targets the 'main' branch.

2. **Azure Login:**
   - Logs into Azure using the specified Azure service principal credentials.
   - Ensures that the Azure CLI is authenticated for subsequent operations.

3. **Using Aztfexport:**
   - Creates a 'Terraform' directory to store Terraform-related files.
   - Utilizes the Aztfexport tool to query and export Azure resources.
   - Specifically targets resources within the '011-task-rg' resource group, filtering for Microsoft.Web and Microsoft.Logic types.
   - Generates a Terraform plan based on the exported resources.

## Prerequisites

Before running this pipeline, ensure the following prerequisites are met:

- **Jenkins Setup:** Make sure Jenkins is properly configured with necessary plugins.
- **GitHub Credentials:** Ensure Jenkins has credentials (`GitHubcredentials`) to access the GitHub repository.
- **Azure Service Principal:** Set up Azure service principal credentials (`Azure_credentials`) with appropriate permissions.
- **Aztfexport:** Ensure that Aztfexport is installed on the Jenkins agent where this pipeline will run.

## Pipeline Execution

1. **Clone Repository:**
   - Ensure Jenkins has the necessary permissions to access the GitHub repository.
   - The pipeline will automatically check out the 'main' branch.

2. **Azure Login:**
   - Uses Azure service principal credentials to authenticate the Azure CLI.

3. **Using Aztfexport:**
   - Creates a 'Terraform' directory.
   - Executes Aztfexport to query and export Azure resources.
   - Generates a Terraform plan for further review.

## Notes and Customization

- Customize the `url` in the 'Checkout' stage to match your GitHub repository.
- Modify the `credentialsId` and `url` in the 'Azure login' stage with appropriate Azure service principal credentials.
- Adjust the resource group and resource types in the 'Using Aztfexport' stage according to your requirements.

Feel free to enhance or modify this pipeline based on your specific needs. Happy automating!
