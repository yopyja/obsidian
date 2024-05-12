# Understanding Cryptography and PKI

## Introducing Cryptography Concepts
Cryptography includes several important concepts that you need to grasp for the CompTIA Sec+ exam.

 - `Integrity` provides assurances that data has not been modified. Hashing ensures that data has retained integrity.
   - A `hash` is a number derived from performing a calculation on data, such as a message, patch, or file.
   - Hashing creates a fixed-length string of bits or hexadecimal characters, which cannot be reversed to re-create the original data.
   - A common hashing algorithm in use today is the Secure Hash Algorithm 3 (SHA-3).
 - `Confidentiality` ensures that data is only viewable by authorized users. Encryption protects the confidentiality of data.
   - `Encryption` scrambles data to make it unreadable if intercepted. Encryption normally includes an algorithm and a key.
   - `Symmetric encryption` uses the same key to encrypt and decrypt data. Most symmetric algorithms use either a block cipher or a stream key.
   - `Stream ciphers` encrypt data 1 bit at a time. `Block ciphers` encrypt data in blocks.
   - `Asymmetric encryption` uses two keys (public and private) created as a matched pair.
     - Asymmetric encryption requires a Public Key Infrastructure (PKI) to issue certificates.
     - Anything encrypted with the public key can only be decrypted with the matching private key.
     - Anything encrypted with the private key can only be decrypted with the matching public key.
 - `Steganography` provides a level of confidentiality by hiding data within other files. For example, it's possible to embed data within the white space of a picture file.
 - A digital signature provides authentication, non-repudiation, and integrity.
   - `Authentication` validates an identity
   - `Non-repudiation` prevents a party from denying an action.
   - Users sign emails with a digital signature, which is a hash of an email message encrypted with the sender's private key.
   - Only the sender's public key can decrypt the hash, providing verification that it was encrypted with the sender's private key.

## Providing Integrity with Hashing
You can verify integrity with hashing.

### Hash Versus Checksum
Hashes and checksums are similar, but there are some differences. In general, hashes are much longer numbers and used in strong cryptographic implementation. A checksum is typically a small piece of data, sometimes only 1 or 2 bits, and is used to quickly verify the integrity of data.

### MD5
`Message Digest 5 (MD5)` is a common hashing algorithm that produces a 128-bit hash. Hashes are commonly shown in hexadecimal format instead of a stream of 1s and 0s.

### Secure Hash Algorithms
`Secure Hash Algorithms (SHA)` are groups of hashing algorithms with variations in grouped four families SHA-0, SHA-1, SHA-2, and SHA-3:
 - SHA-0 is not used
 - SHA-1 is an updated version that creates 160-bit hashes. It is similar to the MD5 algorithm. Weaknesses were discovered and it is no longer approved for most cryptographic uses.
 - SHA-2 improves SHA-1 to overcome potential weaknesses. It includes four Versions.
   - `SHA-256` creates 256-bit hashes
   - `SHA-512` creates 512-bit hashes
   - `SHA-224` (224-bit hashes) & `SHA-384` (384-bit hashes) create truncated versions of SHA-256 and SHA-512, respectively.
 - SHA-3 (previously known as Keccak) is an alternative to SHA-2. The U.S. National Security Agency (NSA) created SHA-1 and SHA-2. SHA-3 was created outside of the NSA and was selected in a non-NSA public competition. It can create hashes of the same size as SHA-2 (224, 256, 384, and 512 bits).

Just as MD5 is used to verify the integrity of files, SHA also verifies file integrity.

### HMAC
Another method used to provide integrity is with a `Hash-based Message Authentication Code (HMAC)`. An HMAC is a fixed-length string of bits similar to other hashing algorithms such as MD5 and SHA-256 (known as HMAC-MD5 and HMAC-SHA256, respectively). However, HMAC also uses a shared secret key to add some randomness to the result and only the sender and receiver know the secret key.

### Hashing Files
Many applications calculate and compare hashes automatically without any user intervention.

