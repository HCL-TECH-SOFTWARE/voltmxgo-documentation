# Import a Domino Application
Domino Application in Volt MX Iris is a way to extract the domino .NSF file to view, modified create and delete.
 
## Pre-requisite
 
     - Must have Volt MX Iris, Foundry and Domino REST API credentials

    -  Must have a configured .NSF file, connected Domino REST API.
    -  


    
## Procedure

1. Open the **Volt Mx Iris** app.
2. Click on **Project** &rarr; **Import** &rarr; **Domino Application**.
4. A pop-up box appears. Click **Get Started**.

    ![Get Started](../assets/images/importstarted.png)

5. Click **Next**. A pop-up menu appears, selecting between `Use Existing` or `Create`. 

    ![Create ](../assets/images/importcreate.png)
    
6. Choose **Create**. The ***Foundry Backend*** create a default name **App 1**. The Foundry Backend incremently create a name **App**.
7. Click **Next**. 
8. Choose  **Create New DRAPI** services and Click **Next**.
9. ***Generated Services*** wiappears. Fill-in the ***fields*** and Click **Next**.

    |  **Fields**     | **Description** |
    | -----------      | -----------     |
    | DRAPI URL   | This refers to the DRAPI URL you are working with.     |
    | Scope       | This is the name of your configured scope describe in your App of DRAPI application management. |
    |Client ID    | This is the App ID of your Application in DRAPI application management. Once you configured and added your App, you may see all along your App ID and your App Secret. |
    |Client Secret| This is the App Secret in DRAPI application management. Once you configured and added your App, you may see all along your App ID and your App Secret. |
    |Service Name: |Any name that identify the Volt Foundry Identity Services. |

10. Select your ***Drapi Identity Service*** and click **Next**.
11. A popup window appears. Log in your credentials in **DRAPI**.
12. Click **Allow** and click **Next**.
13. Select your scope created and click **Next**. There are lot of scope created on one **.NSF**. You'll need to find your created scope. 
14. Select your ***App Identity Service*** and click **Next**.
15. You may  _clear or _select_ again the records from your selected scope and click ***Next***.
16. This page is to validate the fields you selected on each record. 
You can click **Go Back** to verify the fields. 
17. Click ***Import Foundry Application***, if all the fields are validated.

18. Click  ***Build Iris Application*** to import all your selected records.
19. Click **Done**. This form is to show the created Forms, Views and App Forms.





 
