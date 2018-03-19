# Running Dashboards in Azure

To host a dashboard in Azure, you will need to deploy the entire module to your WebApp.

## Manually creating an Azure WebApp

First, create an Azure WebApp.

In the Azure Portal, click New, search for Web App and click Create.![](/assets/azure-web-app.png)Enter your Web App's name, select the subscription and resource group.

![](/assets/azure-create-new-webapp.png)

Once provisioned, go to the WebApp's blade and retrieve the FTP hostname and username.

![](/assets/azure-ftp-username.png)Next, define deployment credentials for the app.

![](/assets/azure-deployment-credentials.png)

Navigate to the wwwroot directory on the FTP server for your website.

![](/assets/ftp-website.png)

Copy the entire contents of the PowerShell Universal Dashboard module to the wwwsite directory.

![](/assets/azure-copy-files.png)

Create a `dashboard.ps1` file that contains `Start-UDDashboard` with the `-Wait` parameter.

```
Start-UDDashboard -Wait -Dashboard (
    New-UDDashboard -Title "Hello, Azure" -Content {
        New-UDCard -Title "Hello, Azure"
    }
)
```

Copy the `dashboard.ps1` file to your `wwwsite` directory.

![](/assets/finished-site-dir.png)

Now you should be able to navigate to your WebApp. When ever you need to update your dashboard, you can stop your WebApp and upload a new `dashboard.ps1`.

![](/assets/hello-azure.png)

## Licensing

The license should be named license.lic and also placed in net451. This will ensure that the license is persistent throughout restarts.

![](/assets/iis-license)