### Hashing Messages
Hashing provides integrity for messages. It provides assurances to someone receiving a message that the message has not been modified. 

### Using HMAC
With HMAC, both parties would know the same secret key and use it to create an HMAC-MD5 hash instead of just an MD5 hash.

### Hashing Passwords
Most systems don't store the actual password for an account. Instead, they store a hash of the password. When a user create a new password, the system calculates the hash for the password and then stores the hash.

### Understanding Hash Collisions
A `hash collision` occurs when the hashing algorithm when the hashing algorithm creates the same hash from different inputs.
This is not desireable.

---

## Understanding Password Attacks
Password attacks attempt to discover, or bypass, passwords used for authentication on systems and networks, and for different types of files. Some password attacks are sophisticated cryptographic attacks, while others are rather simple brute force attacks

An `online password attack` attempts to discover a password from an online system.

`Offline password attacks` attempt to discover passwords from a captured database or captured packet scan.

### Dictionary Attacks
A `dictionary attack` is one of the original password attacks. It uses a dictionary of words and attempts every word in the dictionary to see if works. A dictionary in this context is simply a list of words and character combinations.

### Brute Force Attacks
A `brute force attack` attempts to guess all possible character combinations. One of the first steps to thwart offline brute force attacks is to use complex passwords and store the passwords in an encrypted or hashed format.

### Spraying Attacks
A password `spraying attack` is a special type of brute force or dictionary attack designed to avoid being locked out. An automated program starts with a large list of targeted user accounts. It then picks a password and tries it against every account in the list. It then picks another password and loops through the list again.

### Pass the Hash Attacks
In a `pass the hash attack`, the attacker discovers the hash of the user's password and then uses it to log on the system as the user.  Any authentication protocol that passes the hash over th network is unencrypted format is susceptible to this attack.

### Birthday Attack
A `birthday attack` is named after the birthday paradox in a mathematical probability theory. The birthday paradox states that for any random group of 23 people, there is a 50 percent chance that 2 of them have the same birthday. This is not the same year, but instead one of the 366 days in a year, including february 29.

In a birthday attack, an attacker attempts to create a password that produces the same hash as the user's actual password. This is also known as a hash collision, as described earlier. Using the knowledge of the birthday paradox, the attacker doesn't need to guess every possible password before discovering a collision. If the password could only be one of 366 possibilities, the attacker has a 50 percent chance of guessing it after only 23 attempts.

### Rainbow Table Attack
`Rainbow table attacks` are a type of attack that attempts to discover the password from the hash. A rainbow table is a huge database of possible passwords with the precomputed hashes for each. It helps to look at the process of how some password cracker applications discover passwords without a rainbow table.

### Salting Passwords
`Salting` passwords is a common method of preventing rainbow table attacks, along with other password attacks such as brute force and dictionary attacks. A salt is a set of random data such as two additional characters. Password salting adds these additional characters to a password before hashing it. These additional characters add complexity to the password, and result in a different hash than the system would create using only the password. This causes password attacks that compare hashes with a rainbow table to fail.

### Key Stretching
`Key stretching` is an advanced technique used to increase the strength of stored passwords. Instead of just adding a sal to the password before hashing it, key stretching applies a cryptographic stretching algorithm to the salted password. The benefit of key stretching is that it consumes more time and computing resources frustrating attackers who are trying to guess passwords.

`Bcrypt` is based on the Blowfish block cipher and is used on many Unix and Linux distribution to protect the passwords stored in the shadow password file. Bcrypt salts the password by adding additional random bits before encrypting it with Blowfish. Bcrypt can go through this process multiple times to further protect against attempts to discover the password. The result is a 60-character string.

`PBKDF2` uses salts of at least 64bits and uses a pseudo-random function such as HMAC to protect passwords. Many algorithms such as Wi-Fi Protected Access II (WPA2), Apple's iOS mobile operating system, and Cisco operating systems use PBKDF2 to increase the security of passwords. Some applications send the password through the PBKDF2 process as many as 1,000,000 times to create the hash. The size of the resulting hash varies with PBKDF2 depending on hwo it is implemented. 

