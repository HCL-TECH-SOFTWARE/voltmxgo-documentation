# DRAPI Ingress

## Ingress Details

    - **Overview**: Ingress provides external access to the services in your Kubernetes cluster.  It is required to enable browsers to access the applications and also used by the backend services to communicate with each other.

    - **ingress.enabled**: true if Ingress should be enabled.  Ingress must be enabled for DRAPI to function properly, but there are certain conditions where you may want to temporarily disable Ingress.

    - **ingress.className**: The className property is used to set the class name on the Ingress object.  The default is empty string which will enable the Ingress objects to be processed by your cluster default Ingress controller.  If your cluster does not have a default Ingress controller or if you want to override that, you can set the class name here.  Common values you might use include "nginx", "traefik", and "openshift-default". When utilizing Azure Application Gateway in AKS specify "azure/application-gateway".

    - **ingress.drapiDnsName**: The DNS host names that users will use to access the Domino REST API. The default setting is "drapi.mymxgo.com".

    - **ingress.drapiManagementDnsName**: The DNS host names that administrators will use to access the Domino REST API. The default setting is "drapi-management.mymxgo.com".

    - **ingress.protocol**: The communication protocol for accessing Volt MX Foundry. This value can be either http or https.  This should reflect the type of traffic you want the Ingress or Load Balancer to accept. **Note:** If ingress.tls is enabled, this setting must be https.

    - **ingress.tls**: Use this property to configure Ingress with either the Cluster or a Custom SSL certificate.

    - **ingress.tls.enabled**: When this property is set to true, Ingress is configured to use the Cluster SSL Certificate or the specified Custom SSL certificate.

    - **ingress.tls.drapiCustomCert**: Use this property to specify a Custom SSL certificate for DRAPI. If ingress.tls.drapiCustomCert.cert and ingress.tls.drapiCustomCert.key are not set, then the Cluster SSL certificate will be used for tls.

    - **ingress.tls.drapiCustomCert.cert**: The file name for the custom certificate.  Place your SSL certificate file in the top level direct 'drapi' directory (where values.yaml is located).  The value of this property should be a file path of the form `my-drapi-custom-cert.cert` where my-drapi-custom-cert.cert is the name of your certificate file.  This certificate must be in DER format as per [Section 5.1 of RFC 7468](https://datatracker.ietf.org/doc/html/rfc7468#section-5.1).

    - **ingress.tls.drapiCustomCert.key**: The file name for the custom key.  Place your SSL certificate key file in the top level direct 'drapi' directory (where values.yaml is located).  The value of this property should be of the form `my-drapi-custom-cert.key` where my-drapi-custom-cert.key is the name of your private key file.  The key file must be PKCS #8 in DER format [Section 11 of RFC 7468](https://datatracker.ietf.org/doc/html/rfc7468#section-11).

    - **ingress.tls.drapiManagementCustomCert**: Use this property to specify a Custom SSL certificate for DRAPI. If ingress.tls.drapiCustomCert.cert and ingress.tls.drapiCustomCert.key are not set, then the Cluster SSL certificate will be used for tls.

    - **ingress.tls.drapiManagementCustomCert.cert**: The file name for the custom certificate.  Place your SSL certificate file in the top level direct 'drapi' directory (where values.yaml is located).   The value of this property should be a file path of the form `my-drapi-mgmt-custom-cert.cert` where my-drapi-mgmtcustom-cert.cert is the name of your certificate file.  This certificate must be in DER format as per [Section 5.1 of RFC 7468](https://datatracker.ietf.org/doc/html/rfc7468#section-5.1).

    - **ingress.tls.drapiManagementCustomCert.key**: The file name for the custom key.  Place your SSL certificate key file in the top level direct 'drapi' directory (where values.yaml is located).   The value of this property should be of the form `my-drapi-mgmt-custom-cert.key` where my-drapi-mgmt-custom-cert.key is the name of your private key file.  The key file must be PKCS #8 in DER format [Section 11 of RFC 7468](https://datatracker.ietf.org/doc/html/rfc7468#section-11).

    - **ingress.annotations**:  ingress.annotations allow you to specify additional annotations that will be added to every ingress object.  Add one annotation per line, each annotation should be indented 2 spaces and should be of the format of `annotationName: value`.  When rendered, your annotation value will automatically be quoted.



## Configuring Kubernetes Ingress with SSL Certificate Support

Ingress can be configured to accept connections over HTTP or HTTPS.  HTTP is insecure (information is sent in plain text, no encryption), but it works without any additional configuration.  We recommend utilizing HTTPS for most deployments.  Keep in mind you cannot easily change the deployment domain name once installed, this includes changing from HTTP to HTTPS (see [https://support.hcltechsw.com/csm?id=kb_article&sysparm_article=KB0089025](https://support.hcltechsw.com/csm?id=kb_article&sysparm_article=KB0089025) for details).

You have several options to enable HTTPS.  One approach is to utilize a self-signed SSL certificate.  This avoids requiring the purchase of your own certificate from a Certificate Authority (CA).  However, because Foundry makes back end server to server requests between various applications, there are additional steps required to enable Foundry to trust the secured communication channel when utilizing a self-signed certificate.

If your Kubernetes Ingress will be configured to use a self-signed SSL certificate or if you get a SSL certificate from your enterprise's own Certificate Authority that is not within a trusted root certification path (or if you utilize the cluster default cert that was created from a self-signed CA), you will need to add the SSL certificate or CA certificate to the trust store that is utilized by Tomcat.  Failure to do this will result in runtime errors when Foundry components need to communicate with each other.  More details on the Certification Authority Trust Model can be found [here](http://technet.microsoft.com/en-us/library/cc962065.aspx).  In general the following steps must be done prior to installing Foundry to enable secure HTTPS communication:

1.  Obtain the SSL Certificates to use with Ingress for DRAPI and DRAPI Management (certificate and key)
2.  Copy the certificate and key into the Helm chart so Helm can configure Ingress to use the certificate
3.  Import the SSL or CA certificate into the truststore which will be used by Tomcat during server to server communication
4.  Update your values.yaml
5.  [Install Domino REST API](#install-domino-rest-api)


## Obtain the SSL Certificates

Unless you plan on using the default cluster SSL certificate, you need to obtain SSL certificates.  For test purposes you could [create a self-signed certificate](#create-a-self-signed-certificate) or you might purchase a certificate from a trusted Certificate Authority or obtain a free certificate from [Let's Encrypt](https://letsencrypt.org/) or [ZeroSSL](https://zerossl.com).  Any of these steps should result in obtaining a certificate and key file.

If you are going to utilize the Kubernetes default cluster certificate, [pull the certificate from your cluster](#obtain-default-cluster-certificate) as this likely will need to be imported into the trust store.

## Copy your SSL Certificates and Keys into the DRAPI top level directory

Helm will create a Kubernetes secret with your SSL certificate details in it for use by Ingress.  You must copy the SSL certificate and key files into the top level direct 'drapi' directory (where values.yaml is located).  The example commands below assume your current directory is the location where you unzipped the Helm charts:

``` bash
cp ~/drapi-server.crt   .
cp ~/drapi-management-server.crt   .
cp ~/drapi-server.key   .
cp ~/drapi-management-server.key   .
```

You will need to update some parameters in `values.yaml` with these file names in subsequent steps below.


## Import the Certificate into the truststore with keytool

If your SSL Certificate was issued by a trusted root CA, you can skip this step.  Otherwise, use the Java utility `keytool` to import the certificate.  See [Java Keytool documentation](https://docs.oracle.com/en/java/javase/11/tools/keytool.html) for more details.  An example command follows and again we assume it is run from the root of the directory where you unzipped the Helm charts:

``` bash
# Make foundry aware of the drapi cert:
keytool -import -alias drapi2 -file ./drapi-server.pem -keypass changeit -storepass changeit -keystore ../foundry/voltmx-foundry/certs/cacerts
```

Notes:

* `-alias drapi2` is the alias for the new certificate.  You can use any alias you want but we recommend foundry.
* `-file ./drapi-server.pem` is the file path to your certificate.  Use the proper path for your circumstances.
* `-keystore ../foundry/voltmx-foundry/certs/cacerts` is the location of the truststore your certificate will be imported to and later use by Tomcat.  This file path should not be changed.
* `changeit` is the default password and should not be changed.

## Update the necessary Helm `values.yaml`

To properly configure SSL, you will need to update your `values.yaml`.  General details follow, but be sure to check the notes section for specific use cases.  You may also refer to the [Configuration](./Installing_Containers_With_Helm.md#configuration) section for more details on each parameter.


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

Notes:

* the path for the customCert properties is relative to the `apps` directory.   It should always be `certs/` followed by your certificate or key file name.
* the `drapiCustomCert.cert`, `drapiCustomCert.key`, `drapiManagementCustomCert.cert`, and `drapiManagementCustomCert.key` details can be omitted when using the default cluster certificate.  If you go with this approach, you need to ensure the DNS hostname which you will access the deployment with matches the host name details in the  certificate or the backend communication will fail because the host name doesn't match.


## Obtain default Cluster Certificate

The following procedure should be done to obtain your default cluster certificate if you plan to use that and the certificate is self-signed or was not created by trusted root CA.   Two server addresses are specified here: the parameter following `-connect` must be a DNS name or IP address that resolves to your OpenShift ingress.  The `-servername` parameter specifies the DNS name you will use to access your foundry deployment (this should match the value you are specifying for `serverDomainName` in values.yaml).  These could be the same DNS names, they must properly resolve to the IP address of your Kubernetes load balancer in front of Ingress or Ingress itself.

Obtain the cluster's SSL certificate with the `openssl` command:

``` bash
openssl s_client -connect my-openshift-ingress:443 -servername drapi.example.com 2>/dev/null </dev/null | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > ~/drapi-server.pem
```

Note at this point you only have the certificate, there is no key file associated with this default cluster cert.  Follow the steps to [import this into the trust store](#import-the-certificate-into-the-truststore-with-keytool).

## Create a Self-Signed Certificate

The following procedure could be used to generate a self-signed certificate:

1.  Generate new self-signed certificates:
    <pre><code>
    keytool -v -genkey -keyalg RSA -keystore drapi.keystore -alias drapi -ext SAN=dns:drapi.example.com -dname "cn=drapi.example.com" -storepass changeit -validity 365

    keytool -v -genkey -keyalg RSA -keystore drapi-management.keystore -alias drapi-management -ext SAN=dns:drapi-management.example.com -dname "cn=drapi-management.example.com" -storepass changeit -validity 365
    </pre></code>

    Make certain you replace "drapi.example.com" with your domain name.  You can specify a wild card cert like `*.example.com` which would enable using a dns name like drapi.example.com or mydrapi.example.com without changing the certificate. Likewise, you will do the same for "drapi-management.example.com. These commands will create new keystores called `drapi.keystore` and `drapi-management.com` with a single entry in eachit containing a new self-signed certificate.

2.  Get the private keys from the respective keystores:
    <pre><code>
    openssl pkcs12 -in drapi.keystore -nodes -nocerts -out drapi-server.key
    openssl pkcs12 -in drapi-management.keystore -nodes -nocerts -out drapi-management-server.key
    </pre></code>
3.  Get the certificates from the respective keystores:
    <pre><code>
    openssl pkcs12 -in drapi.keystore -nokeys -out drapi-server.crt
    openssl pkcs12 -in drapi-management.keystore -nokeys -out drapi-management-server.crt
    </pre></code>
4.  Get the PEM portion from the certificate for drapi only:
    <pre><code>
    cat drapi-server.crt | sed -ne '/-BEGIN CERTIFICATE/,/END CERTIFICATE/p' > ./drapi-server.pem
    </pre></code>

    Follow the steps to [import drapi-server.pem into the trust store](#import-the-certificate-into-the-truststore-with-keytool).


Return to [Deploy Domino REST API](../tutorials/downloadhelmchart.md#2-deploy-domino-rest-api)

