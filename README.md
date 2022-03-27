# digitalSignature


# 1. Differece between Private Key and Public Key
Public key is made available to everyone via a publicly accessible repository or directory. On the other hand, the Private Key must remain confidential to its respective owner.<br>
For example, if Bob wants to send sensitive data to Alice, and wants to be sure that only Alice may be able to read it, he will encrypt the data with Alice's Public Key. Only Alice has access to her corresponding Private Key and as a result, is the only person with the capability of decrypting the encrypted data back into its original form.<br>
As only Alice has access to her Private Key, it is possible that only Alice can decrypt the encrypted data. Even if someone else gains access to the encrypted data, it will remain confidential as they should not have access to Alice's Private Key.

# 2. Differece between Encryption and Digital Signature
[電子署名=『秘密鍵で暗号化』」という良くある誤解の話](https://qiita.com/angel_p_57/items/d7ffb9ec13b4dde3357d)

# Encryption
- Sender:   PubKey_Enc(message)      = Encryed-Data<br>
- Receiver: PriKey_Dec(Encryed-Data) = message

PublicKey is for Encryption while PrivateKey is for Decryption.
But, what do you think if it is available that data is decrypted by PrivateKey before it was encrypted by PublicKey? <br>
Yes, it is acutally used as Digital Signature.

# Digital Signature
- Sender:   PriKey_Dec(message's digest) = Decored-data<br>
- Receiver: PubKey_Enc(Decored-data)     = message's digest

In other words, decrypting the "message" into "Decored-data" with a private key and encrypting it with a public key and returning it into "message", if it is possible, "Decored-data" is a data that only the owner of the private key can create. <br>

![DegitalSignature](http://www.herongyang.com/PKI/Digital-Signature-Scheme.jpg)

# 3. HTTPS

# 4. SSH
[SSHサーバへの接続](https://rat.cis.k.hosei.ac.jp/article/rat/linuxliteracy/2005/ssh.html)
