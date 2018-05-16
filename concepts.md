 # Concepts d'Universal Dashboard

Universal Dashboard est un module PowerShell qui crée un serveur Web et le site Web associé qui se base sur les scripts que vous écrivez. Vous définissez l'interface cliente ainsi que les scripts côté serveur qui s'exécuteront lors du chargement du tableau de bord. Ces derniers fourniront les données à l'interface présentée à l'utilisateur. 
Comme tout est écrit en PowerShell, vous avez accès à toutes les fonctionnalités et modules que PowerShell apporte.

## Tableaux de bords

![](/assets/dashboards.png)

Les tableaux de bords représentent l'élément de départ dans Universal Dashboard. Un tableau de bord est composé d'une ou plusieurs pages, lesquelles sont composées à leur tour d'un certain nombre de composants. Un tableau de bord se comporte comme un serveur Web autonome qui s'exécute sur le port de votre choix. Il est possible d'exécuter plusieurs tableaux de bords sur une même machine dans la mesure où ils écoutent sur des ports différents.

## Composants

![](/assets/new-monitor-example-chart.png)

Un tableau de bord est constitué de plusieurs composants. Il existe des composants pour la mise en page, des composants graphiques (courbes, histogrammes, etc.), des composants de formulaires, etc. Chaque composant peut avoir différentes formes selon qu'il se trouve sur une page côté client ou s'il s'exécute côté serveur. Vous pouvez également définir des propriétés statiques telles que du texte ou des couleurs mais vous pouvez aussi des collecter ou générer des données à intervales de temps régulier qui seront fournies aux composants graphiques dans le but de produire un affichage dynamique. 

## Points de terminaisons (Endpoints) [Endpoints](/endpoints.md)

```
New-UDMonitor -Title "Downloads per second" -Type Line -Endpoint {
    Get-Random -Minimum 0 -Maximum 10 | Out-UDMonitorData
}
```

Un point de terminaison est un bloc de scripts PowerShell qui s'exécute à l'intérieur du serveur Universal Dashboard. Les composants qui implémentent le paramètre -Endpoint exécutent le bloc de script côté serveur et renvoient les données au client lorsque nécessaire. Les points de terminaisons sont hébergés en tant que "runspace pool" isolés; ils ne partagent donc pas le même environnement d'exécution de la session PowerShell qui a démarré le tableau de bord. Il est possible d'utiliser les fonctionnalités offertes par le paramètre -EndpointInitializationScript pour charger des modules et des fonctions dans les Endpoints.

## Pages

![](/assets/hamburger-menu.png)

Un tableau de bord peut être constitué de plusieurs pages. Ces dernières peuvent être accédées via un lien, un menu, une URL ou bien via une entrée dynamique. Il existe deux types de pages : statique ou dynamique. Les pages statiques affichent le contenu qui a été défini dans le tableau de bord. Les pages dynamiques quant à elles sont créées à chaque fois qu'elles sont appellées. Elles ont en outre accès aux différents segments de l'URL qui les appelle. A noter que l'URL peut aussi être créée dynamiquement.

## Page de login
![](/assets/login-page.png)

L'authentification et l'autorisation d'accès à un tableau de bord sont définis par l'intermédiaire d'une page de login. Universal Dashboard supporte la plupart des fournisseurs OData tels que Microsoft, Google et Twitter ainsi que l'authentification par formulaire simple. L'authentification par formulaire fournit en retour le nom de l'utilisateur et son mot de passe; le développeur est donc libre d'authentifier l'utilisateur avec le mécanisme de son choix.

## APIs REST

Etant donné qu'Universal Dashboard est un simple serveur Web, il peut aussi se comporter comme une API REST. La commande `New-UDEndpoint` peut être associée soit avec `Start-UDDashboard` ou `Start-UDRestApi` pour définir un service REST qui sera utilisable à partir de tout service compatible HTTP. Lorsque vous utilisez `Start-UDDashboard`, vous avez à la fois un service REST et un site Web qui s'exécutent simultanément sur le même port.
