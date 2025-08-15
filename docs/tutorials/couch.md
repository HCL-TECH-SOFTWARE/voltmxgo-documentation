# Apache CouchDB adapter tutorial

## About this task




Apache CouchDB and CouchDB are trademarks of The Apache Software Foundation

## Before you begin

- You have an active CouchDB instance, and your Volt Foundry server is able to connect to the CouchDB host via HTTP/HTTPS.
- Within your Volt Foundry server, a test environment is already defined. It will be used for API testing, as will be described in the latter part of this tutorial.

    For more information on creating a test environment, see [Add an environment](adaptertutorial.md#add-an-environment).

## Assumptions

Before starting this tutorial, review the following assumptions to make sure you can follow the procedures.

For the purpose of this tutorial, it's assumed that:

- You already have a test environment set up, referred to as **localdevenv**.

- You have a CouchDB database named *population*, hosted on a machine with the hostname *couchdb*.

    The *population* database contains data on the populations of cities across multiple continents, including Asia, Africa, and North America. A sample document in this database looks like the following:

    ```json
    {
    "_id": "11381c61-b182-4fed-bd1b-6453a24c6b8b",
    "_rev": "6-5bdb9d619b82cb45db1d656c849c5c6c",
    "continent": "AS",
    "country": "China",
    "name": "Beijing",
    "population": 513,
    "censusdate": "2023-10-15T00:00:00Z",
    "grads": 100,
    "phds": 50
    }
    ```

- The CouchDB database includes fives views named:

    - **african_cities**
    - **all_cities**
    - **asian_cities**
    - **eu_cities**
    - **north_american_cities**

    For example, the **african_cities** view uses the following map function to filter what documents should show up.

    ```javascript
    function (doc) { 
        if (doc.continent === 'AF') 
            emit(doc.country, doc.name, doc.population);
    }
    ```

    The **asian_cities** view has the following map function:

    ```javascript
    function (doc) { 
        if (doc.continent === 'AS') 
            emit(doc.country, doc.name, doc.population); 
    }    
    ```

## Log in to Volt Foundry

1. Open your browser and navigate to the Volt Foundry hostname followed by `/mfconsole/`.

    !!! tip

        Use the **Console URL** provided in the **Install Complete** window or from the *Installation Complete* details displayed in the command line to access Volt Foundry.

2. On the **Sign in to your account** page, enter your username and password.
3. Click **Sign In**.  

   The **Volt MX Foundry Console** opens, displaying the **Apps** page by default.

## Configure an object service for Apache CouchDB 

1. In the left pane of the **Volt MX Foundry Console**, click **API Management**.
2. On the **APIs** page, navigate to **Objects**, then click **Configure New**.
3. Enter the object service name in the **Name** text field.
4. Select **Apache CouchDB** from the **Business Adapters** options under **Endpoint Type**.
5. Set the **Metadata Security Level** to **Authenticated App Users**.
6. Under **Connection Parameters**:

    1. Enter the host name and the port where the CouchDB instance is hosted in the **CouchDB host URI** and **Port** text fields.

        !!! note

            Cluster is not yet supported.

    2. Enter your CouchDB credentials in the **User name** and **Password** text fields.
    3. Click **Test Connection** to make sure that the connection works.

    !!! tip

        - Make sure to select the environment you added before clicking **Test Connection**. 
        - If the test fails, make sure that the entered connection parameters are correct and update as needed.

7. Click **Save and Configure**.

!!! note

    The Apache CouchDB adapter communicates with the CouchDB instance using CouchDB’s RESTful HTTP/HTTPS API. For the adapter to work, HTTP or HTTPS traffic must be allowed between the Volt Foundry server and the CouchDB instance.

## Generate a data model

1. On the **Data Model** tab, click **Generate**.