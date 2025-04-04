# Access Domino REST API

## About this task

Access Domino REST API Admin UI so you can add and configure a schema, add a scope, and add an application.

## Before you begin

You must complete the [Volt MX Go installation](../../tutorials/installation.md).

## Procedure

<!--### For Domino REST API installed via an installer-->

- Check how to login to [Domino REST API Admin UI](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/adminui.html#login" Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Domino REST API documentation.

- Use your Domino server administrator username and password to log in.

???note "For Domino REST API installed as part of the installation on a *development or test-only environment*, which was only available until Volt MX Go v2.0.4."

    1. Open `http://drapi.mymxgo.com/admin/ui` or your provided Domino REST API hostname concatenated with `/admin/ui` in your browser. 
    2. Enter the following credentials in the login page: 

        - username: `mxgo admin`
        - password: `password` 

        !!! note

            If you updated the administrator's first name, last name, and password in the `values.yaml` file<!--in the [Download the Domino REST API Helm chart](../tutorials/downloadhelmchart.md#download-the-domino-rest-api-helm-chart) procedure-->, use the updated values for the username and password.

    3. Click **Log in**.

## Expected result

A successful login leads you to the Domino REST API landing page. For details on adding and configuring a schema, adding a scope and an application, see [Using Admin UI](https://opensource.hcltechsw.com/Domino-rest-api/references/usingwebui/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Domino REST API documentation.
