# UniFi on Azure 
a\As a docker container

#### Introduction
This is a ready to deploy Unifi controller for Azure. This will install 

### The [Jacob Alberty](https://github.com/jacobalberty/unifi-docker) docker build on Azure. 
### (https://hub.docker.com/r/jacobalberty/unifi)
Almost no configuration is needed.
The Unifi controllers run's as a Container Instance in Azure and uses a Azure file share to store it's configuration data.

## Deployment
Azure provides us with multiple ways to deploy resource. Using [ARM templates](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/) works best for the resources we need.

#### Thing you need to do yourself
The deployment takes care of almost everything. There are still two things that need to be done by hand.
1. Add your own certificates to the file share in /unifi/cert.
2. Configure the controller itself. Either by restoring from an existing back-up. Or by following the wizard. That's up to you.

#### Accessing the controller
After the deployment is complete you need to find the containers IP.

![Container IP](https://raw.githubusercontent.com/Syndicate-Consulting/unifi-on-azure/master/images/docker%20ip.jpg?raw=true)

Browse to the web interface by navigating to https://*x.x.x.x*:8443

![Unifi Controller Webinterface](https://raw.githubusercontent.com/Syndicate-Consulting/unifi-on-azure/master/images/unifi%20web.jpg?raw=true)

And enjoy your new controller.

## Deploy from the Azure Marketplace
The solution is also available from the [Microsoft Azure Marketplace](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/syndicateconsulting1592598527633.offer2?tab=Overview). You can search for UniFi in the Azure portal and deploy the UniFi controller from there.
![Template](https://raw.githubusercontent.com/Syndicate-Consulting/unifi-on-azure/master/images/uoa%20marketplace.png?raw=true)

If you receive a 404 error after the deployment please be patient. The controller is still setting itself up and needs a few minutes. :-)

## Deploy to Azure
If you like to deploy it directly to Azure, please use the link below. This will create the storage account, docker image, an link the two together.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FSyndicate-Consulting%2Funifi-on-azure%2Fmaster%2Fazuredeploy.json) [![Visualize](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/visualizebutton.svg?sanitize=true)](http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FSyndicate-Consulting%2Funifi-on-azure%2Fmaster%2Fazuredeploy.json)

#### I’m lazy, can you make it easier for me
Sure, if you want to put a minimum amount of effort into this grab the *template.json* file from the [azure templates directory](https://github.com/Syndicate-Consulting/unifi-on-azure/tree/master/azure%20templates) and copy-paste the content into a new template file in Azure. Save it, and click deploy.

![Template](https://raw.githubusercontent.com/Syndicate-Consulting/unifi-on-azure/master/images/azure%20template.jpg?raw=true)

## Suggestions
If you have any comments of suggestions please feel free to [add them](https://github.com/Syndicate-Consulting/unifi-on-azure/issues).

Please keep in mind that Azure Container Instances are not available in all regions. You need to deploy the controller to a supported region.

## External Links
[Jacob Alberty's Docker image for the Unifi Controller.](https://github.com/jacobalberty/unifi-docker)

[Microsoft Doc's page for the az container command.](https://docs.microsoft.com/en-us/cli/azure/container?view=azure-cli-latest)

[Microsoft Doc's page for mounting an Azure file share inside a Container Instance.](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-volume-azure-files)
