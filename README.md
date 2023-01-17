Install python cryptography package
`pip3 install cryptography`

Run ransomware server:
`python3 Ransomware_server.py`

Run client script to action the ransom ware program.
`python3 Ransomware_client.py`

The client script encrypts the "target.txt" file and doesn't decrypt it until the code "ivebeenhacked" is entered.


## Detailed overview

### Client script
- Creates a symmetric key (SK)
- Uses SK to encrypt the contents of target.txt
- Uses the public key from the ransomware server to encrypt the SK.
-  - This is done to make sure the client can't use the SK to decrypt the target.txt themselves.
-  - This creates the EncryptedSymmetricKey (ESK).
- Once the correct code is entered, the ESK key is sent to the server script.
- The server returns the SK - the client script can finally decrypt the target file.
- Finally the script will delete the ESK.
- [TODO] Client to download servers public key.

### Server script
- Listens to the client - waiting to receive the ESK.
- Once the ESK is recieved, the server uses its private key to decrypt the ESK and return the SK.
