# Access Domino REST API

## About this procedure

The procedure guides you in accessing Domino REST API Admin UI to add and configure a schema, add a scope, and add an application.

## Before you start

You must complete the [Volt MX Go installation](../tutorials/installation.md).

## Procedure
### For Domino REST API installed via containerized deployment

1. Open `http://drapi.mymxgo.com/admin/ui` or your provided Domino REST API hostname concatenated with `/admin/ui` in your browser. 
2. Enter the following credentials in the login page: 

    - username: `mxgo admin`
    - password: `password` 

    !!!note
        If you updated the administrator's first name, last name, and password in the `values.yaml` file in the [Download the Domino REST API Helm chart](http://localhost:8000/HCL-TECH-SOFTWARE/voltmxgo-documentation/tutorials/downloadhelmchart.html#1-download-the-domino-rest-api-helm-chart) procedure as part of the containerized deployment, use the updated values for the username and password.

3. Click **Log in**.

### For Domino REST API installed via native installer

- Check how to login to [Domino REST API Admin UI](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/adminui.html#login){: target="_blank"}.
- Use your Domino server administrator username and password to log in. 

## Expected result  

A successful login leads you to the Domino REST API landing page. For details on adding and configuring a schema, adding a scope and an application, see [Using Admin UI](https://opensource.hcltechsw.com/Domino-rest-api/references/usingdominorestapi/administrationui.html){: target="_blank"} in the Domino REST API documentation. 
