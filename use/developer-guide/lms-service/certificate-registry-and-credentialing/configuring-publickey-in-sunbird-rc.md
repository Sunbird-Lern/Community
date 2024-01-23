---
description: >-
  Following steps helps to configure publickey in RC which will be used for
  certificate generation process.
---

# Configuring PublicKey in Sunbird-RC

### Step 1

Generate public key

```bash
# Note: Execute the commands one by one.
openssl genrsa -out key.pem; cat key.pem;

openssl rsa -in key.pem -pubout -out pubkey.pem;
```

### Step 2

Open `pubkey.pem` in an text editor and copy the contents of it. And convert multilines into single line by replacing new line to `\r\n`

```
# Example for Copied from pubkey.pem
-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCqwefadcfafdCAQEA4EQdY0cnP8DmBgigxIYP
0cJi7hQVQHDKUw8m+7dY82XQypA123123123123qsddjRkl+lWLdWT2ubekyylDT
7p0cbVKSU7aEYm/Ng7z3OSZKr124oirfqwefdaffw23QjhY5ft1wZ6pYyfWgIIr2
TI6uDUvEFspmj0t5HcKuIB0762Zol43sevcjkpX1znejIJAATpkvaleGFpHNgqwj
bYwzrDpxaDm6Mjgr3FuEjFvr8a94qfqdasdcwef13efEipwn2iTZmiIa4/FVJDhK
uBkQF7bbXvEFobI+vfgjiILhLCLdasdavrqcqs3cHUTl/d+XYsPPUDLchAC+BfyT
AwI3dasB
-----END PUBLIC KEY-----


# Example for converted public key
-----BEGIN PUBLIC KEY-----\r\nMIIBIjANBgkqhkiG9w0BAQEFAAOCqwefadcfafdCAQEA4EQdY0cnP8DmBgigxIYP\r\n0cJi7hQVQHDKUw8m+7dY82XQypA123123123123qsddjRkl+lWLdWT2ubekyylDT\r\n7p0cbVKSU7aEYm/Ng7z3OSZKr124oirfqwefdaffw23QjhY5ft1wZ6pYyfWgIIr2\r\nTI6uDUvEFspmj0t5HcKuIB0762Zol43sevcjkpX1znejIJAATpkvaleGFpHNgqwj\r\nbYwzrDpxaDm6Mjgr3FuEjFvr8a94qfqdasdcwef13efEipwn2iTZmiIa4/FVJDhK\r\nuBkQF7bbXvEFobI+vfgjiILhLCLdasdavrqcqs3cHUTl/d+XYsPPUDLchAC+BfyT\r\nAwI3dasB\r\n-----END PUBLIC KEY-----
```

### Step 3

Pass the converted publickey in the payload of below curl command and make the API call.

```sh
curl --location --request POST '{{rc_host}}/registry-service/api/v1/PublicKey' \
--header 'Content-Type: application/json' \
--data-raw '{"value":"-----BEGIN PUBLIC KEY-----\r\nMIIBIjANBgkqhkiG9w0BAQEFAAOCqwefadcfafdCAQEA4EQdY0cnP8DmBgigxIYP\r\n0cJi7hQVQHDKUw8m+7dY82XQypA123123123123qsddjRkl+lWLdWT2ubekyylDT\r\n7p0cbVKSU7aEYm/Ng7z3OSZKr124oirfqwefdaffw23QjhY5ft1wZ6pYyfWgIIr2\r\nTI6uDUvEFspmj0t5HcKuIB0762Zol43sevcjkpX1znejIJAATpkvaleGFpHNgqwj\r\nbYwzrDpxaDm6Mjgr3FuEjFvr8a94qfqdasdcwef13efEipwn2iTZmiIa4/FVJDhK\r\nuBkQF7bbXvEFobI+vfgjiILhLCLdasdavrqcqs3cHUTl/d+XYsPPUDLchAC+BfyT\r\nAwI3dasB\r\n-----END PUBLIC KEY-----"}'
```

Note: Value for `rc_host` can be found from certificate generater flink job's config map. Config key is `service.rc.basePath`

### Step 4

Make the search API call to verify if the publickey is available.

```sh
curl --location --request POST '{{rc_host}}/registry-service/api/v1/PublicKey/search' \
--header 'Content-Type: application/json' \
--data-raw '{
    "filters": {
    }
}'
```
