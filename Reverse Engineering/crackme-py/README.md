# crackme-py
AUTHOR: SYREAL
## Description
[crackme.py](crackme.py)
### Points
30
### Hints
None
## Solution
The code we got for this challenge starts with the following information:
```python
# Hiding this really important number in an obscure piece of code is brilliant!
# AND it's encrypted!
# We want our biggest client to know his information is safe with us.
bezos_cc_secret = "A:4@r%uL`M-^M0c0AbcM-MFE055a4ce`eN"
```
seems like a secret we need to understand what it is <br>
we have the next decode_secret function:
```python
def decode_secret(secret):
    """ROT47 decode

    NOTE: encode and decode are the same operation in the ROT cipher family.
    """

    # Encryption key
    rotate_const = 47

    # Storage for decoded secret
    decoded = ""

    # decode loop
    for c in secret:
        index = alphabet.find(c)
        original_index = (index + rotate_const) % len(alphabet)
        decoded = decoded + alphabet[original_index]

    print(decoded)
```
the secret is probably only encoded with ROT47, <br>
(you can read about ROT cipher family on GOOGLE) <br>
executing the decode_secret function with the encoded secret results with the decoded secret.
## FLAG
picoCTF{1|\/|_4_p34|\|ut_dd2c4616}
