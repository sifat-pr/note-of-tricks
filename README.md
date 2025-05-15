# 🎯 Tricks Exploration Log
A personal knowledge base documenting all the tips, tricks, and techniques I’m currently exploring. This note serves as a quick-access resource for experiments, discoveries, and strategies across various topics—whether it's ethical hacking, development, or productivity hacks.

## Cryptography
Cryptography is the practice of securing information and communications using codes, ensuring only authorized parties can access or read it. 
**It can be devided by**
1. Symmetric Key Cryptography (Secret Key Cryptography)
2. Asymmetric Key Cryptography (Public Key Cryptography)
3. Hash Functions

### For Cipher Identify
- [BoxenTriq.com](https://www.boxentriq.com/code-breaking/cipher-identifier)
- [Dcode.fr](https://www.dcode.fr/cipher-identifier)

### Encrypt or Decrypt Cipher
- [BoxenTriq.com](https://www.boxentriq.com/code-breaking/caesar-cipher)
- [Dcode.fr](https://www.dcode.fr/cipher-identifier)
- [Cryptii.com](https://cryptii.com/pipes/caesar-cipher)
**For Encoding and Decoding you can also use** [CyberSHef.io](https://cyberchef.io/)

### Use Online Tools to Identify Hashes
1. [Hashes.com](https://hashes.com/en/tools/hash_identifier)
2. [TunnelsUp.com](https://www.tunnelsup.com/hash-analyzer/)

### Hash Decoder Online Tools
1. [Hashes.com](https://hashes.com/en/decrypt/hash)
2. [Base64Decode](https://www.base64decode.org/) For Base64 Encoding and Decoding

## Reverse Engineering on Apk
First of all if we wanna see source code of any application we need to decomplie it we can use apktool to decompile and building apks.
For decomplie an app use this command `apktool d name.apk`
For Building an app use this cmmand `apktool b foldername`

After modifying source code and building the app we have to sign and compress the app. 
*For signing the app we need to generate a hash key that stores additional info.*
**Generating a key using keytool - (Example command)**
```bash
keytool -genkey -v -keystore CTF.keystore -alias CTF.keystore -keyalg RSA -keysize 2048 -validity 10000
```
**Signing the key to our builded app - (Example command)**
```bash
jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 <apk file path> CTF_keystore
# Or you can use apksigner
apksigner sign --ks CTF.keystore --ks-key-alias CTF.keystore --out app-release-signed.apk <app path>

# Verify the key is signed or not
jarsigner -verify -verbose -certs <apk file path>
# Or
apksigner verify <app path>
```
**Use Zipalign to compress the app - (Example command)**
```bash
zipalign -v 4 <unsigned apk file path> <aligned apk file path>
```

## 🫠 Additional Tricks
**Create symbolic link to run file instead of another**
```bash
sudo ln -s <path of actual file that will run> <path of the linked file>
```
**Upgrade reverse shell to TTY**
```bash
python3 -c 'import pty;pty.spawn("/bin/bash")'
```
**Find SUID files in linux.**
```bash
find / -type f -perm -u=s 2>/dev/null

sudo -l # It lists the commands the current user is allowed to run with sudo.
```
**Find how many services are running on a linux system.**
```bash
systemctl list-units --type=service --state=running
```
## Website Highlights
- [GTFObbins](https://gtfobins.github.io) - Unix binaries for privilege escalation.
- [Playit.gg](https://playit.gg) - Free port forwarding for gamers.
- [HackTricks](https://book.hacktricks.wiki/) - Hacking techniques and privilege escalation.
- [LostSec](https://lostsec.xyz/) - Bug bounty tools and recon.
