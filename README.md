# CNS-ALA-3
NAME:DIYA VORA 
ENROLLMENT:240905091019
SUBJECT: Cryptography and Network Security-BETIT16326 (ALA-3)

HMAC (Hash-Based Message Authentication Code)

Your program demonstrates HMAC, a technique used to ensure:

✅ Message integrity (data is not altered)
✅ Authentication (message comes from a trusted sender)

HMAC combines:

A secret key
A hash function (like SHA-256)
 What is HMAC?

HMAC (Hash-Based Message Authentication Code) is a mechanism where:

A message is hashed together with a secret key
The result is called a MAC (Message Authentication Code)

 Only parties who know the shared secret key can generate or verify the MAC.

 Working of Your Program
1.  Shared Secret Key
secret_key = b"my_secret_key"
Same key is used by both sender and receiver
Must be kept confidential
2.  Sender Side
 Message Input
message = input("Enter message to send: ").encode()
 MAC Generation
mac = hmac.new(secret_key, message, hashlib.sha256).hexdigest()
Uses HMAC + SHA-256
Produces a secure MAC value

 This MAC is sent along with the message

3.  Receiver Side
  Recreate MAC
new_mac = hmac.new(secret_key, received_message, hashlib.sha256).hexdigest()
Receiver uses the same secret key
Generates MAC again from received message
4.  Verification
if hmac.compare_digest(received_mac, new_mac):
Compares original MAC with newly generated MAC
Uses secure comparison to avoid timing attacks

 If both match:

✅ Message is authentic
✅ Message is not modified

 If not:

Message has been tampered
 Properties of HMAC
 Secure (resistant to attacks if key is safe)
 Key-based authentication
 Efficient and fast
 Protects against message tampering
 Applications of HMAC
 API authentication (like tokens)
 Secure communication (HTTPS, SSL/TLS)
 Data integrity in networks
 Payment gateways
 Important Notes
Security depends on:
Strength of hash function (e.g., SHA-256 )
Secrecy of the key
Unlike digital signatures:
HMAC uses shared key (symmetric)
No public/private key pair
 HMAC vs Digital Signature
Feature	HMAC	Digital Signature
Keys	Shared secret key	Public + Private key
Speed	Fast	Slower
Use case	Authentication	Authentication + Non-repudiation
 Conclusion
Your program demonstrates HMAC authentication
It ensures:
 Message integrity
 Sender authenticity
Widely used in real-world secure systems
import hmac
import hashlib

Shared secret key (must be same for sender & receiver)
secret_key = b"my_secret_key"

print(" SENDER SIDE")

message = input("Enter message to send: ").encode()

# Generate MAC using HMAC + SHA-256
mac = hmac.new(secret_key, message, hashlib.sha256).hexdigest()

print("Generated MAC:", mac)

print("\n RECEIVER SIDE")

received_message = message   # Simulating same message received
received_mac = mac           # MAC sent along with message

# Receiver generates MAC again
new_mac = hmac.new(secret_key, received_message, hashlib.sha256).hexdigest()

# Verify MAC
if hmac.compare_digest(received_mac, new_mac):
    print(" Message is authentic and not modified")
else:
    print(" Message has been tampered")
<img width="816" height="358" alt="Screenshot 2026-04-09 002839" src="https://github.com/user-attachments/assets/49a8bc89-425d-42c1-a030-903a8e08ceda" />


