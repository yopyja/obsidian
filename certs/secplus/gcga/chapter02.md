# Understanding Identity and Access Management

 ## Exploring Auth Management

 `Authentication` proves an identity with some type of credentials, such as a username and password. 
 `Identification` occurs when users claim their identity with identifiers such as usernames or emails.

 ---

 ### **Comparing Identification and AAA**

 `AAA` work together with identification to provide a comprehensive access management system. 

  - `Authentication` - (already defined up above 😀)
  - `Authorization` - granted access to resources based on their proven identity.
  - `Accounting` - methods that track user activity and record activity in logs. Admins may use these to create `audit trials`.

 ---

 ### **Comparing Authentication Factors**

  Authentication is often simplified as types, or factors, of authentication.

  ---

  #### **Something you know**
   Such as a password or personal identification number (PIN).

  Consider some of the following National Institute of Standards and Technology (NIST), Microsoft, and the U.S. Dep of Homeland Security:
   - Hash all passwords
   - Require multifactor auth
   - Don't require mandatory password resets
   - Require passwords to be at least eight characters
   - Check for common passwords and prevent their use
   -  Tell users not to use same work password anywhere else.
   -  Allow all special characters, including spaces, but don't require them.

  **Password Complexities**
   - Uppercase character (26 letters A-Z)
   - Lowercase characters (26 letters A-Z)
   - Numbers (10 numbers 0-9)
   - Special characters (such as !, $, and *)

  **Password Expiration** - A password setting identifies when users must change their password. As an example, a password exp of 60 means every 2 months the user must change their password.

  **Password History and Reuse** - Many users would prefer to use the same password forever simply because it's easier to remember. `Password history` system remembers past hashes and prevents users from setting new passwords to old ones.

  **Password Vaults** - (or password manager) is a single source designed to keep most of your passwords. 

  **Password Keys** - are often used to reset passwords on systems. They are commonly a bootable disc or usb drive.

  **Knowledge Based Authentication (KBA)** - Some organizations use KBA to prove the identity of individuals. There are two Types of KBA:
   - `Static KBA` - is typically used to verify identities when you've forgotten your password. Example: Mothers maiden name
   - `Dynamic KBA` - identifies individuals without an account. The site queries public and private data sources, such as credit reports or third-party organizations. Then it crafts multiple choice questions only the user would know.

  **Implementing Account Lockout Policies** - Accounts will typically have `lockout policies` preventing users from guessing the password. Two key phrases associated with account lockout policies on Microsoft systems are: 
   - `Account lockout threshold` - This is the max # of times a user can enter the wrong password.
   - `Account lockout duration` - This indicates how long an account remains locked.

  **Changing Default Passwords** - Many systems and devices start with default passwords. Basic security practice is to change these before putting a system in use.

  *Remember this*:
  ```
  Account lockout policies thwart some default password attacks, such as brute force and dictionary attackers. Many applications and devices have default passwords. These should be changed before putting the application or device into service.
  ```

  **Training Users About Password Behaviors** - Common user habits related to password behaviors have historically ignored security. Many users don't understand the the value of their password or potential damage if they give it out. Orgs need to provide adequate training to users on password security.

 ---

  #### **Something you have**
  Refers to something you can physically hold. Examples Smart cards, Common Access Cards, and hardware tokens.

  **Smart Card Authentication** - Smart Cards are credit-sized cards that have embedded microchip and a certificate. Smart cards provide confidentiality, integrity, authentication, and non-repudiation. Requirements for a smart card are: 
   - `Embedded certificate` - holds the a users private key (which is only accessible to the user) and is matched with a public key (available to all other users).
   - `Public Key Infrastructure (PKI)` - supports issuing and managing certificates.

  **Token Key** - (sometimes called a key fob or just token) is an electronic device about the size of a car key that has a small LCD display that displays a number that changes over time.
  
  **HOTP & TOTP** - `Hashed-based Message Authentication Code (HMAC)` uses a hash function and cryptographic key for many different cryptographic functions. `HMAC-based One-Time Password (HOTP)` is an open standard used for creating one-time passwords, similar to those used in tokens or key fobs. Expires after one use. `Time-based One-Time Passwords (TOPT)` is similar to HOTP, but uses a timestamp instead of a counter. OTP created with TOTP typically expire after 30 seconds. One significant benefit of HOTP and TOTP is the price. Hardware tokens are significantly less expensive than tokens that use proprietary algorithms.

  **Two-Step Verification** - (also called two-factor authentication) adds an extra layer of security to accounts. Users typically enter username & password then they receive a message on their mobile device. This is vulnerable as text push notifications typically appear on your device and people can should surf.

  ---

  #### **Something you are**
  Uses biometrics for authentication. Biometrics are often the strongest form of authentication bc they are the most difficult for an attacker to falsify. In comparison, passwords are the weakest form of authentication.

  *Biometric Methods*:
  - `Fingerprint`
  - `Vein`
  - `Retina`
  - `Iris`
  - `Facial`
  - `Voice`
  - `Gait` - 🚶

 ---

  #### **Two-Factor & Multifactor**
  - `Single Factor Auth` - Single
  - `Two Factor Auth` - Two
  - `Multi Factor Auth` - Two or more 🙃

  ---

  #### **Authentication Attributes**
  - `Somewhere you are` - geolocation 🌎
  - `Something you can do` - gestures on a touch screen (patterns n such)
  - `Something you exhibit` - CACs/badges (w/ pic and name) worn around the building
  - `Someone you know` - someone is vouching for you.

  ---

  ### Authentication Log files
  Can track both successful and unsuccessful login attempts. It's most important to monitor login activity for any privileged accounts, such as administrators.

  ---

  ## Managing Accounts
  Concern with the creation, management, disablement, and termination of accounts.

  ---

  ### Credential Policies and Account Types
  Define login login policies for different personnel, devices, and accounts. The following list identifies different account types and credential policies associated with each:
   - `Personnel` or `end-user accounts` - 
   - `Admin` and `root accounts` - 
   - `Service accounts` - 
   - `Device accounts` - 
   - `Third-part accounts` - 
   - `Guest accounts` - 
   - `Shared` and `Generic account/credentials` -  

  ---

  ### Priv Access Management (PAM)
  Allows an organization to apply more stringent security controls over accounts with elevated privileges, such as admin or root-level accounts. Some capabilities of PAM are: 
  - Allow users to access the privileged account without knowing the password
  - Automatically change privileged account passwords periodically
  - Limit the time users can use the privileged account
  - Allow users to check out credentials
  - Log all access credentials

  ---

  ### Require Admins to use Two Accounts
  It's common for admins to have two accounts, one with regular day-to-day permissions same as every other regular user. The other having elevated permissions. This helps prevent escalation attacks.

  ---

  ### Prohibiting Shared and Generic Accounts
  Personnel should not use shared or generic accounts. As this directly hinders `Identification`, `Authentication`, `Authorization`, and `Accounting`.

  ---

  ### Disablement Policies 
  Specifies how to manage accounts in different situations. Disabling is preferred over deleting the account at least initially. Some contents of an account disablement policy include:
   - Terminated employee
   - Leave of absence
   - Delete account 

  ---

  ### Time-based Logins
  (sometimes referred to as time-of-day restrictions) ensure that users can only log on to systems during specific hours of the day.

  ---

  ### Account Audits
  Looks at the rights and permissions assigned to users and helps enforce the least privilege principle.

  ---

  ## Comparing Authentication Services
  ### Single Sign-On (SSO)
  Refers to a users ability to log on once and access multiple systems without logging on again.  

  ### Kerberos
  A network authentication mechanism used within Windows Active Directory domains and some Unix environments. Kerberos includes several requirements to work properly. They are: 
   - A method of issuing tickets used for authentication
   - Time synchronization
   - A database of subjects or users

  ### SSO and a Federation
  SSO but for joint sites and systems like USAF's GCDS authentication.

  ### Security Assertion Markup Language (SAML)
  XML-based data format used for SSO on web browsers. 

  ### SAML and Authorization
  Many federation SSO systems, including SAML, include the ability to transfer authorization data between their systems. In other words it's possible to use SAML for single sign-on authentication and for authorization.

  ### OAuth
  `Open standard for authorization` many companies use to provide secure access to protected resources. Instead of creating a different account for each website you can create/sign-in with a single account (google, facebook, twitter)

  ### OpenID and OpenID Connection
  `OpenID` is an authentication standard maintained by the OpenID Foundation. Not really used much anymore. `OpenID Connection (OIDC` builds on OpenID  for authorization and uses OAuth 2.0 framework for authentication. 

  ---

  ## Comparing Access Control Schemes
  `Access control` ensures that only authenticated and authorized entities can access resources. The `access control schemes` (sometimes referred to as access control models) covered in this section are: 
   - Role-based access control
   - Rule-based access control
   - Discretionary access control (DAC)
   - Mandatory access control (MAC)
   - Attribute-based access control (ABAC)

  Often when using these schemes you'll run into the following terms:
  - `Subjects` - are typically users or groups that access an object. Occasionally, the subject may be a service that is using a service account to access an object.
  - `Objects` - are items such as files, folders, shares, and printers that subjects access.

  ---

  ### Role-based Access Control
  Uses roles to manage rights and permissions for users.

   - Using Roles Based on Jobs and Functions
   - Documenting Roles with a Matrix
   - Establishing Access with Group-Based Priv

  ---

  ### Rules-Based Access Control
  Uses rules, the most common being using rules with routers or firewalls.

  ---

  ### Discretionary Access CTRL

  **Filesystem Permissions**
   - Write
   - Read
   - Read & Execute
   - Modify
   - Full Control


  **SIDs & DACLs** - Microsoft systems identify users with security identifiers (SIDs). Every object includes a discretionary access control list (DACL) that identifies who can access it in a system using the DAC scheme.

  **The Owner Establishes Access** - If a user creates a file they are the designated owner of sed file. Able to grant/revoke access to other users/groups.

  **Mandatory Access Control** - Uses labels like the military grant access levels (need to know, secret, top secret)

  **Labels and Lattice** - Uses different levels to classify both the users and the data.

  **Establishing Access** - An admin is responsible for establishing access, but only someone at a higher authority can define the access for subjects and objects.

  ---

  ## Conditional Access
  Microsoft has implemented Conditional Access within Azure Active Directory env'. It can be used with traditional access control schemes but adds additional capabilities to enforce organizational policies. Conditional Access uses policies, which are if-then statements. Some common conditional signals are: 
   - User or group membership
   - IP location
   - Device


