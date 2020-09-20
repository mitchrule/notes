# Authentication

## Passwords

### Password Policies

- The person who designed the password complexity requirements had zero background in security.
- Short, cryptic passwords are easily cracked
- Longer, easier to remember passphrases are a much better option
- Password expiration is bad, results in users appending numbers to passwords
  - Becomes difficult for users to remember constantly changing passwords

### Password Capture

- An attacker observes passwords by looking at a sticky note or shoulder surfing
- MITM attack intercepts passwords by sniffing traffic
  - Plain text passwords
  - Crackable ciphers
  - Redirect HTTPS to traffic to HTTP
- Client side malware

## Account Recovery

- Question based recovery should never be used

## Two Factor Authentication

### One Time Passwords

- Valid for one use only
- Often used alongside a static password
  - Password, PIN, etc
- Methods
  - By mobile phone
    - OTP is sent via SMS
  - By HOTP or TOTP such as Google Authenticator
    - Open standard
    - Server generates a password and displays a QR code
    - User scans the password
    - User generates the password

### HOTP and TOTP

- HOTP (HMAC Based OTP)

  - A sequence of OTPs are generated from
    - A random secret
    - A one way hash function
    - A counter
    - The previous password

- TOTP (Time Based OTP)

  - Differs from HOTP in that the counter is generated from Unix time, and an intercal of time, often 30 seconds
  - Both server and the OTP device need to have their times synchronised with NTP

- OTP Hardware
  - Hardware token such as Yubico
  - Users lose them, forget them
  - Cost
