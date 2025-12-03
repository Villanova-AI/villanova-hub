# Villanova Hub Bundle

## Overview
This is the parent repository for the Villanova Hub project which currently contains two deployable sub-projects
* `application` which has the MFEs and microservices for the Villanova Hub application
* `content` which has the non-compiled components such as pages, page templates, and fragments.

## Getting Started

### Deploy on Villanova App

Move inside one of the two folders `application` and `content`, which contain the bundles.<br/>
You can build,deploy and install the bundles on Villanova with commands of ent.

```
ent bundle pack
ent bundle publish
ent bundle deploy
ent bundle install
```

For more details check the readme of `application` and `content`.

## Configure Hub Registry in AppBuilder
This sections is useful to connect an existing Villanova Hub.
From AppBuilder menu, you select `Hub`. At the top right, select `Select Registry` and `New Registry`.

You can choose Name and configure the url endpoint.

* example endpoint value for localhost:

```
http://localhost:8081/appbuilder/api
```

* example endpoint value for production: 

```
http://{{YOUR-HOSTNAME}}/villanova-hub-application-{{BUNDLE-CODE}}/villanova-hub-catalog-ms/appbuilder/api
```


## Use Villanova Hub as a bundle from AppBuilder

You can deploy through ent using pre-built image from villanova.

```
ent ecr deploy --repo=docker://registry.hub.docker.com/villanova/villanova-hub-application

ent ecr deploy --repo=docker://registry.hub.docker.com/villanova/villanova-hub-content
```

Install the bundle from AppBuilder GUI. <br><br>
Set up permissions to configure the service:

1. Login to your Keycloak instance as an admin.
2. Give at least one user the ability to manage the Hub by granting the `eh-admin` role. Assign the `eh-admin` role for the `pn-{{BUNDLE-ID}}-{{PLUGIN-ID}}-villanovapsdh-villanova-hub-catalog-ms-server` client.
3. Give the generated plugin client permission to manage users:
*  From the left sidebar, go to Clients and select client ID `pn-{{BUNDLE-ID}}-{{PLUGIN-ID}}-villanovapsdh-villanova-hub-catalog-ms-server`.
* Click the `Service Account` tab at the top of the page and select `realm-management` from the `Client Roles` field.
* Choose `realm-admin` from `Available Roles`. Click `Add selected`. It should appear as an `Assigned Role`.

Note: `BUNDLE-ID` and `PLUGIN-ID` are dynamic values that depend on the publishing url.