The following page will give you a brief overview of the implementation.

## Development
You will have to use [.Net Core](https://www.microsoft.com/net/learn/get-started/windows) to build the project. You simply have to run "dotnet run" to start GoNorth. You can find more details about running and deploying GoNorth in the [Deployment](/steffendx/GoNorth/wiki/Deployment) page.  
The different services in the background for database access or analyzing the values is injected using the [ASP .Net Core dependency injection](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection).  
If you want to adjust the frontend you will have to use [Knockout](http://knockoutjs.com/).  
The JavaScript files and css files are bundled and minified on build and these bundled versions are used. If you want to add new files you will have to adjust the [bundleconfig.json](https://docs.microsoft.com/en-us/aspnet/core/client-side/bundling-and-minification?view=aspnetcore-3.0&tabs=visual-studio).  
I recommend you use [Visual Studio Code](https://code.visualstudio.com/) for development which I used to build the whole project.

## Folder structure
This is the folder structure of the project:
 *  **Authentication**: This folder includes all the classes required for the [ASP .Net Core Identity Framework](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/identity?view=aspnetcore-3.0&tabs=visual-studio)
 * **Config**: This folder includes classes for reading the config. If you need a new config value you will have to add this as a property to the classes in here
 * **Controllers**: This folder includes all the ASP .Net controllers
   * **Api**: This subfolder includes all the ASP .Net WebApi controllers
 * **Data**: This folder includes all the classes required for Database access. There are subfolders for every different module
 * **Documentation**: This folder includes documentation
 * **Extensions**: Includes classes that provide extension methods
 * **HelpImages**: Includes some images in their original format
 * **Localization**: Includes all classes used for localization implementation (not the language files)
 * **Logging**: Includes all logger classes
 * **Models**: Includes the ASP .Net Models for Views. There are subfolders for all the different modules
 * **Resources**: Includes all the language files
   * **Authentication**: Includes language files used for error during authentication or user creation
   * **Controllers**: Includes language files that are used by the controllers for server side errors
   * **Models**: Includes language files that are used for model localization
   * **Services**: Includes language files that are used for service localization. The timeline texts can be found here as well.
   * **Templates**: Includes language files that are used for email localization
   * **Views**: Includes language files for the different views
 * **Services**: Includes different service classes
   * **Email**: Includes email services
   * **Encryption**: Includes classes used for encryption of config values etc.
   * **ImplementationStatusCompare**: Includes compare classes to determine which values where changed of an object that should be flagged as implemented
   * **Karta**: Includes services for map processing
   * **Kirja**: Includes services for analyzing the Kirja wiki pages for references
   * **Timeline**: Includes services for adding and displaying timeline entries
   * **User**: Includes services for user creation
 * **Templates**: Includes a helper class for creating a localization service for email templates
 * **Views**: Includes the different views
 * **wwwroot**: Includes all the css and javascript files
   * **css**: Includes the project css files
   * **img**: Includes the images
   * **js**: Includes all the javascript files. They are organized by module in folders.
   * **lib**: Includes the different javascript files