To make sure that GoNorth has as little bugs as possible I have implemented UI tests (and also because I wanted to play around with [Puppeteer](https://github.com/GoogleChrome/puppeteer)). These UI tests can be found in the UITest subfolder.  

## Implementation of the UI Tests
The implemented UI tests use [mocha](https://github.com/mochajs/mocha) as a test framework and [Puppeteer](https://github.com/GoogleChrome/puppeteer) as a headless browser.  
The UI Tests will login to GoNorth and navigate to all the different pages of GoNorth. The tests ensure that no JavaScript errors occure and no requests fail.   
The test config (target url, username and password) is read from the following environment variables:
 * **TEST_BASE_URL**: This specifies the base url to your GoNorth deployment (i.e. https://localhost:5001). You should not add a slash in the end.
 * **TEST_LOGINNAME**: The username of the user that is used to login to GoNorth. To test all of GoNorth you will have to give this user all roles except of Administrator.
 * **TEST_PASSWORD**: The password of the test user.

Using environment variables you will not have to commit the user credentials or add them in a readable form on the server. Instead you should use whatever CI tool you have and only set those variables for the release process.  
If you just want to test it locally you can create an npm script which sets these variables before running "npm run test". I have included a sample npm script for this called "testWithCred".

## Integrating the UI Tests in your CI pipeline
To find errors after deploying a new version of GoNorth (preferably on your test environment) you can include those UI tests in your CI pipeline. To do so you will just have to add a new step which runs "npm run test" in the working directory of the UI Tests files and sets the required environment variables.  
Mocha will create a JUnit test result file called "xunit.xml" in the working directory.  
You can then publish the test results of this generated file. In [Azure DevOps](https://azure.microsoft.com/en-us/services/devops/) you could use the [Publish Test Results task](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/test/publish-test-results?view=azure-devops&tabs=yaml) for example.