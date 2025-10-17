# Writeup RED  PicoCTF (Forensics) 2025

Task: Download the image red.png and find the flag.


## Steps

Step 1) I inspect the file utilizing "file" and "exiftool" commands.File just gives me the properties of my file and exiftool shows metadata properties and comments. I notice a weird poem displayed at the bottom

<img width="1446" height="661" alt="image" src="https://github.com/user-attachments/assets/7ea0a3fd-5a5d-405e-86aa-25e54aaefdf3" />


Step 2) I utilize the "strings" command, since I'm given a png with no information. The strings command helps extract known variables from files. I notice I see the poem again, so it must be important. I decide to use zsteg and xxd to explore further. Zsteg is designed to detect and extract hidden data within image files liek png and jpg. XXd creates and analyzes hexadecimal dumps from files.

<img width="387" height="337" alt="image" src="https://github.com/user-attachments/assets/6dab48b7-3ca3-444c-ba8b-2fc530d1adad" />

<img width="850" height="1038" alt="image" src="https://github.com/user-attachments/assets/a8efd37a-6554-458a-a33f-35008eb0e1d7" />




Step 3) As mentioned earlier, now I utilzie zsteg and notice it gives me a base 64 code that needs to be decoded. 

<img width="1868" height="411" alt="image" src="https://github.com/user-attachments/assets/0278194d-3521-4772-8c4c-c023fcaba273" />

Step 4) Now, I do simple decoding utilizing the "echo" command, which prints texts or variables to a terminal


echo "cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==" | base64 --decode

This results in my final answer, picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}
