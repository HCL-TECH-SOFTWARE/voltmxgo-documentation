# Troubleshooting

List of issues and corresponding resolutions. 

## General issues

- [**First Touch or Custom Application Fails to Install on Volt MX Go Foundry**](https://support.hcltechsw.com/csm?id=kb_article&sysparm_article=KB0106427){: target="_blank" rel="noopener noreferrer"}

    !!!note
        This issue and its corresponding resolution aren't applicable when setting up First Touch in Volt MX Go installed in a development or test-only environment.   

- **The kubectl commands fail after restarting Windows or Rancher Desktop**

    When your kubectl commands fail after restarting Windows or Rancher Desktop, you must run the `kubectl config set-context --current --namespace=mxgo` command in your Ubuntu terminal session to set the current namespace context.

## Domino Rest API schema issues

--8<-- "mxgoversion.md"

List of issues and corresponding resolutions related to Domino REST API when importing Domino applications using Design Import.

!!!warning "Important"
    If the Domino Rest API settings encounter an issue, a prompt will appear. While it may proceed, there is no guarantee that the resulting program will function correctly.

    ![](../assets/images/didrapissues.png)


!!!note
    These issues apply only to **default** mode and **dql** mode.

- **Field value mismatch between modes** 

    This issue occurs when the **dql** mode and **default** mode have different property values, such as fields, type, field access, in declaring each mode. They have to be in parallel or similar in property values.

- **Form missing Default mode Fields and DQL mode**

    This issue occurs when you haven't declared the same property values in both the **dql** mode and **default** mode. You have to declare the same property values in **dql** mode and **default** mode.

- **Form missing Fields on Default mode**

    This issue occurs when you save the form without declaring any property values or fail to declare property values in **default** mode that's in the **dql** mode. You must declare all the fields in the **default** mode.

- **Missing DQL mode**

     This issue occurs when only the default mode is declared. The **dql** mode and **default** mode must be parallel or similar to each other before importing the schema.

Consult your Domino Rest API administrator to assist you with configuring the Domino Rest API based on the prerequisites required for [importing Domino Application](../tutorials/designimport.md#before-you-begin).

### Domino database ACL and Domino REST API maximum access level

The **Maximum Access Level** specifically concerns access through Domino REST API and doesn't update the database's ACL. The user's access level defined in the Domino database ACL won't be exceeded. For example, if the user is specified as a Reader in the Domino database ACL and maximum access level for the scope is set to Editor, the user won't have the ability to create documents through Maximum Access Level.

- **Maximum Level Access in Domino REST API**

    You should contact your Domino REST API admin to update your scope's Maximum Level Access to *Designer*.

    ![alt text](../assets/images/didrapierr.png)


- **Domino database ACL**
   You should contact your Domino admin to update your Domino database `.nsf` ACL to *Designer*.

    ![alt text](../assets/images/diaclerr.png) 