A Password Hashing Competition (PHC) in 2015 selected `Argon2` as an alternative key stretching algorithm. Like bcrypt and PBKDF2, Argon2 uses a password and salt that is passed through an algorithm several times. Argon2 has been improved with each new version using a lowercase letter such as Argon2d and Argon2i.

---

## Providing Confidentiality with Encryption
Encryption provides confidentiality and presents unauthorized disclosure of data. Plain-text is human readable data. An encryption algorithm scrambles the data, creating ciphertext, which is unreadable.

`Data at rest` refers to any data stored on media and it's common to encrypt sensitive data. For example, it's possible to encrypt individual fields in a database (such as fields holding customer credit card data), individual files, folders, or a full disk.

`Data in transit` or `data in motion` refers to any data sent over a network and it's common to encrypt sensitive data in transit. For example e-commerce websites commonly use Hypertext Transfer Protocol Secure (HTTPS) sessions to encrypt transactions that include credit card data. If attackers intercept the transmission, they only see ciphertext.

`Data in processing` (sometimes called data in use) refers to data being used by a computer. Because the computer needs to process the data, it is not encrypted while in use. If the data is encrypted, an application with decrypt and store it in memory while in use. If the application changes the data, it will encrypt it again before saving it. Additionally, applications usually take an extra steps to purge memory of sensitive data after processing it.

These encryption methods include two element:
 - `Algorithm` The algorithm performs mathematical calculations on data. The algorithm is always the same.
 - `Key` The key is a number that provides variability for the encryption. It is either kept private and/or changed frequently.

### Symmetric Encryption
`Symmetric encryption` uses the same key to encrypt and decrypt data. In other words, if you encrypt data with a key of three, you decrypt it with the same key of three. Symmetric encryption is also called secret-key encryption or session-key encryption.

`Encryption algorithm` Move X spaces forward to encrypt.
`Decryption algorithm` Move X spaces backward to decrypt.

### Block Versus Stream Ciphers
Most symmetric algorithm cipher use either a block cipher or stream cipher. They are both symmetric, so they both use the same key to encrypt or decrypt data. However, they divide data in different ways.

A `block cipher` encrypts data in specific-sized blocks, such as 64-bit blocks or 128-bit blocks. The block cipher divides large files or messages into these blocks and then encrypts each indiviidual block separately. A `stream cipher` encrypts data as a stream of bits or bytes rather than dividing it into blocks.

### Common Symmetric Algorithms

#### AES
The `Advanced Encryption Standard (AES)` is a strong symmetric block cipher that encrypts data in 128-bit blocks. The National Institute of Technology (NIST) adopted AES from the Rijndael encryption algorithm after a lengthy evaluation of several different algorithms.

AES can use 128, 192, and 256 bits. Because of its strengths, AES has been adopted in a wide assortment of applications. For example, many applications that encrypt data on USB drives use AES. Some of the strengths of AES are:
 - Fast
 - Efficient
 - Strong

#### 3DES
`3DES (pronounced as "Triple DES")` is a symmetric block cipher designed as an improvement over the known weaknesses of the legacy Data Encryption Standard (DES). In basic terms, it encrypts data using the DES algorithm in three separate passes and uses multiple keys. 3DES encrypts data in 64-bit blocks.

#### Blowfish and Twofish
`Blowfish` is a strong symmetric block cipher that is still widely used today. It encrypts data in 64-bit blocks and supports key sizes between 32 and 448 bits.

`Twofish` is related to Blowfish, but it encrypts data in 128-bit blocks, and it supports 128-, 192-, or 256-bit keys. It was also one of the finalist algorithms evaluated by NIST.

---

### Asymmetric Encryption
`Asymmetric encryption` uses two keys in a matched pair to encrypt and decrypt data (a public key and a private key). There are several important points to remember with these keys:
 - If the `public key` encrypts information, only the matching private key can decrypt the same information.
 - If the `private key` encrypts information, only the matching public key can decrypt the same information.
 - Private keys are always kept private and never shared.
 - Public keys are freely shared by embedding them in a shared certificate.

