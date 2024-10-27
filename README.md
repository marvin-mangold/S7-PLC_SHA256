# S7-PLC_SHA256
## SHA256 encryption FC for Siemens PLC S7-1200 and S7-1500

Sha256 is an cryptographic algorithm that takes a string of any length and reduces it to a unique fixed length string. 
In this implmementation the string length is limited to a maximum length of 254 characters (String[254] - 2032 bit).
The hash output is the final hash value as a hexadecimal string of H0 - H7 (64 bytes string).
	
    - Step 00: Initialize variables H0 - H7
    - Step 01: Set constants
    - Step 02: Convert and save message in data as Bytes
    - Step 03: Calculate number of chunks and append padding Bits 
    - Step 04: Append 64 Bit containg the original message length in Bits
    - FOR every chunk do Step 05 - Step 09:
        - Step 05: Break the chunk into 16 DWords
        - Step 06: Extend chunk to 64 DWords
        - Step 07: Initialize variables A - H
        - Step 08: Do some bitwise operations on the 64 chunk DWords
        - Step 09: Save the chunk's hash to result for the next chunk 
    - Step 10: Produce "digest"
    - Step 11: Produce "hexdigest"

  
![SHA256](https://github.com/marvin-mangold/S7-PLC_SHA256/assets/10088323/c362c0b6-dbf4-4990-ad74-942484a2f46d)
