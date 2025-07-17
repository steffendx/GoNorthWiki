**If you want to deploy GoNorth without using the installer you can find more details in the [Deployment wiki page](/steffendx/GoNorth/wiki/Deployment)**  
**If you want to use Docker you can find more details in the [Docker Deployment wiki page](/steffendx/GoNorth/wiki/Docker-Deployment)**

## Quick Start using Release package on local machine
You will have to follow these steps to start GoNorth using the Release package:
 * Download the [installer release package](https://github.com/steffendx/GoNorth/releases)) fitting for your OS
 * [Install .Net Core](https://dotnet.microsoft.com/download). Be sure to select the correct plattform for your system. GoNorth requires .Net Core 8.0.
 * [Install MongoDB Community Edition](https://docs.mongodb.com/manual/administration/install-community/). GoNorth supports MongoDB up to version 5.0.
 * Start MongoDB if its not already running:
   * Open a command line (if you are running windows you can press File -> Open Windows PowerShell -> Open Windows PowerShell inside the Mongodb bin folder)
   * Navigate to the mongodb bin folder
   * Run mongod from the command line to start the MongoDB
   * **Please note:** If you installed MongoDB as a service this is not required since MongoDB will already be running.
 * Extract the Release Package to where you want to store the files of GoNorth
 * Start the installer using **Installer** or **Installer.exe** (depending on your OS)
 * Start the webservice:
   * Open a command line
   * Navigate to the folder where you extracted the Release Package
   * Run the command `dotnet GoNorth.dll`
 * Open a browser and navigate to http://localhost:5000 or https://localhost:5001
 * Login with your created admin account
 * You can now use all the different modules of GoNorth

If you want to you can also:
 * [Install MongoDB as a service to have it always running and not having to start it manually if you are using windows](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/#configure-a-windows-service-for-mongodb-community-edition)
 * Install the [GoNorth Webserver as a service](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/?view=aspnetcore-8.0)

More details about deploying or updating an existing installation can be found in the [deployment page](/steffendx/GoNorth/wiki/Deployment) below.