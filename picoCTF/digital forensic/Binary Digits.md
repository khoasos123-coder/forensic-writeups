# 📝 Writeup: Binary Digits - picoCTF
* Category: Forensics | Difficulty: Easy

## 💡 1. Analyzing the challenge

* The challenge provides a file named digits.bin along with the description: "This file doesn't look like much... just a bunch of 1s and 0s" .
When using the cat command to read the file's content, we only see a very long text string consisting entirely of 0 and 1 characters.
This indicates that the data is encoded (or represented) as a binary string (ASCII Binary) .

## 🛠️ 2. Solution steps (Step-by-Step)

* Step 1: Download the file to your machine (Kali Linux) Use the wget tool to download the file from the tournament server:
Bash

`wget https://challenge-files.picoctf.net/c_plain_mesa/cfc550931c1ca482fc71f6f88d4049b6632c906ec5ba1dcf80fdc568d477fc2e/digits.bin`


* Step 2: Decode the binary string into Raw Bytes Every 8 characters of 0 and 1 (8 bits) in this text file actually represent 1 Byte of data.
To recover the original data, we need to group these 8-bit chunks together and convert them into actual bytes, then write them out to a new file.
Use a condensed Python3 script (One-liner) to do this:

Bash

`python3 -c "data = open('digits.bin').read().replace(' ', '').replace('\n', ''); open('decoded.bin', 'wb').write(bytes(int(data[i:i+8], 2) for i in range(0, len(data), 8)))"`

 Code explanation: This script will read the file, remove all spaces and newline characters (if any), then slice the string into clusters of 8 characters, cast them to base 2 integers (binary), convert them to bytes and save them to a new file named decoded.bin.

* Step 3: Determine the true format of the file In Forensics, the file extension (like .txt, .bin) does not mean much because it can be changed very easily.
To know exactly what the file decoded.bin contains, we must read its File Signature (Magic Bytes) using the file command:

<img width="906" height="168" alt="image" src="https://github.com/user-attachments/assets/3cfd61d7-a402-4784-a097-ac7af1c1a7a5" />

### Returned result:

<img width="834" height="62" alt="image" src="https://github.com/user-attachments/assets/374c1868-631f-4f70-85c8-d3977999d281" />

The result shows that the data hidden beneath the binary code layer is actually a JPEG format image.

* Step 4: Extract the Flag Now everything is clear.
  
We just need to change the file extension back to the correct image format so the operating system can read it:

<img width="943" height="502" alt="image" src="https://github.com/user-attachments/assets/6120af85-ff04-49c2-acc2-8417317c4b5d" />



