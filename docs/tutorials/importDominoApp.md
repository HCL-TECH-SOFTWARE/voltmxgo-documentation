# Import a Domino Application
Domino Application in Volt MX Iris is a way to extract the domino .NSF file to view, modified create and delete.
 
## Pre-requisite.
 
    * Must have a credentials.
    * Must have a configured .NSF file, connected to scope and schema in DRAPI
    * Must have configured Foundry and Drapi
    * Must have an Iris Application
    
## Procedure

### How to Import Domino Application For New Foundry and New DRAPI 
1. Open the **Volt Mx Iris** application.
2. Click on **Project**.
3. On Project menu, hover **Import** and click **Domino Application**.
4. A pop-up box will appear. Click **Get Started**.
5. Click **Next**. A pop-up menu will appear, selecting between `Use Existing` or `Create`. 
6. Choose **Create**. The ***Foundry Backend*** will create a default name **App 1**. The Foundry Backend will incremently create a name **App**.
7. Click **Next**. 
8. Choose  **Create New DRAPI** services and Click **Next**.
9. ***Generated Services*** will appear. Fill-in the ***fields*** and Click **Next**.
    |  **Fields**     | **Description** |
    | ----------- | ----------- |
    | DRAPI URL   This refers to the DRAPI URL you are working with.     |
    | Scope       | This is the name of your configured scope describe in your App of DRAPI application management. |
    |Client ID    | This is the App ID of your Application in DRAPI application management. Once you configured and added your App, you may see all along your App ID and your App Secret. |
    |Client Secret| This is the App Secret of our Application in DRAPI application management. Once you configured and added your App, you may see all along your App ID and your App Secret. |
    |Service Name: |Any name that will identify the Volt Foundry Identity Services. |
10. Select your ***Drapi Identity Service*** and click **Next**.
11. A popup window will appear. Log in your credentials in **DRAPI**.
12. Click **Allow**. This will allow your scopes or the resources to be accessed and click **Next**.
13. Select your scope created and click **Next**. There will be lot of scope created on one **.NSF**. You'll need to find your created scope. 
14. Select your ***App Identity Service*** and click **Next**.
15. You may  _uncheck_ or _check_ again the records from your selected scope and click ***Next***.
16. This page is to validate the fields you selected on each record. 
You can click **Go Back** to verify the fields. 
17. Click ***Import Foundry Application***, if all the fields are validated.

18. Click  ***Build Iris Application*** to import all your selected records.
19. Click **Done**. This form is to show the created Forms, Views and App Forms.





 
