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
[How does HTTPS (SSL) encryption works?](https://sid-500.com/2017/11/01/how-does-https-ssl-encryption-works/)

[How Does HTTPS Work? RSA Encryption Explained](https://tiptopsecurity.com/how-does-https-work-rsa-encryption-explained/)

![HTTPS](https://patrick6649.files.wordpress.com/2017/10/unbenannt68.png)

1. The Client tries to establish a connection to the server. (Hello!) The server responds, that he accepts only secure communication.
2. The Server sends his Public Key to the Client.
3. The Client generates a random value (243, the session Key) and encrypts this number by using the Server’s public key.
4. The Server is the only one that can decrypt the data with his Private Key. After decryption, he can read the session key (243).
5. The transfer of data begins.
6. To avoid that the attacker can guess the session key (243) it is regenerated from time to time.

# 3-1. HTTPS(mTLS)

[Isolated multiple trust domain mTLS in Envoy and Istio](https://speakerdeck.com/mathetake/isolated-multiple-trust-domain-mtls-in-envoy-and-istio)



# 4. SSH
[SSHサーバへの接続](https://rat.cis.k.hosei.ac.jp/article/rat/linuxliteracy/2005/ssh.html)

![RSA](https://www.thesslstore.com/blog/wp-content/uploads/2021/04/how-ssh-authentication-works.png)

1. RSA authentication starts. First of all, User requests a connection from the server.
2. The server generates random number data and encrypts the generated random number data using the registered public key and sends it.
3. The User decrypts the received encrypted data using his private key and sends the decrypted data to the server.
4. The User is identified trusted user who has the private Key paired the public key of server, If the data sent from the user matches the data generated by the server.
5. If the RSA authentication is successful, the server will generate a session key.
6. The generated session key is encrypted with the public key and sent to the user.
7. The User decrypts the encrypted session key using the private key and obtains the session key.
8. After that, encrypted communication will be performed using the session key.
