# S7-PLC_SHA256
## SHA256 encryption FC for Siemens PLC S7-1200 and S7-1500

SHA, which stands for secure hash algorithm, is a cryptographic hashing algorithm used to determine 
the integrity of a particular piece of data. SHA256 has become a successor to that of SHA1 because it is 
currently much more resistant to collision attacks, as it is able to generate a longer hash which is harder to break.

The hashing is a one-way method making it almost impossible to decrypt. 
This in turn means that SHA256 is ideal for challenge hash authentication, finger-printing, password validation, 
digital signatures, uniquely identifying files, and as checksums to detect accidental data corruption.

depending on the input "inputmode" different inputformats are used

	-1 Message is used as Bytes
	-2 Message is used as String

depending on the input "outputmode" different outputformats are available

	-1 The digest ouput is the final hash value as bytes of H0 - H7 (Array [0..31] of Byte)
	-2 The hexdigest output is the final hash value as a hexadecimal string of H0 - H7 (64 bytes string)
	-3 Both 1 and 2

steps:

	-Step 00: Initialize variables H0 - H7
	-Step 01: Set constants
	-Step 02: Convert and save message in data as Bytes
	-Step 03: Calculate number of chunks and append padding Bits 
	-Step 04: Append 64 Bit containg the original message length in Bits
	-FOR every chunk do Step 05 - Step 09:
	    -Step 05: Break the chunk into 16 DWords
	    -Step 06: Extend chunk to 64 DWords
	    -Step 07: Initialize variables A - H
	    -Step 08: Do some bitwise operations on the 64 chunk DWords
	    -Step 09: Save the chunk's hash to result for the next chunk 
	-Step 10: Produce "digest"
	-Step 11: Produce "hexdigest"
	  
![SHA256](https://github.com/user-attachments/assets/7288e595-75ff-4b1c-8a42-ca36560bc74f)
