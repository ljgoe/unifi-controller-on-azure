# UniFi on Azure 

This is a ready to deploy Unifi controller for Azure. This will install unify using docker

#### Using docker build on Azure from the following source: 
1. [Jacob Alberty](https://github.com/jacobalberty/unifi-docker)
2. [Docker image](https://hub.docker.com/r/jacobalberty/unifi)


The Unifi controllers run's as a Container Instance in Azure and uses a Azure file share to store it's configuration data.

## Deployment
Azure provides us with multiple ways to deploy resource. Using [ARM templates](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/) works best for the resources we need.

## Deploy to Azure
If you like to deploy it directly to Azure, please use the link below. This will create the storage account, docker image, an link the two together.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https://raw.githubusercontent.com/ljgoe/unifi-controller-on-azure/master/azuredeploy.json)

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

If you receive a 404 error after the deployment please be patient. The controller is still setting itself up and needs a few minutes. :-)


## External Links
[Jacob Alberty's Docker image for the Unifi Controller.](https://github.com/jacobalberty/unifi-docker)

[Microsoft Doc's page for the az container command.](https://docs.microsoft.com/en-us/cli/azure/container?view=azure-cli-latest)

[Microsoft Doc's page for mounting an Azure file share inside a Container Instance.](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-volume-azure-files)
