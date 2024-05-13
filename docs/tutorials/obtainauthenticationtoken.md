# Obtain authentication token from HCL Container Repository

## About this task

The binary images and Helm charts for Volt MX Go server components are pulled from the HCL Container Repository. This requires you to get your authentication token from the HCL Container Repository. This task guides you on how to obtain your authentication token.

## To obtain your authentication token

1. Go to the [HCL Container Repository](https://hclcr.io){: target="_blank" rel="noopener noreferrer"}.
2. On the login page, click **LOGIN VIA OIDC Provider**, and then login using your corporate email address.
3. On the **Projects** page, click your username and select **User Profile**.

    ![search project](../assets/images/harborproject.png)

4. On the **User Profile** dialog, copy the value of the **CLI secret** by clicking the copy icon.

    ![user profile dialog](../assets/images/userprofile.png)

5. Save the **CLI secret** value as it's required in the next steps.

    !!!note
        You will use the **CLI secret** value as your authentication token or password when using Docker or Helm CLI to access HCL Container Repository.

6. Take note of exactly how your email address is written in the **User Profile** dialog as authentication is case sensitive on the user email.

## Next step

For installing Volt MX Go using helm charts on a supported Kubernetes platform for a production environment, proceed to [Configure Helm to pull from HCL Container Repository](nativeinstallers.md#1-create-a-namespace-and-a-temp-directory-for-the-charts).

For installing Volt MX Go to **development or test only environment**, proceed to [Deploy Kubernetes](deploykubernetes.md).