# 1. Getting Set Up
## 1.1. Install basic packaging software
>`$sudo apt install gnupg pbuilder ubuntu-dev-tools apt-file`
- gnupg (GNU Privacy Guard) :  include the encrypt key that must sign the file before uploading.
- pbuilder : The tool to build package in the clear enviroment.
- ubuntu-dev-tools : (dependency of devscripts) The tool to make package easier.
- apt-file : Provide a simple way to find binary package.
## 1.2. Generate GPG key
Need to generate your own GPG key, when uploading package to launchpad, launchpad will verify who upload the package, and then accept it.
>`$gpg --gen-key` //generate new GPG key

You will get similar message after successfully build the key :
```
gpg: key <keyID> marked as ultimately trusted
public and secret key created and signed.

pub   4096R/43CDE61D 2010-12-06
      Key fingerprint = 5C28 0144 FB08 91C0 2CF3  37AC 6F0B F90F 43CD E61D
uid                  Name <email@xxx.com>
sub   4096R/51FBE68C 2010-12-06
```
also will get the Key ID\
key ID :  EXX5X2XXX7FXXXXX
>`$gpg --send-keys --keyserver keyserver.ubuntu.com <key ID>`

:exclamation: **need to sync key ID with ubuntu keyserver first, then it can be uploaded to Launchpad and be verified.**

If cannot use command to sync keyID, you can directly go to [Ubuntu Keyserver](https://keyserver.ubuntu.com/) and submit public key
> [!TIP]
> `$gpg --armor --export email@xxx.com` //you can get your PGP public key

Reference：[GnuPrivacyGuardHowto
](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

## 1.3. Generate SSH key
>`$ssh-keygen -t rsa`
