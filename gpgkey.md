## 1. About GPG key
### 1.1. generate key
`gpg --gen-key`
### 1.2. list secret key
`gpg --list-secret-keys --keyid-format=long`
### 1.3. edit key
`gpg --edit-key <keyID>`\
`gpg> help` //it will list all the command that can be used

### 1.4. delete key
`gpg --delete-key <keyID>`\
`gpg --delete-secret-key <keyID>`

### 1.5. export / import public key
#### export public key
`gpg --armor --output public-key.asc --export <keyID>`

>-a, ----armor //export ASCII format\
>-o, ----output //designate the name of the file that will be exported\
>----export export public, need to designate uid, or id os public key

#### export secret key
`gpg --armor --output private-key.asc --export-secret-keys <keyID>` 
#### import 
`gpg --import <key_filename>`
