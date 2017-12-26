---
layout: page
title: Déploiement de paquets
redirect_from:
 - /documentation/task/deploy_fr.html
---

Le déploiement de logiciels par FusionInventory se configure en deux endroits du serveur GLPI: les paquets et les tâches.

Un paquet est un ensemble logiciel cohérent: exécutable d'installation, version, paramètres, etc…
Une tâche permet de déployer un paquet sur un ordinateur.

![]({{ site.baseurl }}/documentation/tasks/deploy/FusionInventoryMain.png)

1.  Le déploiement de paquets se fait principalement à partir du menu déroulant *Tâches* de FusionInventory. Mais ce menu peut aussi être utilisé pour d'autres tâches.
2.  Le menu déroulant *Déployer* est utilisé pour créer, modifier et supprimer les paquets qui peuvent être déployés.

# Gestion des paquets

## Créer un paquet

![]({{ site.baseurl }}/documentation/tasks/deploy/FusionPluginPackageManagementMain.png)

1.  Utilisez le sous-menu *Gestion de paquets* du menu *Déployer* pour gérer les paquets.
2.  Cliquez sur le "+" pour créer un paquet, ou cliquez sur un paquet existant pour le modifier.

### Edit package

You can add checks before running the package, but you can prefer to do
that with the deployed scripts.

![]({{ site.baseurl }}/documentation/tasks/deploy/FusionInventoryPackageCreation.png)

1.  Select to upload a file. You can upload a number of files, but must upload one at a time. You can also elect to 
    upload a zip file. 
2.  Select to get the file "From this computer". Use the browse button to select the file.
    * With **P2P** enabled, computers will keep and share the downloaded files to the other computers of the LAN. 
      This allow you to speed up a large download.
    * If **Extract** is enabled, FusionInventory will try to extract the archive (.7z, .zip, tar.gz, .tar)
3.  Click OK and the file will be uploaded.
4.  Click on "Add command", select "execute a command" then type in the command you want, you can use the script 
    name here, but if you're doing something else, any valid windows command (use full path names) can be used.
    -   You can optionally add return codes to validate against for success or failure.

If you use "move" command, use "*" in case from if the agent get the file from GLPI

## Task Management (Normal)

Please see the [task creation]({{ site.baseurl }}/documentation/fi4g/tasks.html) page.

### Creating a deployment task

**NOTE**: You **must** have created the package you want to deploy
FIRST. Please read that section if you need help with that.

![]({{ site.baseurl }}/documentation/tasks/deploy/FusionInventoryTaskTest.png)

1.  Give the task a name
2.  Select the communication type (push or pull). Traditionally we have
    used Pull.
3.  Set Advanced mode to Yes.

Then:

![]({{ site.baseurl }}/documentation/tasks/deploy/FusionInventoryNewAction.png)

1.  Click on New Action
2.  Give the job a name (Optional)
3.  Select module to use - Package Deployment

Then:

![]({{ site.baseurl }}/documentation/tasks/deploy/FusionInventoryJobDetails.png)

1.  Click the plus sign next to definition, select a package, click add.
2.  Click the plus sign next to Action, select computers etc, then use
    find as you type to add in the selection to apply the task to. Click
    add.

#### Assigning Computers to a deployment task via Mass Action:

1.  Make sure you have created but not activated a task and a deployment
    package.
2.  Use "Target a task" as the Mass Action section
3.  Select the existing non-active task.
4.  Select the existing deployment package.
5.  Click Post. This will create a new job for that task.

### Running a Deployment Task

You can run a deployment task more than once, and it is separate from
creating one.

![]({{ site.baseurl }}/documentation/tasks/deploy/FusionInventoryTaskReady.png)

1.  First, set the task to Active and click update.
2.  Then either force the task to start immediately with "Force Start"
    OR schedule the task start and click update.

### Checking a Tasks status

#### Running Jobs

When a job is running, you can see it by clicking on the FusionInventory
menu and selecting Running Jobs.

#### Task status on a PC

When a task is running on a PC it will update information about its
status. This log is saved after the task completes and can be reviewed
from the Task Job page.

![]({{ site.baseurl }}/documentation/tasks/deploy/FusionInventoryTaskStatusDetails.png)

## Deploy Dropdown

This dropdown is used to create packages for deployment and to edit
them, list them and look at groups of computers (which are internal to
fusion inventory, there are also separate groups used by
GLPI for display etc).

