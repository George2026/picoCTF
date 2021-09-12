# Transformation
AUTHOR: MADSTACK
## Description
I wonder what this really is... [enc](enc)<br>
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
### Points
20
### Hints
1. You may find some decoders online
## Solution
From the code snippet we got: <br>
```python
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
```
we can understand how the flag was encoded and write the same algorithm in a simpler way: <br>
```python
flag = "ABCDEFGH"
encoded_flag = ""

for i in range(0, len(flag), 2):  # flag length needs to be a multiple of 2
	first_char = ord(flag[i])
	second_char = ord(flag[i+1])
	encoded_char = chr((first_char << 8) + (second_char))
	encoded_flag += encoded_char

print("Encoded Flag: {0}".format(encoded_flag))
```
Now we can write a very similar script that will decode the flag:
```python
encoded_flag = open('enc', 'r').read()
print("Encoded Flag: {0}".format(encoded_flag))

decoded_flag = ""

for i in range(0, len(encoded_flag)):  # encoded flag length needs to be a multiple of 2
	encoded_char = ord(encoded_flag[i])
	first_char = chr(encoded_char >> 8)  # we want the get the 8 high bits of the number -> binary SHIFT right by 8
	second_char = chr(encoded_char & 0b11111111)  # we want the 8 low bits of the number -> binary AND with 0b11111111
	decoded_flag += first_char
	decoded_flag += second_char

print("Decoded Flag: {0}".format(decoded_flag))
```
## FLAG
picoCTF{16_bits_inst34d_of_8_04c0760d}