Although asymmetric encryption is strong, it is also very resource intensive. It takes a significant amount of processing power to encrypt and decrypt data, especially when compared with symmetric encryption. Most cryptographic protocols that use asymmetric encryption only use it for key exchange.

#### Key Exchange
`Key exchange` is a cryptographic method used to share cryptographic keys between two entities. In this context, asymmetric encryption uses key exchange to share a symmetric key.

#### The Rayburn Box
I often talk about the Rayburn box in the classroom to help people understand the usage of public and private keys. A Rayburn box is a lockbox that allows people to securely transfer items over long distances. It has two keys. One key can lock the box but cant unlock it. The other key can unlock the box but cant lock it. Both keys are matched to one box and wont work with other boxes.
 - Only one copy of one key exist-think of it as the private key.
 - Multiple copies of the other key exist, and copies are freely made and distributed-think of these as public keys.

The box comes in two different versions. In one version, it's used to send secrets in a confidential manner to prevent unauthorized disclosure. In the other version, it's used to send messages with authentication, so you know the sender sent the message and that the message wasn't modified in transit.

---

### Certificates
A key element of asymmetric encryption is a certificate. A certificate is a digital document that typically includes the public key and information on the owner of the certificate. Certificate Authorities (CAs) issue and manage certificates.

There is much more information in the certificate than just the public key, but not all of it is visible in the figure. Common elements within a certificate include:
 -  Serial number
 -  Issuer
 -  Validity dates
 -  Subject
 -  Public key
 -  Usage

Certification attributes identify the issuer using Distinguished Name attributes. Some common attributes are:
 - CN: CommonName (367trss.mil)
 - o: Organization (USAF)
 - L: Locality (Layton)
 - S: StateOrProvinceName (UT)
 - C: CountryName (US)

### Ephemeral Keys
`Ephemeral` refers to something that lasts a short time. In the context of cryptography, an ephemeral key has a short lifetime and is re-created for each session. In contrast, a static key is semipermanent and stats the same over a long period of time.

### Elliptic Curve Cryptography
`Elliptic curve cryptography (ECC)` doesn't take as much processing power as other cryptographic methods. It uses mathematical equations to formulate an elliptical curve. It then graphs points on the curve to create keys. A key benefit is that ECC keys can be much smaller when compared with non-ECC keys.

### Quantum Computing
`Quantum cryptography` uses quantum mechanical properties to perform cryptographic tasks.

#### Quantum Cryptography
Quantum key distribution (QKD) is one example of quantum cryptography. It allows two parties to establish a shared key, similar to how asymmetric encryption is used to allow two parties to establish a shared key used with symmetric encryption.

#### Post-Quantum Cryptography
`Post-Quantum Cryptography` (also known as quantum-proof or quantum-resistant) refers to cryptographic algorithms that are likely to be resistant to attacks using a quantum computer.

---

### Lightweight Cryptography
Lightweight cryptography refers to cryptography deployed to smaller devices such as radio-frequency identification(RFID) tags, sensor nodes, smart card, health care devices, and Internet of Things (IoT) devices.

Unlike servers and desktop computers, these smaller devices have limited processing power.

### Homomorphic Encryption
`Homomorphic Encryption` allows data remain encrypted while it is being processed. This allows people to access and manipulate the data without being able to see it because it remains encrypted.

### Key Length
Because the algorithm always stays the same, the way that any individual algorithm is strengthened is by increasing the length of of a key.

### Modes of Operation
Authenticated encryption modes ensure the confidentiality of data and the authenticity of the data.

### Steganography
`Steganography` hides data inside other data, or, as some people have said it, it hides data in plain sight.

#### Audio Steganography

#### Image Steganography

#### Video Steganography

---

## Using Cryptography Protocols

### Protecting Email

#### Signing Email with Digital Signature
It provides the following 3 security benefits:
 - Authentication
 - Non-repudiation
 - Integrity
