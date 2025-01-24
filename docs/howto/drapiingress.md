# Configure Kubernetes Ingress for Domino REST API

--8<-- "devtestenvironment.md"

## About this task

Configures Kubernetes Ingress for Domino REST API. Ingress provides and manages external access to the services in your Kubernetes cluster. It's required to enable browsers to access the applications and back-end services to communicate with each other. 

## Before you begin

Take note of the following information regarding properties and parameters associated with Kubernetes Ingress. The recent improvements have led to variations in the properties and parameters for different versions of Volt MX Go. Refer to the Volt MX Go version for the relevant properties and parameters.
 
### For Volt MX Go v2.1

Familiarize yourself with the following properties and parameters related to Kubernetes Ingress applicable for Volt MX Go v2.1. 

- **ingress.enabled**: Set to `true` to enable Ingress. Ingress must be enabled for Domino REST API to function properly. Kindly note that there are certain conditions where you may want to temporarily disable Ingress.

- **ingress.className**: This property sets the class name on the Ingress object. The default is empty string, which enables the processing of Ingress objects by your cluster default Ingress controller. If your cluster does not have a default Ingress controller or if you want to override that, set the class name. Common values you might use include "nginx", "traefik", and "openshift-default". When utilizing Azure Application Gateway in AKS, specify "azure/application-gateway".

- **ingress.drapiDnsName**: The DNS host name that users will use to access the Domino REST API. The default setting is `drapi.mymxgo.com`.

- **ingress.drapiManagementDnsName**: The DNS host name that administrators will use to access the Domino REST API. The default setting is `drapi-management.mymxgo.com`.

- **ingress.protocol**: The communication protocol for accessing Volt MX Go Foundry. Its value can be either http or https. This should reflect the type of traffic you want the Ingress or Load Balancer to accept. *If `ingress.tls` is enabled, this setting must be https*.

- **ingress.tls**: Use this property to configure Ingress with either a Cluster or a Custom SSL certificate.

- **ingress.tls.enabled**: Set to `true` to configure Ingress to use the Cluster SSL Certificate or the specified Custom SSL certificate.

- **ingress.tls.drapiCustomCert**: Use to specify a Custom SSL certificate for Domino REST API. If `ingress.tls.drapiCustomCert.secretName` is not set, the Cluster SSL certificate will be used for TLS.

- **ingress.tls.drapiCustomCert.secretName**: The filename of the secret file containing the certificate and key.

- **ingress.tls.drapiManagementCustomCert**: Use to specify a Custom SSL certificate for Domino REST API. If `ingress.tls.drapiCustomCert.secretName` is not set, then the Cluster SSL certificate will be used for TLS.

- **ingress.tls.drapiManagementCustomCert.secretName**: The filename of the secret file containing the certificate and key. 

- **ingress.annotations**: Allows you to specify additional annotations that will be added to every ingress object. Add one annotation per line. Each annotation should be indented 2 spaces and of the format  `annotationName: value`. When rendered, your annotation value will automatically be quoted.

### For Volt MX Go v2.0.4 or earlier

Familiarize yourself with the following properties and parameters related to Kubernetes Ingress applicable for Volt MX Go v2.0.4 or earlier.

- **ingress.enabled**: Set to `true` to enable Ingress. Ingress must be enabled for Domino REST API to function properly. Kindly note that there are certain conditions where you may want to temporarily disable Ingress.

- **ingress.className**: This property sets the class name on the Ingress object. The default is empty string, which enables the processing of Ingress objects by your cluster default Ingress controller. If your cluster does not have a default Ingress controller or if you want to override that, set the class name. Common values you might use include "nginx", "traefik", and "openshift-default". When utilizing Azure Application Gateway in AKS, specify "azure/application-gateway".

- **ingress.drapiDnsName**: The DNS host name that users will use to access the Domino REST API. The default setting is `drapi.mymxgo.com`.

- **ingress.drapiManagementDnsName**: The DNS host name that administrators will use to access the Domino REST API. The default setting is `drapi-management.mymxgo.com`.

- **ingress.protocol**: The communication protocol for accessing Volt MX Go Foundry. Its value can be either http or https. This should reflect the type of traffic you want the Ingress or Load Balancer to accept. *If `ingress.tls` is enabled, this setting must be https*.

- **ingress.tls**: Use this property to configure Ingress with either a Cluster or a Custom SSL certificate.

- **ingress.tls.enabled**: Set to `true` to configure Ingress to use the Cluster SSL Certificate or the specified Custom SSL certificate.

- **ingress.tls.drapiCustomCert**: Use to specify a Custom SSL certificate for Domino REST API. If `ingress.tls.drapiCustomCert.cert` and `ingress.tls.drapiCustomCert.key` are not set, the Cluster SSL certificate will be used for TLS.

