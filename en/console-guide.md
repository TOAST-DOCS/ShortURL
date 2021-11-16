## Application Service > ShortURL > Console User Guide

## URL

### Shortened URL added
- In **View > URL** tab, click the **Add URL** button to add a new shortened URL.
- Select a full URL and domain to add a new shortened URL.
- To create a URL you want, select **URL Type > Manually Enter** and enter the URL you want.
- **Opening Date** and **Expiry Date** indicates the period during which users can access through the added URL, which is useful when you want to prohibit user access after a specific date and time.

### View shortened URL
- In **View > URL** tab, you can check the added URL information.
- Enter **Domain**, **Status**, and **Search Term** to search for a URL.
- Click **Copy** button to easily copy the link.
- Click the **Disable** button to block the access to the shortened URL currently in use at any time.
- Click the **Delete** button to delete a shortened URL no longer used.



## Campaign

### Add campaign
- In **View > Campaign** tab, click the **Add Campaign** button to add a new campaign.
- **Campaign** is an event group that can include a multiple number of shortened URLs.
- Add a URL you want in **Affiliated URL** to manage it.
- Click the **Edit** button to add or delete **Affiliated URL**.
- Click the **More** button to see the list of the shortened URLs included in the campaign.

### View campaign
- In **View > Campaign** tab, you can check the **Campaign** information.
- Enter **Domain**, **Status**, and **Search Term** to search for a campaign.


## Domain

### Register DNS
> IP: 43.227.116.15
- **Domain** can be added only after the **Domain** is registered with the above IP of the DNS server.
    - **A record** is checked for its validation; thus, **A record** must be present.
- **nslookup** command can be used to check if DNS is properly registered as shown below.

```bash
...
Name:   nh.nu
Address: 43.227.116.15
```

### Add domain
- In **Manage > Domain** tab, click the **Add Domain** button to add a domain owned by users.
- Checks if the IP is a shortened URL server IP when registering a **Domain**.
- **Open Range** allows multiple projects within the same organization to share and use a **Domain**.
- Click the **More** button to see more information on the domain.
- The registered **Domain** cannot be re-registered in another organization or project.

### View domain
- In **Manage > Domain** tab, you can check the **Domain** information.
- Click the **More** button to see more information on the domain.



## Certificate

### Certificate file format
- Only certificate in **.pem** format is supported.
- Only a certificate of which [Passphrase](https://github.com/TOAST-DOCS/ShortURL/pull/1/files#passphrase-삭제) is deleted can be added.
- The file contains a certificate (chain) information and private key information.

```
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```

### Delete passphrase
- A passphrase can be deleted using the following command.

```bash
openssl rsa -in input.key -out output.key
```

### How to create a certificate file (.pem)
1. Convert the certificate information into **.pem** format.
2. Create a single **.pem** file that includes a certificate chain and a private key.

```bash
cat mydomain.crt mydomain.key root-ca-chain.pem > mydomain.pem
```

- This is an example of simply integrating them into a single result.pem file using the - **cat** command result.pem.
- Make sure to open the integrated result.pem file with a text editor and check the different pieces of PEM information are all separated.
- Root/chain certificate could be a little different.


### Add certificate
- -In **Manage > Certificate** tab, click the **Add Certificate** button to add a certificate owned by users.
- When a **Certificate** is uploaded, the certificate is validated. If the certificate is validated to be usable, the information is automatically displayed on the console.
    - You cannot use a certificate already in use.
- **Open Range** allows multiple projects within the same organization to share and use a **Certificate** 
    - In the case of a *_wildcard* certificate, only one can be registered; therefore, the certificate must be shared to be able to make it usable.
- Click the **More** button to see more information on the certificate.
- The registered **Certificate** cannot be re-registered in another organization or project.

### View certificate
- In **Manage > Certificate** tab, you can check the **Certificate** information.
- Click the **More** button to see more information on the certificate.

### Renew certificate
- In the **Manage > Certificates** tab, you can renew a certificate by clicking the **Edit** button for each certificate.
    - Only a certificate with the same common name (CN) can be registered.
    - Only a certificate whose expiration date is later than the expiration date of previously registered certificate can be registered.