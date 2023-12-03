|Hashmode|Hash Name|Example Hash|
|---|---|---|
|0|MD5|8743b52063cd84097a65d1633f5c74f5|
|100|SHA1|b89eaac7e61417341b710b727768294d0e6a277b|
|1000|NTLM|b4b9b02e6f09a9bd760f388b67351e2b|
|1800|sha512crypt $6$, SHA512 (Unix)|$6$52450745$k5ka2p8bFuSmoVT1tzOyyuaREkkKBcCNqoDKzYiJL9RaE8yMnPgh2XzzF0NDrUhgrcLwg78xs1w5pJiypEdFX/|
|3200|bcrypt $2*$, Blowfish (Unix)|$2a$05$LhayLxezLhK1LhWvKxCyLOj0j1u.Kj0jZ0pEmm134uzrQlFvQJLF6|
|5500|NetNTLMv1 / NetNTLMv1+ESS|u4-netntlm::kNS:338d08f8e26de93300000000000000000000000000000000:9526fb8c23a90751cdd619b6cea564742e1e4bf33006ba41:cb8086049ec4736c|
|5600|NetNTLMv2|admin::N46iSNekpT:08ca45b7d7ea58ee:88dcbe4446168966a153a0064958dac6:5c7830315c7830310000000000000b45c67103d07d7b95acd12ffa11230e0000000052920b85f78d013c31cdb3b92f5d765c783030|
|13100|Kerberos 5 TGS-REP etype 23|$krb5tgs$23$_user$realm$test/spn_$63386d22d359fe42230300d56852c9eb$ < SNIP >|

---

## Example 1 - Cracking Password Protected Microsoft Office Documents

`Hashcat` can be used to attempt to crack password hashes extracted from some Microsoft Office documents using the [office2john.py](https://raw.githubusercontent.com/magnumripper/JohnTheRipper/bleeding-jumbo/run/office2john.py) tool.

`Hashcat` supports the following hash modes for Microsoft Office documents:

|**Mode**|**Target**|
|---|---|
|`9400`|MS Office 2007|
|`9500`|MS Office 2010|
|`9600`|MS Office 2013|

## Example 2 - Cracking Password Protected Zip Files

During an assessment, we may find an interesting zip file, but it is password protected! We can extract these hashes using the compiled version of the [zip2john](https://github.com/magnumripper/JohnTheRipper/blob/bleeding-jumbo/src/zip2john.c) tool. `Hashcat` supports a variety of compressed file formats such as:

|**Mode**|**Target**|
|---|---|
|`11600`|7-Zip|
|`13600`|WinZip|
|`17200`|PKZIP (Compressed)|
|`17210`|PKZIP (Uncompressed)|
|`17220`|PKZIP (Compressed Multi-File)|
|`17225`|PKZIP (Mixed Multi-File)|
|`17230`|PKZIP (Compressed Multi-File Checksum-Only)|
|`23001`|SecureZIP AES-128|
|`23002`|SecureZIP AES-192|
|`23003`|SecureZIP AES-256|