- **ingress.tls.drapiCustomCert.cert**: The file name for the custom certificate. Place your SSL certificate file in the top level direct `drapi` directory (where `values.yaml` is located). The value of this property should be a file path of the form `my-drapi-custom-cert.cert` where my-drapi-custom-cert.cert is the name of your certificate file. This certificate must be in DER format as per [Section 5.1 of RFC 7468](https://datatracker.ietf.org/doc/html/rfc7468#section-5.1).

- **ingress.tls.drapiCustomCert.key**: The file name for the custom key. Place your SSL certificate key file in the top level direct 'drapi' directory (where values.yaml is located). The value of this property should be of the form `my-drapi-custom-cert.key` where my-drapi-custom-cert.key is the name of your private key file. The key file must be PKCS #8 in DER format [Section 11 of RFC 7468](https://datatracker.ietf.org/doc/html/rfc7468#section-11).

- **ingress.tls.drapiManagementCustomCert**: Use to specify a Custom SSL certificate for Domino REST API. If `ingress.tls.drapiCustomCert.cert` and `ingress.tls.drapiCustomCert.key` are not set, then the Cluster SSL certificate will be used for TLS.

- **ingress.tls.drapiManagementCustomCert.cert**: The file name for the custom certificate. Place your SSL certificate file in the top level direct `drapi` directory (where `values.yaml` is located). The value of this property should be a file path of the form `my-drapi-mgmt-custom-cert.cert` where my-drapi-mgmtcustom-cert.cert is the name of your certificate file. This certificate must be in DER format as per [Section 5.1 of RFC 7468](https://datatracker.ietf.org/doc/html/rfc7468#section-5.1).

- **ingress.tls.drapiManagementCustomCert.key**: The file name for the custom key. Place your SSL certificate key file in the top level direct 'drapi' directory (where values.yaml is located).   The value of this property should be of the form `my-drapi-mgmt-custom-cert.key` where my-drapi-mgmt-custom-cert.key is the name of your private key file. The key file must be PKCS #8 in DER format [Section 11 of RFC 7468](https://datatracker.ietf.org/doc/html/rfc7468#section-11).

- **ingress.annotations**: Allows you to specify additional annotations that will be added to every ingress object. Add one annotation per line. Each annotation should be indented 2 spaces and of the format  `annotationName: value`. When rendered, your annotation value will automatically be quoted.

## Additional information

You can configure Kubernetes Ingress to accept connections over HTTP or HTTPS. HTTP isn't secure but works without any extra configuration. It's recommended to use HTTPS for most deployments.

!!!note
    You can't easily change the deployment domain name once installed, this includes changing from HTTP to HTTPS. For more information, see [How to change Hostname/IP address and port details of Volt MX Go Foundry Server?](https://support.hcltechsw.com/csm?id=kb_article&sysparm_article=KB0089025).

One approach to enable HTTPS is to use a self-signed SSL certificate, which avoids purchasing your own certificate from a Certificate Authority (CA). However, since Volt MX Go Foundry makes back-end server to server requests between applications, there are more steps to enable Volt MX Go Foundry to trust the secured communication channel when utilizing a self-signed certificate.

If you configure your Kubernetes Ingress to use a self-signed SSL certificate or an SSL certificate from your enterprise's own Certificate Authority that's not within a trusted root certification path, or if you use the cluster default cert created from a self-signed CA, you need to add the SSL certificate or CA certificate to the trust store used by Tomcat. Failure to do so results in runtime errors when Volt MX Go Foundry components need to communicate with each other. For more information, see [Certification Authority Trust Model](http://technet.microsoft.com/en-us/library/cc962065.aspx).

## Procedure

!!! note
    In general, perform the following procedure before installing Volt MX Go Foundry to enable secure HTTPS communication.

### For Volt MX Go v2.1

1. Obtain SSL Certificates. You can use any of the following options:

    - Purchase a certificate from a trusted Certificate Authority.

    - Obtain a free certificate from [Let's Encrypt](https://letsencrypt.org/) or [ZeroSSL](https://zerossl.com).

    - Create a self-signed certificate.

        ??? info "To create a self-signed certificate" 

            1.  Generate new self-signed certificates:
                
                ```text
                keytool -v -genkey -keyalg RSA -keystore drapi.keystore -alias drapi -ext SAN=dns:drapi.example.com -dname "cn=drapi.example.com" -storepass changeit -validity 365

                keytool -v -genkey -keyalg RSA -keystore drapi-management.keystore -alias drapi-management -ext SAN=dns:drapi-management.example.com -dname "cn=drapi-management.example.com" -storepass changeit -validity 365
                ```

                !!! note
                     Make sure to replace `drapi.example.com` with your domain name. You can specify a wild card cert like `*.example.com` that would enable using a DNS name like `drapi.example.com` or `mydrapi.example.com` without changing the certificate. Likewise, do the same for `drapi-management.example.com`. These commands create new keystores called `drapi.keystore` and `drapi-management.com` with a single entry, each containing a new self-signed certificate.

            2.  Get the private keys from the respective keystores:
                
                ```text
                openssl pkcs12 -in drapi.keystore -nodes -nocerts -out drapi-server.key
                openssl pkcs12 -in drapi-management.keystore -nodes -nocerts -out drapi-management-server.key
                ```

            3.  Get the certificates from the respective keystores:
                
                ```text
                openssl pkcs12 -in drapi.keystore -nokeys -out drapi-server.crt
                openssl pkcs12 -in drapi-management.keystore -nokeys -out drapi-management-server.crt
                ```

    - Use the Kubernetes default cluster certificate by pulling it from your cluster.

        ??? info "To obtain default Cluster Certificate"

            - Obtain the cluster's SSL certificate by running the `openssl` command:

                ```text
                openssl s_client -connect my-openshift-ingress:443 -servername drapi.example.com 2>/dev/null </dev/null | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > ~/drapi-server.pem
                ```

                !!!note
                    The parameter following `-connect` must be a DNS name or IP address that resolves to your OpenShift ingress. The `-servername` parameter specifies the DNS name you use to access your Volt MX Go Foundry deployment. This should match the value you specified for `serverDomainName` in `values.yaml`. The DNS names could be the same as long as they resolve to the IP address of your Kubernetes load balancer in front of Ingress or Ingress itself.


2. Create a Kubernetes secret with your SSL certificate details.
    
    Create a secret file with your SSL certificate and keys on the same namespace where you will install Domino REST API by running the following command:

    ```
    kubectl create secret tls drapi-secret --cert=path/to/tls.crt --key=path/to/tls.key -n namespace
    ```
    wherein:

    - `drapi-secret` is the name of the secret file
    - `--cert=path/to/tls.crt` is the path to the certificate file
    - `--key=path/to/tls.key` is the path to the key file
    - `-n namespace` is the namespace where you want to install Domino REST API

3. Update the Helm `values.yaml`.

    Update your `values.yaml` with the configuration details you used to create the secret file to configure SSL. Check the notes for specific use cases and refer to Kubernetes Ingress details in [Before you begin](#before-you-begin) for more details on each parameter.


    ``` bash
    ingress.enabled: true
    ingress.drapiDnsName: drapi.example.com
    ingress.drapiManagementDnsName: drapi-management.example.com
    ingress.protocol: "https"
    ingress.tls.enabled: true
    ingress.tls.drapiCustomCert.secretName: "drapi-secret"
    ingress.tls.drapiManagementCustomCert.secretName: "drapi-secret"
    ```

    !!!note
        The `drapiCustomCert.secretName` and `drapiManagementCustomCert.secretName` details can be omitted when using the default cluster certificate. If you go with this approach, make sure that the DNS hostname which you will access the deployment with matches the host name details in the certificate. Otherwise, the backend communication will fail because the host name doesn't match.

Return to [Deploy Domino REST API](../tutorials/downloadhelmchart.md#deploy-domino-rest-api).

### For Volt MX Go v2.0.4 or earlier

1. Obtain SSL Certificates. You can use any of the following options:

    - Purchase a certificate from a trusted Certificate Authority.

    - Obtain a free certificate from [Let's Encrypt](https://letsencrypt.org/) or [ZeroSSL](https://zerossl.com).

    - Create a self-signed certificate.

        ??? info "To create a self-signed certificate" 

             1. Generate new self-signed certificates:
                    
                ```text
                keytool -v -genkey -keyalg RSA -keystore drapi.keystore -alias drapi -ext SAN=dns:drapi.example.com -dname "cn=drapi.example.com" -storepass changeit -validity 365

                keytool -v -genkey -keyalg RSA -keystore drapi-management.keystore -alias drapi-management -ext SAN=dns:drapi-management.example.com -dname "cn=drapi-management.example.com" -storepass changeit -validity 365
                ```

                !!!note
                    Make sure to replace `drapi.example.com` with your domain name. You can specify a wild card cert like `*.example.com` that would enable using a DNS name like `drapi.example.com` or `mydrapi.example.com` without changing the certificate. Likewise, do the same for `drapi-management.example.com`. These commands create new keystores called `drapi.keystore` and `drapi-management.com` with a single entry, each containing a new self-signed certificate.

             2. Get the private keys from the respective keystores:
                    
                ```text
                openssl pkcs12 -in drapi.keystore -nodes -nocerts -out drapi-server.key
                openssl pkcs12 -in drapi-management.keystore -nodes -nocerts -out drapi-management-server.key
                ```

             3. Get the certificates from the respective keystores:
                    
                ```text
                openssl pkcs12 -in drapi.keystore -nokeys -out drapi-server.crt
                openssl pkcs12 -in drapi-management.keystore -nokeys -out drapi-management-server.crt
                ```

            4. Get the PEM portion from the certificate for Domino REST API only:
                    
                ```text
                cat drapi-server.crt | sed -ne '/-BEGIN CERTIFICATE/,/END CERTIFICATE/p' > ./drapi-server.pem
                ```

            5. Proceed to the *Step 3. Import certificate into the truststore with keytool*.

    - Use the Kubernetes default cluster certificate by pulling it from your cluster.

        ??? info "To obtain default Cluster Certificate"

             1. Obtain the cluster's SSL certificate by running the `openssl` command:

                ```text
                openssl s_client -connect my-openshift-ingress:443 -servername drapi.example.com 2>/dev/null </dev/null | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > ~/drapi-server.pem
                ```

                !!!note
                    The parameter following `-connect` must be a DNS name or IP address that resolves to your OpenShift ingress. The `-servername` parameter specifies the DNS name you use to access your Volt MX Go Foundry deployment. This should match the value you specified for `serverDomainName` in `values.yaml`. The DNS names could be the same as long as they resolve to the IP address of your Kubernetes load balancer in front of Ingress or Ingress itself.


             2. Proceed to *Step 3. Import certificate into the truststore with keytool*.

2. Copy your SSL certificates and keys into the Domino REST API top level directory.

    !!!tip
        Helm creates a Kubernetes secret with your SSL certificate details in it for use by Ingress. 
        
    1. Copy the SSL certificate and key files into the top level direct `drapi` directory where `values.yaml` is located by running the following commands. It's assumed that you will run the commands in the directory where you unzipped the Helm charts.

        ```bash
        cp ~/drapi-server.crt   .
        cp ~/drapi-management-server.crt   .
        cp ~/drapi-server.key   .
        cp ~/drapi-management-server.key   .
        ```

    2. Proceed to *Step 4. Update the Helm `values.yaml`* to update the parameters with these file names.

3. Import certificate into the truststore with keytool.

    !!!warning "Important"
        If your SSL certificate is issued by a trusted root CA, you can skip this step. 

    - Use the Java utility `keytool` to import the certificate by running the following command. It's assumed that you will run the command from the root of the directory where you unzipped the Helm charts.   


    ``` bash
    # Make foundry aware of the drapi cert:
    keytool -import -alias drapi2 -file ./drapi-server.pem -keypass changeit -storepass changeit -keystore ../foundry/voltmx-foundry/certs/cacerts
    ```

    !!!note
        - `-alias drapi2` is the alias for the new certificate. You can use any alias but we recommend foundry.
        - `-file ./drapi-server.pem` is the file path to your certificate. Use the proper path for your circumstances.
        - `-keystore ../foundry/voltmx-foundry/certs/cacerts` is the location of the truststore your certificate will be imported to and later use by Tomcat. This file path shouldn't be changed.
        - `changeit` is the default password and shouldn't be changed.

    For more information about `keytool`, see [Java Keytool documentation](https://docs.oracle.com/en/java/javase/11/tools/keytool.html).

4. Update the Helm `values.yaml`.

    Update your `values.yaml` with the following configuration details to configure SSL. Check the notes for specific use cases and refer to Kubernetes Ingress details in [Before you begin](#before-you-begin) for more details on each parameter.

    ``` bash
    ingress.enabled: true
    ingress.drapiDnsName: drapi.example.com
    ingress.drapiManagementDnsName: drapi-management.example.com
    ingress.protocol: "https"
    ingress.tls.enabled: true
    ingress.tls.drapiCustomCert.cert: “drapi-server.crt”
    ingress.tls.drapiCustomCert.key: “drapi-server.key”
    ingress.tls.drapiManagementCustomCert.cert: “drapi-management-server.crt”
    ingress.tls.drapiManagementCustomCert.key: “drapi-management-server.key”
    ```

    !!!note
        - The path for the customCert properties is relative to the `apps` directory. It should always be `certs/` followed by your certificate or key file name.
        - The `drapiCustomCert.cert`, `drapiCustomCert.key`, `drapiManagementCustomCert.cert`, and `drapiManagementCustomCert.key` details can be omitted when using the default cluster certificate. If you go with this approach, make sure that the DNS hostname which you will access the deployment with matches the host name details in the certificate. Otherwise, the backend communication will fail because the host name doesn't match.

Return to [Deploy Domino REST API](../tutorials/downloadhelmchart.md#deploy-domino-rest-api).

