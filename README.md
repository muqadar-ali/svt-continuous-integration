# svt-continuous-integration
> Configure SQL Test, Visual Studio NUnit Tests, TFS, and TeamCity (Continuous Integration)   

## Getting Started
> This readme will guide you through installation and configuration of **SQL Test**, **TeamCity**, **TFS**, and **Visual Studio NUnit** from scratch.   

### Prerequisites
>* Visual Studio installed   
>* SQL server installed    
>* Have a hotmail/live/outlook email id    
>* Sign in to visual studio with account    

## Download Setups 

>*  Download [TeamCity](https://www.jetbrains.com/teamcity/download/)    
>*  Download zip [tSQLt Runner](https://github.com/cprieto/tsqlt-teamcity/releases) 


   ![alt text](Images/downloadTSQLT_Runner.png?raw=true) 
   
   
>*  Download [SQL Test](https://www.red-gate.com/dynamic/products/sql-development/sql-test/download) 

## Installing 

#### TeamCity 

  > Run downloaded setup of teamcity and proceed with standard installation. It will prompt for a port in during installation.  
  Enter port i.e. 8888 and note that down. After a few steps of installtion, it will show an **information   
  window** like this 
  
  
  ![alt text](Images/teamcity-workdir.PNG) 
  
  
  > Next step is to select system account for given steps like this 
  
  
  ![alt text](Images/teamcity-select-account.PNG) 
  
  
  > Once you are done with installtion, it will automatically start teamcity in your default browser. 
  Follow below given steps if it doesn't start.
  1. Open **cmd** as admin.
  2. Enter
  ```
  cd C:\TeamCity\bin
  ```
  3. execute command
  ```
  teamcity-server start
  ```
  4. Open **localhost:yourport** in browser. 
  you will have to go through a few steps more in browser if it is the first time that you have installed teamcity on your machine. 
  follow those steps i.e. create account (enter username, password). One of those steps will be about **Database**. Have a look 
  at given image and select that option and go on with further steps if any.
  
  > Image Source: https://confluence.jetbrains.com/display/TCD10/Installation+Quick+Start 
  
  
  ![alt text](Images/teamcity-initialstep.png) 
  
  
  > Setup is done. 
  
#### tSQLt Runner 
   
   > Open teamcity in browser, go to **Administration** tab on top 


   ![alt text](Images/teamcity-adm.png) 
   

   > Scroll down and click **Plugins List** 


   ![alt text](Images/teamcity-plugins-list.png) 
   

   > follow below shown steps 


   ![alt text](Images/teamcity-plugin-upload.png) 
   

   > select zip and click upload 


   ![alt text](Images/teamcity-tsql-popup.png) 
   
    
   > Now you should see **tsqlt runner** in external plugins 
   
   
   
   ![alt text](Images/teamcity-tsqlt-verify.png) 
   
   
#### SQL Test

   > Run downloaded sql test setup and select only **SQL Test** 
   
   
   ![alt text](Images/sql-test-install.png) 
   
   
   > and go on with standard installation
   
   ##### Verify sql test installation
   
  >  1. Open **Microsoft SQL Server Management Studio (MSSMS)** and connect with your username and password. 
  >  2. Go to **Databases** and right click on any schema/database.
  >  3. You should see following options
   
   
   ![alt text](Images/sql-test-installed2.png) 
   
   
   ##### Running sql test in Microsoft SQL Server Management Studio (MSSMS) 
   
   > Open MSSMS 
   > Go to **Databases** 
   > Right click on any schema/database 
   > Click **New Test** and after that you should see below given option if it is the first time. 
   
   
   ![alt text](Images/sql-test-schema-select.png) 
   
   
   > Write test case name(test stored procedure) 
   * It should start with **test** word (standard notation) 
   
   
   ![alt text](Images/sql-test-new-test.png) 
   
   
   > After above steps, you should see an auto generated new sample test case like this 
   
   
   ![alt text](Images/new-test-sample.png) 
   
   
   > Inorder to keep this tutorial simple, remove comments and make a small change in above shown test case 
   > i.e. it should look like this 
   
   
   ![alt text](Images/sql-test-new-test-simple.png) 
   
   
   > Execute this test case (procedure script)
   
   
   ![alt text](Images/sql-test-execute.png) 
   
   
   > You should see below given message 
   
   
   ![alt text](Images/sql-test-execute-success.png)
   
   > After that, go to below shown tab 
   
   
   ![alt text](Images/click-sql-test.png) 
   
   > Run test case in MSSMS to verify if framework works or not  
   
   
   ![alt text](Images/sql-test-run-tests.png) 
   
   > Success message 
   
   
   ![alt text](Images/sql-test-run-success.png) 
   
   
   
## Configure and run 
   
   #### Create TFS project live (Tested using hotmail account) 
   
   > Go to TFS Online: https://visualstudio.microsoft.com/vso/  
   > Get started for free   
   > Sign in (Sign up and sign in if you do not have microsoft account i.e. hotmail/live/outlook)   
   > Create project as shown below   
   
   
   ![alt text](Images/tfsCreateProject.png) 
   
   
  >  then 
   
   
   ![alt text](Images/tfsCreateProject2.png) 
   
   
 >   And you should see your first TFS project created
   
   
   ![alt text](Images/tfs-project-created.png)
   
   
 >   Now we need to generate token. To do that, go to security tab as shown below
   
   
   ![alt text](Images/tfs-token.png) 
   
   
 >   Click **add** as shown below
   
   
   ![alt text](Images/tfs-add-token1.png) 
   
   
 >   fill the given fields 
   
   
   ![alt text](Images/tfs-token2.png) 
   
   
 >   scroll down and click **Create Token** 
   
   
   ![alt text](Images/tfs-token-gen.png) 
   
   
 >   you should now copy the generated token and note it down as shown below 
   
   
   ![alt text](Images/tfs-token-copy.png) 
   
   
>    you have successfully configured tfs online. Now it is time to create a visual studio project with NUnit tests.
   
#### Create visual studio project 
   
 >   Go to File => New => Project and select the project as shown below.
 >   Name the project same as you named the tfs repository (in order to keep it simple for now) 
   
   
   ![alt text](Images/vs-code1.png) 
   
   
  >  now you have empty test method as shown below but it is in MSTest framework. (We will change it to NUnit as we move further) 
   
   
   ![alt text](Images/vs-code2.png) 
   
   
 >   Add a new project to same solution (that needs to be nested) 
   
   
   ![alt text](Images/vs-code3.png) 
   
   
 >   select project type as shown below 
   
   
   ![alt text](Images/vs-code4.png) 
   
   
 >   now you have empty class 
   
   
   ![alt text](Images/vs-code5.png) 
   
   
 >   change above shown class to **calculator** class (for testing purpose) 
   
   
   ![alt text](Images/vs-code6.png)
   
   
 >   Adding reference of calculator project (ClassLibrary1) to testing project 
   
   
   ![alt text](Images/vs-code7.png) 
   
   
 >   select as shown below 
   
   
   ![alt text](Images/vs-code8.png) 
   
   
 >   Adding **NUnit** test framework and **NUnit adapter** to the test project 
   
   
   ![alt text](Images/vs-code9.png) 
   
   
   ![alt text](Images/vs-code10.png) 
   
   
   ![alt text](Images/vs-code11.png) 
   
   
   
   ![alt text](Images/vs-code14.png)
   
   
 >   Change **UnitTest1** class (or whatever you named it) as shown below 
   
   
   ![alt text](Images/vs-code12.png) 
   
   
 >   Build solution  
 >   Run test cases as shown below 
   
   
   ![alt text](Images/vs-code15.png) 
   
   
 >   Go to **Test Explorer** to see results 
   
   
   ![alt text](Images/vs-code13.png) 
   
   
 >   Test cases result 
   
   
   ![alt text](Images/vs-code17.png) 
   
   
 >   you can also run tests using **Test Explorer** 
   
   
   ![alt text](Images/vs-code16.png)  
   
   
   
 #### connect remote repository (online tfs) to visual studio project 
  
 >  Open team explorer 
  
  
  ![alt text](Images/tfs-vs1.png)  
  
  
 >  Click connect 
  
  
  ![alt text](Images/tfs-vs2.png)  
  
  
  ![alt text](Images/tfs-vs3.png) 
  
   
>    select the project 

   
   ![alt text](Images/tfs-vs4.png) 
   

   
>    map and get project 
   
   
   ![alt text](Images/tfs-vs5.png) 
   
 >   mapped successfully. now we need to push the project (add to source control) 
   
   
   ![alt text](Images/tfs-vs6.png)  
   
   
   ![alt text](Images/tfs-vs7.png)  
   
   
   ![alt text](Images/tfs-vs8.png)  
   
   
 >   go to team explorer => pending changes => check in changes 
   
   
   ![alt text](Images/tfs-vs16.png)  
   
   
   ![alt text](Images/tfs-vs9.png)  
   
   
   ![alt text](Images/tfs-vs10.png) 
   
   
   ![alt text](Images/tfs-vs11.png)  
   

 >   tfs is configured. follow next step of creating project in teamcity 
   
  #### Creating project in teamcity 
  
 >  Open team city in browser and click **Administration** tab on top 
 >  before we move on to creating project, let's add some tools. 
  
  
  ![alt text](Images/tc-vs21.png) 
  
  
  ![alt text](Images/tc-vs22.png) 
  
  
 >  add NUnit console 
 
  
  ![alt text](Images/tc-vs23.png) 
  
  
>   select NUnit console version 
  
  
  ![alt text](Images/tc-vs24.png) 
  
   
 >  again click install tool and add NuGet installer (version 4.8.1 for this tutorial)
  
  
  ![alt text](Images/tc-vs25.png) 
  
   
   
 >  Go to Administration tab and then create new project 
   
   
  ![alt text](Images/teamcity-new-proj.png)  
  
  
 >  after that, select visual studio team service 
  
  
  ![alt text](Images/tc-conf1.png)  
  
  
  ![alt text](Images/tc-conf2.png) 
  
 >  choose repository 
  
  
  ![alt text](Images/tc-conf3.png) 
  
  
 >  and after that you will be prompted with an option, just click **Proceed**. 
  
  
  ![alt text](Images/tc-vs36.png) 
  
  
 >  after this, just click cancel and go to **Parameters** tab.  
 >  we need to add 4 parameters.
  
  
  ![alt text](Images/tc-conf4.png) 
  
  
  
  ![alt text](Images/tc-conf5.png) 
  
  
  1. 
 >  add project name parameter 
  
  
  ![alt text](Images/tc-conf6.png) 
  
  
  2. 
 >  click **add parameter** as shown in one of above pics.   
 >  this time, add database server parameter. you can find your database server name by clicking  
  Microsoft sql server management studio 
  
  
  ![alt text](Images/tc-conf9.png) 
  
  
  
  ![alt text](Images/tc-vs27.png) 
  
  
  3.
 >  click add parameter and add database name.  
 >  you can get your database name from microsoft sql server management studio as shown below  
  
  
  ![alt text](Images/tc-conf10.png) 
  
  
  ![alt text](Images/tc-conf11.png) 
  
  
  4. 
  > click add parameter and add database username 
  
  
  ![alt text](Images/tc-conf7.png) 
  
  
>   parameters added. you should see these 4 parameters 
  
  
  ![alt text](Images/tc-conf12.png) 
  
  
  > Now we need to add 4 build steps.
  > Go to build steps tab 
  
  
  ![alt text](Images/tc-conf13.png) 
  
  
  
  ![alt text](Images/tc-conf14.png) 
  
  
 >  select NuGet installer 
  
  
  ![alt text](Images/tc-conf16.png) 
  
  
  1. 
 >  add NuGet installer to your project and save 
  
  
  ![alt text](Images/tc-vs26.png) 
  
  
  2. 
  > click add build step and select MS Build   
  > add MS Build step 
  
  
  ![alt text](Images/tc-conf15.png) 
  
  
 >  save. 
  
  3.
 >  click add build step and select NUnit 
 >  add NUnit step 
  
  
  ![alt text](Images/tc-conf17.png) 
  
  
>   save 
  
  4. 
 >  click add build step and select tSQLt Runner  
 >  add tSQLt Runner step (to run sql tests) 
  
  
  ![alt text](Images/tc-conf18.png) 
  
  
  
 >  you should see these 4 build steps 
  
  
  ![alt text](Images/tc-vs33.png) 
  
  
  
  > In order to avoid any errors, go to visual studio project and make some kind of changes to project like 
  > go to calculator class 
  > go to add method 
  > change return statement from 
  ```
  return a+b; 
  ```
 >  to 
  ``` 
  return a+b+3;
  ```
 >  save it (Ctrl+S) and again change it to 
  ```
  return a+b;
  ```
>   save it (Ctrl+S). Go to team explorer => pending changes => check in 
  
  
  ![alt text](Images/tfs-vs16.png) 
  
  
>   THE TIME HAS COME ! 

>  A few steps more to run teamcity continuous integration 

>   Redirect to: **localhost:yourport** in your browser and click your project 
  
  ![alt text](Images/tc-vs28.png) 
  
>   click run and wait for the result 
  
  ![alt text](Images/tc-29.png) 
  
>   result 
  
  ![alt text](Images/tc-vs30.png) 
  
>   You have your continuous integration. Enjoy!. 
  
  
## Common Errors

* NuGet missing on computer 

![alt text](Images/error.png) 


* Solutions 

Case 1. 

Add NuGet installer in your teamcity build step on top (1st step). 

Case 2. 
> Go to your visual studio project.

> Change a few lines. 

> Save it. 

> Again undo changes. 

> Save it. 

> Go to team explorer => pending changes => check in. 


  
  
  
  
  
