---
title: "Generating OpenSSL Private certs"
date: 2024-05-31T07:23:52.438Z

categories: ['Tutorials']
tags: ['SSL', 'Private Certs']
author: "Benjamin Appiah-Brobbey"
---

Follow this set of commands to generate trustable OpenSSL Certificates.

<!--more-->

First, Generate an RSA Private key by:

```plaintext
openssl genrsa -out {name|dns_name}.key 2048
```

Generate a CSR(Certificate signing Request):

```plaintext
openssl req -new -key {rsa_private_key}.key -config {config_file_name}.conf -out {name|dns_name}.csr
```

Generate certificate:

```plaintext
openssl x509 -req -in {csr_name}.csr -signkey {rsa_private_key}.key -out {cert_name}.crt -days {validity_days} -sha256 -extfile {file_name}.ext
```

**Extras**
Public key generation:
```plaintext
openssl rsa -in {rsa_private_key}.key -out {name}.key
```

**Config file templates:**
[openssl req config file](https://gist.github.com/fanky5g/398c5cac84629eebfd7811598c36b9ac)

[v3.ext](https://gist.github.com/fanky5g/89a0ce74c8b8639ec06ce64a4b7c4101)