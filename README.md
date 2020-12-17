# WHAC
WHAC is a command-line steganography tool written in Python. You can use it to hide and encrypt images or text in the least significant bits of pixels in an image.

# Encryption
The encryption uses HMAC-SHA256 to authenticate the hidden data. Therefore the supplied MAC password is hashed with SHA-256 digest to generate the HMAC-SHA256 key. 
The MAC and the message data is further encrypted using the XTEA algorithm in CFB mode running 32 iterations, before being embedded in the image data. The SHA-256 hash for the XTEA key is created using the 128 high-order bits of the supplied password. A random 8 byte seed is used in the CFB 64 bit block cipher.

# Decryption
The random seed is appended to the hidden secret and is used with the user supplied password to decrypt the hidden message using XTEA block cipher according to the encryption process. Further the decrypted secret is authenticated by comparing the embeded hmac hash with the HMAC-SHA256 of the extracted hidden message and the user supplied mac password.

