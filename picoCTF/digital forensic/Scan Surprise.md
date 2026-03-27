
# 🛡️ picoCTF - Scan Surprise Write-up

* 🚀 Steps to Solve

## 1️⃣ Download the Challenge File

*Use the wget command to download the provided .zip file from the picoCTF server to your local machine:

Bash

`wget <URL_from_picoCTF>`

##2️⃣ Extract the Zip File

* Use the unzip command to extract the contents of the downloaded file:
  
<img width="592" height="175" alt="image" src="https://github.com/user-attachments/assets/cb4ad81f-9afe-4645-bbde-d8197f951516" />

Bash

`unzip challenge.zip`

* After extracting, you will find a directory structure (e.g., home/ctf-player/drop-in/). Inside, there is an image file named flag.png, which is a QR Code.

## 3️⃣ Convert QR Code to Text

* To decode the QR code without using a phone, install and use the ZBar tool.

Installation (on Kali Linux):

<img width="611" height="84" alt="image" src="https://github.com/user-attachments/assets/b600c7bf-492a-4bd4-9173-3fd463cd67c5" />

Bash

`sudo apt update`

`sudo apt install zbar-tools`

* Decoding the image:

* Once installed, run the zbarimg command followed by the path to the QR code image:

Bash

`zbarimg flag.png`


###🚩 Flag

*After running the command, the terminal will display the decoded text:

> picoCTF{4n_0pt1c4l_5urpr153_73225212}
