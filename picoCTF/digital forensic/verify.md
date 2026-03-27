# 🚀 picoCTF - Verify Write-up
 ## Challenge Details
![Category](https://img.shields.io/badge/Category-Forensics-blue)

![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green)

![Status](https://img.shields.io/badge/Status-Solved-success)

## 📝 Description
> [cite_start]People keep trying to trick my players with imitation flags... [cite: 1]

## 🛠️ Tools Used
* [cite_start]`ssh` - To connect to the remote server [cite: 2, 3]
  
* [cite_start]`sha256sum` - To verify file integrity [cite: 7]
  
* [cite_start]`grep` - To filter specific data [cite: 7, 9]

Approach & Solution
### Step 1: Connect to the picoCTF server (SSH)💻
* Open your terminal and use the provided SSH command to connect to the challenge instance:

Bash

`ssh -p 51983 ctf-player@rhea.picoctf.net`

Note: Accept the fingerprint by typing yes and enter the password provided in the challenge description when prompted.

### Step 2: Find the real flag file (Using Checksum and Grep)
* Once connected, running the ls command reveals a files/ directory containing many dummy files and an executable script named decrypt.sh.

* Instead of manually checking the hash of each file, use the sha256sum command to calculate hashes for all files in the directory and pipe the output to `grep` to filter for the specific checksum:

Bash

`sha256sum files/* | grep "5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda` 

`sha256sum files/*: Calculates the SHA-256 hash for every file in the files folder.`


`| grep "..."`: Filters the results to only show the line containing the target hash.

* The output will display the hash alongside the correct file path (e.g., files/target_file_name).

### Step 3: Decrypt the file to get the Flag🚩
* Now that the correct file is identified, use the provided decryption script:

Bash

`./decrypt.sh files/<the_file_name_you_found`

Replace <the_file_name_you_found> with the actual filename from Step 2.

Executing this will successfully decrypt the file and reveal the flag.🚩

## Takeaways⚠️
* Using sha256sum to verify file integrity.

* Combining commands with the pipe | operator and using grep to filter large outputs efficiently.