Digital signatures are much easier to grasp if you understand some other cryptography concepts discussed in this chapter. A short review, these concepts are:
 - Hashing
 - Certificate
 - Public/private keys

#### Encrypting Email

#### S/MIME
Secure/Multipurpose Internet Mail Extensions(S/MIME) is one of the most popular standard used to digitally sign and encrypt email.

---

### HTTPS Transport Encryption

#### TLS vs. SSL

#### Encrypting HTTPS Traffic with TLS

#### Downgrade Attacks on Weak Implementations
A `downgrade attack` is a type of attack that forces a system to downgrade its security. The attacker then exploits the lesser security control. It is most often associated with cryptographic attacks due to weak implementations of cipher suites.

---

### Blockchain
`Blockchain` is commonly defined as a distributed, decentralized, public ledger. In other words, it is a public record-keeping technology. Banks commonly use ledgers to record transactions such as deposits and withdrawals.

### Crypto Diversity
`Cryptographic diversity` typically refers to using different methods to protect security keys. The idea is that if a vulnerability appears in one method, the diversified methods still protect the key.

### Identifying Limitations
When evaluating different algorithms, it is important to consider their possible limitations. When you understand these, it becomes much easier to identify the best algorithm to meet specific requirements.

#### Resource Vs. Security Constraints

#### Speed and Time
Speed refers to how long an algorithm takes to compute the result.

#### Size and Computational Overhead
Size in cryptography typically relates to the amount of memory space the algorithm needs to execute.

#### Entropy
`Entropy` refers to the randomness of a cryptographic algorithm.

#### Predictability
In general, predictability refers to knowing what will likely happen based on repeating the same event. same applies to cryptography with input and output comparisons.

#### Weak Keys
Even the strongest algorithms can be easily cracked when weak keys are used.

#### Longevity
Longevity refers to how long you can expect to use an algorithm.

#### Reuse
When using symmetric encryption, the same keys shouldn't be reused.

---

### Plaintext Attack
A plaintext attack is possible if an attacker has some known plaintext and the ciphertext created from this plaintext.

### Common Use Cases
 - Supporting integrity
 - Supporting confidentiality 
 - Supporting non-repudiation
 - Supporting high resiliency
 - Supporting obfuscation
 - Supporting low power devices
 - Supporting low latency

---

## Exploring PKI Components
A `public key infrastructure(PKI)` is a group of technologies used to request, create, manage, store, distribute, and revoke digital certificates. Asymmetric encryption depends on the use of certificates for a variety of purposes, such as protecting email and protecting internet traffic with TLS.

### Certificate Authority
A `certificate authority(CA)` issues, manages, validates, and revokes certificates. In some contexts, you might see a CA referred to as a certification authority.

### Certificate Trust Models
CAs are trusted by placing a copy of their root certificate into a trusted root CA store.

The most common trust model is the hierarchical trust model, also known as centralized trust model. In this model, the public CA creates the first CA, known as the root CA.

### Registration Authority and CSRs

### Online vs. Offline CAs
If the CA is online, meaning it is accessible over a network, it's possible to submit the CSR using an automated process.

### Updating and Revoking Certificates

### Certificate Revocation List


Online Certificate Status Protocol(OCSP) allows the client to query the CA with the serial number of the certificate.

OCSP stapling solves this problem. Less handshakes are needed.

### Public Key Pinning
Public key pinning is a security mechanism designed to prevent attackers from impersonating a website using fraudulent certificates.

### Key Escrow
`Key escrow` is the process of placing a copy of a private key in a safe environment.

### Key Management
`Key management` within a PKI refers to all the steps taken to manage public and private keys used within the PKI. This includes keeping private keys private, distributing public keys in certificates, and revoking certificates when keys are compromised.

### Comparing Certificate Types

 - Machine/Computer
 - User
 - Email
 - Code signing
 - Self-signed
 - Root
 - Wildcard
 - Subject alt name
 - Domain validation
 - Extended validation

### Comparing Certificate Formats

CER
DER
PEM/CER/CRT/KEY
P7B/P7C
P12/PFX