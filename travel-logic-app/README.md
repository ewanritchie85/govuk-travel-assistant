
# Azure Logic App Directory

This directory contains all files related to the Azure Logic App integration for the Travel Assist AI project.

## Contents

- `logic-app.json`: The workflow definition for your Logic App. This file describes the triggers, actions, and flow of your automation.
- *(Optional)* `arm-template.json`: An Azure Resource Manager (ARM) template for deploying the Logic App and related resources in a repeatable, automated way.
- *(Optional)* `parameters.json`: Sample parameters for ARM template deployments.
- `README.md`: This documentation file.

## What is a Logic App Workflow vs. ARM Template?

- **Logic App Workflow JSON**: Contains only the workflow logic (triggers, actions, conditions). Useful for editing or importing/exporting workflows.
- **ARM Template**: A broader deployment file that wraps the workflow JSON and describes the Azure resource, its configuration, and dependencies. Use this for automated deployments.

## Deployment Instructions

### Manual Deployment
1. Go to the Azure Portal.
2. Create a new Logic App resource.
3. Import the contents of `logic-app.json` into the Logic App Designer.

### Automated Deployment (Recommended)
1. Use the ARM template (if provided) with Azure CLI or PowerShell:
	- Azure CLI: `az deployment group create --resource-group <your-group> --template-file arm-template.json --parameters @parameters.json`
2. Update parameters as needed for your environment.

## Security Notes

- **Do not commit secrets or credentials.** Use Azure Key Vault or environment variables for sensitive information.
- Provide only sample or template files for secrets (e.g., `env.example`).

## References

- [Azure Logic Apps Documentation](https://docs.microsoft.com/azure/logic-apps/)
- [ARM Templates Documentation](https://docs.microsoft.com/azure/azure-resource-manager/templates/)

## Contributing

Please update this README and add documentation for any new files or deployment steps.
