**If you want to use Docker you can find more details in the [Docker Deployment wiki page](/steffendx/GoNorth/wiki/Docker-Deployment)**  
**If you want to use an installer you can find more details in the [Installer Deployment wiki page](/steffendx/GoNorth/wiki/Installer-Deployment)**  

## Quick Start using Release package on local machine
You will have to follow these steps to start GoNorth using the Release package:
 * [Install .Net Core](https://dotnet.microsoft.com/download). Be sure to select the correct plattform for your system. GoNorth requires .Net Core 6.0.
 * [Install MongoDB Community Edition](https://docs.mongodb.com/manual/administration/install-community/). GoNorth supports MongoDB up to version 5.0.
 * Start MongoDB if its not already running:
   * Open a command line (if you are running windows you can press File -> Open Windows PowerShell -> Open Windows PowerShell inside the Mongodb bin folder)
   * Navigate to the mongodb bin folder
   * Run mongod from the command line to start the MongoDB
   * **Please note:** If you installed MongoDB as a service this is not required since MongoDB will already be running.
 * Download the [Release Package](https://github.com/steffendx/GoNorth/releases)
 * Extract the Release Package to where you want to store the files of GoNorth
 * Open the file "appsettings.json" in any editor you want to adjust the config settings. You will need to:
   * Set a value for the config key **"FirstTimeDeploymentPassword"**. You can use any value for this password you want (for example "A9TempWord!")
   * The MongoDB Connection string should be fine if you are running mongodb locally
 * Start the application:
   * Open a command line
   * Navigate to the folder where you extracted the Release Package
   * Run the command `dotnet GoNorth.dll`
 * Confirm that the webserver is running by navigating to http://localhost:5000. If you get a login screen the webserver is running
 * Navigate to http://localhost:5000/Deployment to create your admin account:
   * Enter the password you specified in the appsettings.json for the **"FirstTimeDeploymentPassword"** Key in the Text Field "First Time Deployment Password"
   * Enter your Username, E-Mail Address and a Password. The password must have at least 8 characters
   * Press Save to create your admin account
   * If any error occures while creating your admin account you will see it in the Command line where you ran the command `dotnet GoNorth.dll`
 * You will be redirected to the login screen. You can now login with the email address and password you provided in the step before
 * Navigate to the administration area using the NavBar at the top
 * Create a default project:
   * Select Project Management on the left of the admin page
   * Click "Create Project"
   * Enter your project name (you can rename it later on, no worries)
   * **Important**: Click the checkbox Default Project.
   * More details in the [Administration Wiki Page](/steffendx/GoNorth/wiki/Administration#project-management)
 * Assign all roles to your admin account:
   * Click the Star Icon on the right of your user to edit your roles
   * Select all roles and click Add role
   * Click save to assign the roles
   * More details in the [Administration Wiki Page](/steffendx/GoNorth/wiki/Administration#user-management)
 * Logout
 * Stop the webservice by pressing Ctrl+C in the command line which is running the webservice
 * Change the value for the config key **"FirstTimeDeploymentPassword"** back to "" in the **"appSettings.json"** file
 * Start the webservice again:
   * Open a command line
   * Navigate to the folder where you extracted the Release Package
   * Run the command `dotnet GoNorth.dll`
 * Open a browser and navigate to http://localhost:5000
 * Login with your admin account
 * You can now use all the different modules of GoNorth

If you want to you can also:
 * [Install MongoDB as a service to have it always running and not having to start it manually if you are using windows](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/#configure-a-windows-service-for-mongodb-community-edition)
 * Install the [GoNorth Webserver as a service](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/?view=aspnetcore-6.0)

More details about deploying can be found in this page below.

## Updating an existing Deployment
If you already have GoNorth installed and want to simply update an existing installation you can do the following:
 * Stop GoNorth
 * Replace the existing files with the lastest [Release Package](https://github.com/steffendx/GoNorth/releases) files while keeping all files that are not getting overwritten.  
   **Attention**: Be careful about replacing the appsetting files to not overwrite your customized settings. You might need to merge the appsettings files by hand if new keys werde added in a new release
 * Start GoNorth
 * Navigate to the Admin Page -> Setup DB to make sure you have all the latest indices added to the database.

**Please note**: If you have a GoNorth version installed prior to 1.9.0.5 you might need to upgrade your .Net Core version to 6.0.

## Adjust configuration
You will have to adjust the config file to your settings. You can find the config settings in the "appsettings.json" file. If you want to adjust values for development you can adjust the "appsettings.development.json" file.

### MongoDB Connection
To specify your MongoDB connection settings you will have to adjust the connection string and database name in the MongoDB section.

### Email Settings
You can specify your connection settings for your SMTP server if you want GoNorth to be able to send emails. This is useful for allowing users to reset their passwords.  
Please note: The SmtpPassword must be saved as an encrypted value. You can use the encryption page in the admin area (see below) to encrypt a value.

### Logging
In the logging section you can specify your log levels. Possible values are "Trace, Debug, Information, Warning, Error, Critical, None". Trace will log the most informations, while none will log no informations at all.

### Miscellaneous Settings
The following settings can be made in the Misc Section:
 * **ExternalUrl**: Specifies the url used when filling E-Mail Templates for resetting passwords etc. This is required to correctly fill the templates when using a reverse proxy for hosting.
 * **KirjaAllowedAttachmentMimeTypes**: This specifies which Mime-Types are allowed for attachments in the Wiki Component.
 * **KirjaVersionMergeTimeSpan**: Specifies the timespan in minutes for a wiki page version to be merged if it was edited by the same user. This prevents to many versions to be spammed. If the value is zero or negative, no versions will be merged. You can read more details in the [wiki page](/steffendx/GoNorth/wiki/Kirja)
 * **KirjaMaxVersionCount**: Specifies the maximum amount of version to be kept for a wiki Page. If the value is equal to zero, the versioning feature will be disabled. If the value is below zero an unlimited amount of versions will be kept. More details can be read in the [wiki page](/steffendx/GoNorth/wiki/Kirja).
 * **TimelineMergeTimeSpan**: Specifies the timespan in minutes for timeline events to be merged if made for the same event for the same user (for example if a user modifies the same wiki page in a timespan of 5 minutes). This way you can prevent flodding of timeline events. If the value is below or equal zero, no timeline events will be merged.
 * **FirstTimeDeploymentPassword**: Specifies the password used for the first time deployment page (see below). It is recommended to leave this blank if you have the portal up and running.
 * **UseGdpr**: True if the GDPR feature should be used, else false. More details can be found on the [GDPR wiki page](/steffendx/GoNorth/wiki/Gdpr).
 * **UseLegalNotice**: True if the Legal Notice feature should be used, else false. More details can be found on the [legal notice wiki page](/steffendx/GoNorth/wiki/Legal-Notice).
 * **DisableAutoSaving**: True if you want to disable auto saving. Details can be found in the [wiki](/steffendx/GoNorth/wiki/Autosave)
 * **DisableWikiExternalSharing**: True if you want to disable support for external sharing of wiki pages. Details can be found in the [wiki](/steffendx/GoNorth/wiki/Kirja#review)
 * **AllowScriptSettingsForAllFieldTypes**: True if you want to be able to set export settings for all types of fields, not only the ones which can be exported to script.
 * **DisableItemInventory**: True if you want to disable an inventory for items, else false.

### Legal Notice Settings
If you are using the [legal notice](/steffendx/GoNorth/wiki/Legal-Notice) you can adjust the contact details shown on the legal notice page in the LegalNotice section.

## Building
Since GoNorth is build with .Net Core you will have to install .Net Core on your system for building. (See [Getting Started with .Net Core](https://www.microsoft.com/net/learn/get-started)). Before building the project I recommend you adjust the encryption key bytes in the "/Services/Encryption/AesEncryptionService.cs" to a new value.

After you have installed .Net Core you can build the project using:

    dotnet build -c Release

Afterwards you will find a new folder bin/Release which will include the built project.

If you want to publish the project for deployment you will have to use:

    dotnet publish -c Release

Afterwards you will find a new folder bin/Release/publish which will include the files required for deployment.

## Running GoNorth locally
To run the web application on your development system you can use:

    dotnet run

This will start a new webserver listening on port 5000. Alternatively you can simple press run in [Visual Studio Code](https://code.visualstudio.com/).  
If your MongoDB is running you can now connect to the portal. But you will have to create a new admin user, see First Time Deployment below on how to create this user.

## Hosting GoNorth in your production environment
Please refer to the [official documentation on how to host and deploy an ASP.Net Core application](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/?view=aspnetcore-6.0) for hosting GoNorth in a your production environment. Keep in mind that GoNorth requires .Net Core 6.0.

If you use nginx or any other reverse proxy you will have to adjust the maximum upload size and the maximum header size. This is required to be able to upload big images for maps in Karta and ensure stability.  
I use the following settings in nginx for example:
    
    client_max_body_size 100m;
    client_body_timeout 180s;

    fastcgi_buffers 16 16k; 
    fastcgi_buffer_size 32k;

    proxy_buffer_size   128k;
    proxy_buffers   4 256k;
    proxy_busy_buffers_size   256k;

## First Time Deployment
Once you can reach GoNorth in the browser (either locally or in your production environment) you must proceed with the first time deployment steps.
Since you need an admin account to create new users you will have to create a user now. For this I implemented a First Time Deployment page.  
This page can be reached under **/Deployment** (i.e. http://localhost:5000/Deployment). This is only available if a value is specified for the Config Key **FirstTimeDeploymentPassword** in the Misc Section. This page will also not be available if you already have an admin account.  
So specify a **FirstTimeDeploymentPassword** in your config, restart your webserver and navigate to the first time deployment page. If you open this page you will have to enter the deployment password specified in the config and enter the user details. After pressing save you will be redirected to the login screen where you can now login with your new admin account.  
Please note: You will not get an error message if any problem occures to not expose too much information. So if you can't login try again.

## Adjusting the config
After you have an admin account it is recommended to clear the FirstTimeDeploymentPassword value in the config. Additionally you can now encrypt your email password for the config under Administration -> Encrypt value.  
After adjusting the config you have to restart the web service.  

## Creating users / Adjusting roles
You can now create new users and adjust your roles to make the different modules available to you and other users.  
Please note: You will have to sign out and sign in again in order for the role changes to take effect.  
More details regarding this can be found on the [Admin Wiki Page](/steffendx/GoNorth/wiki/Administration)

## Creating a project
Since GoNorth will not work without a default project, you will also have to create a new default project in the admin project managment page. Just provide your project name and flag it as a default project.  
GoNorth will associate all the different objects you will create to this default project. I've implemented this project management to be able extend GoNorth to allow multiple projects in parallel on which different users are working in the future. But for now one default project is enough.