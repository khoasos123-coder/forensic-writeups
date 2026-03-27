# [cite_start]picoCTF - Verify Write-up [cite: 1]

## Challenge Details
- **Event:** picoCTF 
- **Category:** Forensics
- **Difficulty:** Easy

## Approach & Solution

### [cite_start]Step 1: Connect to the picoCTF server (SSH) [cite: 2]
[cite_start]Open your terminal and use the provided SSH command to connect to the challenge instance[cite: 3]:

```bash
ssh -p 51983 ctf-player@rhea.picoctf.net
Note: Accept the fingerprint (type yes) and enter the password provided in the challenge description when prompted.
Step 2: Find the real flag file (Using Checksum and Grep)
Once connected, if you run the ls command, you will see a files/ directory containing many dummy files and an executable script named decrypt.sh.Instead of manually checking the hash of each file, we can use the sha256sum command to calculate the hashes of all files within the files/ directory. We can then pipe that output into grep to filter for the exact checksum provided in the challenge.
Run the following command in your terminal:
sha256sum files/* | grep "5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda"
The output will display the hash alongside the correct file path (e.g., files/target_file_name). Copy or remember this specific file name.
Step 3: Decrypt the file to get the Flag
Now that we know exactly which file is the real one , we can use the provided decryption script.
Execute the script and pass the correct file path as an argument:
./decrypt.sh files/<the_file_name_you_found>
Executing this will successfully decrypt the file and reveal the flag!
Takeaways
Using sha256sum to verify file integrity.
Combining commands with the pipe | operator and using grep to filter large outputs efficiently.
