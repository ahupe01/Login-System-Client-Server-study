# Login-System-Client-Server-study
As an extension from the previous client/server study, 
my professor had me build upon my original client and server to include 
a user database of sorts. 

I created a password file that is similar to that 
of a linux password file. Every time a new user is added to the file, a set of six 
cryptographically strong random bytes (48 bits that are referred to as the salt) 
is generated. The random bytes (the salt) will likely contain unprintable characters 
(control characters, etc). In order to display these characters when someone views 
the password file I used base64 character encoding – which converts the raw bytes 
to printable characters. 

The base64 encoded salt was be added to the password file 
and each user has a unique base64 encoded salt.  Rather than storing the user’s password
in the password file I stored a cryptographically hashed version of the password. 
A cryptographic hash function converts a variable length byte string to a fixed length
byte string (I used SHA 256). The output of hash can be fed directly into a base64 encoding
function (as I did for the salt). This  base64 encoded version is also be stored in the
password file.

The final format of the password file is:
Username: Base 64 encoded salt: Base 64 encoding of the user’s password concatenated with the salt.
