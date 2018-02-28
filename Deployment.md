## Quick Start using Release package on local machine
You will have to follow these steps to start GoNorth using the Release package:
 * [Install .Net Core](https://www.microsoft.com/net/learn/get-started). Be sure to select the correct plattform for your system
 * [Install MongoDB Community Edition](https://docs.mongodb.com/manual/administration/install-community/)
 * Start MongoDB if its not already running:
   * Open a command line
   * Navigate to the mongodb bin folder
   * Run mongod from the command line to start the MongoDB
 * Download the [Release Package](https://github.com/steffendx/GoNorth/releases)
 * Extract the Release Package to where you want to store the files of GoNorth
 * Open the file "appsettings.json" in any editor you want to adjust the config settings. You will need to:
   * Set a value for the config key **"FirstTimeDeploymentPassword"**. You can use any value for this password you want
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
 * Assign all roles to your admin account:
   * Click the Star Icon on the right of your user to edit your roles
   * Select all roles and click Add role
   * Click save to assign the roles
   * More details in the [Administration Wiki Page](/steffendx/GoNorth/wiki/Administration#user-management)
 * Create a default project:
   * Select Project Management on the left of the admin page
   * Click "Create Project"
   * Enter your project name (you can rename it later on, no worries)
   * **Important**: Click the checkbox Default Project.
   * More details in the [Administration Wiki Page](/steffendx/GoNorth/wiki/Administration#project-management)
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
 * Install the [GoNorth Webserver as a service](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/?tabs=aspnetcore2x)

More details about deploying can be found in this page below.

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
 * **KirjaAllowedAttachmentMimeTypes**: This specifies which Mime-Types are allowed for attachments in the Wiki Component Kirja.
 * **FirstTimeDeploymentPassword**: Specifies the password used for the first time deployment page (see below). It is recommended to leave this blank if you have the portal up and running.

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
Please refer to the [official documentation on how to host and deploy an ASP.Net Core application](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/?tabs=aspnetcore2x) for hosting GoNorth in a your production environment.

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
More details for this can be found on the [Admin Wiki Page](Administration.md)

## Creating a project
Since GoNorth will not work without a default project, you will also have to create a new default project in the admin project managment page. Just provide your project name and flag it as a default project.  
GoNorth will associate all the different objects you will create to this default project. I've implemented this project management to be able extend GoNorth to allow multiple projects in parallel on which different users are working in the future. But for now one default project is enough.