# Create New MuleSoft Flow

Step by step instructions to create a new MuleSoft application.

## Create Workspace

1. Open Anypoint Studio
2. Click on File -> Switch Workspace -> Other
3. Create a new workspace with the name of the application; default location is OK

## Pull Domain Project

Most projects will require a domain project.
The domain project holds common modules and has the main HTTP Listener config.

1. In Bash, navigate to where git repos are saved
2. Clone the repo: `git clone ssh://git@git.company.net:/mule/domain.git`

## Import Domain Project

1. Click on File -> Import
2. Click on Anypoint Studio -> Anypoint Studio project from File System
3. **Uncheck** Copy project into workspace
4. Under External Project, navigate to the domain project repo

## Initialize Flow Repo

If the repo is already initialized, skip this step.

1. In Bash, navigate to where git repos are saved
2. Clone the repo
3. Checkout the master branch: `git checkout master`
4. Create a README file: `touch README.md`
5. Add a title and basic description to the README
6. Add the README to the index: `git add .`
7. Commit: `git commit -m  **Initial Commit **`
8. Push: `git push`
9. Create the develop branch: `git checkout -b develop`
10. Push the branch upstream: `git push --set-upstream origin develop`
11. Create the initial version tag: `git tag v1.0.0`
12. Push the tag upstream: `git push origin v1.0.0`
13. Create a new feature branch: `git checkout -b [feature-branch-name]`

## Create Flow Mule Application

1. Click on File -> New -> Mule Application
2. Set project name in all lowercase
3. **Uncheck** use default location
4. Under Project location, navigate to the repo location

## Upgrade Project to Domain Project

1. Right click on the Mule Application -> Properties
2. Click on Mule Project
3. Set Domain to the domain project (warnings will appear after making this change)
4. In the Package Explorer, open **pom.xml**
5. Click on problems
6. There should be a few errors about multiple definitions; right click on each -> Quick Fix -> Finish

## Import APIKit

If the project is not a part of an organization, skip steps 3-5 and login with Anypoint Platform credentials.

1. In the Package Explorer, delete the main flow under src/main/mule
2. Right click the project -> Anypoint Platform -> Import from Design Center
3. Click on Configure -> External identity
4. Set Organization domain to _your organization domain_
5. Click OK and wait for the page to refresh
6. Change the Business Group to the correct business group
7. Select the correct Project/Branch and click OK

## Update APIKit

1. Click on the new file in src/main/mule
2. Click on Global Elements and delete all Http Listener configs
3. Click on Message Flow and find the main flow at the top
4. Click on the Listener and set the Connector configuration to _Domain_HTTP_Listener_Config_
5. Find the console flow and delete it

## Create Config Files

### Create Global Configuration

The global config file is where all shared configs are stored. For example, HTTP Request and Database configurations.

1. Right click src/main/mule -> New Mule Configuration File
2. For File Name put  _global_ and click finish

### Create Properties Files

Use this section if the project uses TeamCity and Octopus Deploy.

The property files are where environment variables are stored for Octo. For example, database servers and usernames/passwords.

1. Right click src/main/resources -> New -> Folder
2. For Folder Name put _local_ and click finish
3. Right click src/main/resources -> New -> Folder
4. For Folder Name put _teamcity_ and click finish
5. Right click src/main/resources/local -> New -> File
6. For File Name put _application.properties_ and click finish
7. Right click src/main/resources/teamcity -> New -> File
8. For File Name put _application.properties_ and click finish
9. Navigate to src/main/resources/global.xml
10. Click on Global Elements -> Create
11. Filter for _Configuration properties_ -> OK
12. For File put _application.properties_ and click OK