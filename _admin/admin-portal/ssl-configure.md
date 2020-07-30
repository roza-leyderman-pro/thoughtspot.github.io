---
title: [Configure SSL]
last_updated: 7/27/2020
summary: Secure socket layers (SSL) provide authentication and data security when sending data to and from ThoughtSpot.
toc: true
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
You can use your own SSL certificate to secure ThoughtSpot HTTP(S) traffic.

{: id="ssl-about"}
## About SSL
To enable SSL for the ThoughtSpot web service, you must provide your organization's SSL certificate for the ThoughtSpot service URL.  If you do not have this certificate, you have the following options:

-   Check with your IT department if they have an SSL certificate you can use.
-   Obtain the certificate from an issuing authority.
-   Use the default SSL certificate on the ThoughtSpot nodes.
-   Disable SSL using the `tscli ssl off` command.

ThoughtSpot supports a wide variety of SSL types.

{: id="ssl-ports"}
## Required ports

To use the ThoughtSpot web service securely, ensure that TCP port 443 is open to accommodate incoming connections to ThoughtSpot nodes and clusters.

{: id="ssl-configure"}
## Prerequisites
To add SSL and enable HTTPS in ThoughtSpot, you must generate the [Certificate Signing Request (CSR)](#csr) and obtain the [SSL certificate chain](#ssl-certificate-chain) and the [private key](#key).

{: id="csr"}
### Certificate Signing Request
When you generate a CSR, you handle sensitive data. Therefore, ThoughtSpot recommends that its customers generate their own CSRs.

You can generate a CSR in several ways. Most often, you generate a CSR and a new private key [at the same time](#csr-new-private-key). If you already have a private key, [use it to generate a CSR](#csr-existing-private-key).

{: id="csr-new-private-key"}
Follow these steps to generate a CSR and a private key. You need a computer you can run Linux commands on, and a recent version of *openssl*.

1. `ssh` into one of your ThoughtSpot nodes.
    ```
    ssh admin@<node_IP>
    ```
2. Run the command to generate a CSR and private key pair:
    ```
    openssl req -new -newkey rsa:2048 -nodes -out csr.pem -keyout pk.key[-subj "/key1=value1/key2=value with space/"]
    ```

    Note the following parameters:
    * ThoughtSpot supports a 2048 or 4096 bit key.
    * `subj`: a common subject. Logically equivalent to the `-dname` property of *keytool*. Alternatively, you can skip this flag, and `openssl` prompts you to enter this information interactively.
    * Optionally, run `add-multivalue-rdn` to allow multiple values to be set for the same key.
    * Run `man req` for more details.

{: id="csr-existing-private-key"}
If you already have a private key, you can use it to generate a CSR. Follow these steps to generate a CSR with an existing private key:

1. `ssh` into one of your ThoughtSpot nodes.
    ```
    ssh admin@<node_IP>
    ```
2. Run the command to generate a CSR and private key pair:
    ```
    openssl req -new -key <private_key_file> -nodes -out csr.pem[-subj "/key1=value1/key2=value with space/"]
    ```

    Specify the existing private key file. Refer to the parameters listed above.

{: id="ssl-certificate-chain"}
### SSL certificate chain
The SSL certificate chain must be in PEM format, which is an `X.509v3` file that contains ASCII (Base64) armored data, packed between `BEGIN` and `END` directives. The certificate chain may contain a series of certificates, with the root certificate at the bottom and user-facing, while the ThoughtSpot-specific SSL certificate is at the top.

{: id="key"}
### Private key
The private key must also be in compatible PEM format. It cannot be password-protected, or passphrase-protected.

{% include note.html content="Do not use a passphrase when creating certificates with ThoughtSpot." %}

If you are prompted to specify a passphrase, first check if it exists by invoking the following command:

```
openssl rsa -check -in pk.key`
```

If the answer is 'yes', you must remove the passphrase first, and then proceed to use the private key with ThoughtSpot.

{% include content/admin-portal/ssl-configure.md %}

{: id="config-load-balancer"}
### Configuration string for load balancers

When enabling SSL support on a load balancer’s server-side SSL client profile, make sure to add support for the following ciphers to ensure compatibility between the load balancer and ThoughtSpot.

The following ciphers are currently supported:

```
|   TLSv1.2:
|     ciphers:
|       TLS_DHE_RSA_WITH_AES_128_GCM_SHA256 - strong
|       TLS_DHE_RSA_WITH_AES_256_CBC_SHA - strong
|       TLS_DHE_RSA_WITH_AES_256_CBC_SHA256 - strong
|       TLS_DHE_RSA_WITH_AES_256_GCM_SHA384 - strong
|       TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 - strong
|       TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA - strong
|       TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384 - strong
|       TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 - strong
|     compressors:
|       NULL
|_  least strength: strong
```

The cipher string would be as follows:

```
EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH
```

You can retrieve these from the ThoughtSpot web server (not against the load balancer) by running the following command on any ThoughtSpot node:
    ```
    nmap --script ssl-enum-ciphers -p 443 <ThoughtSpot_node_IP_address>
    ```
You must ensure that your load balancer supports these ciphers.

{: id="ssl-configure-test"}
## Test the SSL certificate

To test if the certificate is installed correctly, see [Sign in to the ThoughtSpot application]({{ site.baseurl }}/admin/setup/logins.html#sign-in-to-the-thoughtspot-application).