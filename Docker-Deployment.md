**If you want to deploy GoNorth without using Docker you can find more details in the [Deployment wiki page](/steffendx/GoNorth/wiki/Deployment)**  
**If you want to use an installer you can find more details in the [Installer Deployment wiki page](/steffendx/GoNorth/wiki/Installer-Deployment)**  

## Installing Docker
[Docker](https://www.docker.com/) is an open-source software that uses OS-level virtualization to deliver software packages in containers.  
If you dont have it installed already, follow the steps described [here to install docker](https://docs.docker.com/get-started/).

## Run Docker from repository
The GoNorth repository contains a dockerfile as well as a docker compose file. You can use those to start a docker image from the cloned source code.  
To do so the following steps are required:  

 * Create the docker volumes by running **docker-volume-setup.sh**. If you are on windows, just run all the commands inside the file.  
 **Please note:** Since the paths inside this script are relative paths you must make sure your working directory is set to the checked out GoNorth source repository. To do use the command `cd PATH_TO_GONORTH` (replace PATH_TO_GONORTH with the actual path).
 * Open **appsettings.docker.json** and enter a first time deployment password, for example "Deploy".
 * Build GoNorth using the following command: `docker-compose up --build`
 * Once this command has finished GoNorth will be available at http://localhost:5000/
 * To create your admin account navigate to http://localhost:5000/Deployment
 * Enter the password you specified in the appsettings.json for the **"FirstTimeDeploymentPassword"** Key in the Text Field "First Time Deployment Password". If you used the example, that would be "Deploy".
 * Enter your Username, E-Mail Address and a Password. The password must have at least 8 characters
 * Press Save to create your admin account
 * You can now login at http://localhost:5000/ using the new account
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
 * Logout and login back in again to make sure the new roles get active
 * You are now ready to use GoNorth
 * Next time you want to start GoNorth you can simply run `docker-compose up`, omitting the `--build` parameter.