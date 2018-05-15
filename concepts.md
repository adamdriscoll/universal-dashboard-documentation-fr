# Concepts d'Universal Dashboard

Universal Dashboard est un module PowerShell qui crée un serveur Web et le site Web associé qui se base sur les scripts que vous écrivez. Vous définissez l'interface cliente ainsi que les scripts côté serveur qui s'exécuteront lors du chargement du tableau de bord. Ces derniers fourniront les données à l'interface présentée à l'utilisateur. 
Comme tout est écrit en PowerShell, vous avez accès à toutes les fonctionnalités et modules que PowerShell apporte.

## Tableaux de bords

![](/assets/dashboards.png)

Les tableaux de bords représentent l'élément de départ dans Universal Dashboard. Un tableau de bord est composé d'une ou plusieurs pages, lesquelles sont composées à leur tour d'un certain nombre de composants. Un tableau de bord se comporte comme un serveur Web autonome qui s'exécute sur le port de votre choix. Il est possible d'exécuter plusieurs tableaux de bords sur une même machine dans la mesure où ils écoutent sur des ports différents.



## Les composants

![](/assets/new-monitor-example-chart.png)

Dashboards are made up of components. There are components for formatting, charts, input and more. Each component may translates to a different aspect of the client webpage as well as the server side endpoints. You can define properties like colors and text that are static as well as data for charts that is loaded dynamically on an interval.

Un tableau de bord est constitué de plusieurs composants. Il existe des composants pour la mise en page, des composants graphiques, des composants de formulaires, etc. Chaque composant peut avoir différentes formes selon qu'il se trouve sur une page côté client ou s'il s'exécute côté serveur. Vous pouvez également définir des propriétés statiques telles que du texte ou des couleurs mais vous pouvez aussi des collecter ou générer des données à intervales de temps régulier qui seront fournies aux composants graphiques dans le but de produire un affichage dynamique. 


## [Endpoints](/endpoints.md)

```
New-UDMonitor -Title "Downloads per second" -Type Line -Endpoint {
    Get-Random -Minimum 0 -Maximum 10 | Out-UDMonitorData
}
```

Endpoints are PowerShell script blocks that run within the Universal Dashboard server. Components that support server-side data have Endpoint properties that are executed when data is requested by the client. Endpoints are hosted as part of an isolated runspace pool and not in the same execution environment as the PowerShell session that started the dashboard. You can use features such as the EndpointInitializationScript to load modules and functions into endpoints.

## Pages

![](/assets/hamburger-menu.png)

Dashboards can have multiple pages that can be viewed via links, the menu, URLs or through dynamic input. There are both static and dynamic pages. Static pages display content that has been defined in the dashboard. Dynamic pages are created whenever they are requested and have access to segments of the URL that may be dynamically defined. 

## Login Page

![](/assets/login-page.png)

Authentication and Authorization is defined via login page configuration. Universal Dashboard supports popular OData provides such as Microsoft, Google and Twitter as well as forms-based authentication. Forms authentication provides a script block with the username and password and the dashboard developer can use it to authenticate against whatever mechanism they wish. 

## REST APIs

Since Universal Dashboard is just a web server, it can also operate as a REST API. The `New-UDEndpoint` cmdlet can be paired with either `Start-UDDashboard` or `Start-UDRestApi` to define a RESTful service you can call from any HTTP compatible service. When using `Start-UDDashboard`, you will have both a website and a REST service running on the same port. 



