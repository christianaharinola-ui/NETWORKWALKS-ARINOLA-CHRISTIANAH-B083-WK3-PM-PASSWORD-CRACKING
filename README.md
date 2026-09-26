# 🔐Password Cracking

**W3-PM-FINAL | Cybersecurity | Networkwalks**

![Skill](https://img.shields.io/badge/Skill-Cybersecurity-red)
![Skill](https://img.shields.io/badge/Skill-Password%20Cracking-red)
![Skill](https://img.shields.io/badge/Skill-Hash%20Analysis-red)
![Tool](https://img.shields.io/badge/Tool-John%20the%20Ripper-blue)
![Tool](https://img.shields.io/badge/Tool-Johnny-blue)
![Tool](https://img.shields.io/badge/Tool-Hash%20Calculator-blue)
![Kali Linux](https://img.shields.io/badge/Kali-Linux-purple)
![NetworkWalks](https://img.shields.io/badge/NetworkWalks-grey)
![Ethical Hacking](https://img.shields.io/badge/Ethical%20Hacking-black)

## Introduction

I completed two modules that approached the same underlying task, recovering the password of a locked PDF file, using two different toolsets: John the Ripper (JTR) with its Johnny GUI (W3-PM1), and Networkwalks' own browser-based Hash Calculator and Password Cracker tools.

The purpose of covering the same task with two different tools was to understand the underlying process which is extracting a password hash from a protected file, then running that hash through a cracking tool, independent of which specific software is used to do it.

## Tools Used

| Tool | Purpose |
|---|---|
| John the Ripper (JTR) | Command-line password cracking tool, tests password hashes against wordlists |
| Johnny | Graphical front-end for John the Ripper |
| Networkwalks Hash Calculator | Browser-based tool to extract a password hash from a locked PDF |
| Networkwalks Password Cracker | Browser-based tool to crack a password from a given hash |
| Notepad | Used to save the extracted hash in the correct plain-text format |

---

## Activities Performed

### PM1 — Password Cracking with JTR (John the Ripper & Johnny)

**Step 1 — Install John the Ripper**
I downloaded John the Ripper for Windows from the official Openwall website.

**Step 2 — Install Johnny (GUI)**
I downloaded and installed Johnny, the graphical front-end for John the Ripper, and pointed its settings to the `john.exe` file located in JTR's run folder.

<img width="892" height="706" alt="Johnny install" src="https://github.com/user-attachments/assets/8b0d919e-730f-4ef4-bb07-05a22ddfeab7" />

**Step 3 — Extract the PDF's password hash**
I uploaded the locked PDF to an online PDF hash extractor tool, which returned the file's hash value in the format starting with `$pdf$...`. I copied this hash exactly, making sure not to include any extra characters (such as a leading `b'` sometimes added when copying from certain tools).

<img width="1459" height="579" alt="PDF Extractor" src="https://github.com/user-attachments/assets/24aac75d-2c03-4370-84a5-93d215610449" />

**Step 4 — Save the hash to a text file**
I pasted the hash into Notepad and saved it as `hash1.txt`, ready to be loaded into Johnny.

<img width="1451" height="805" alt="PDF 1 HASH" src="https://github.com/user-attachments/assets/2b30549e-39b2-4055-9a36-1cf65a214d82" />

**Step 5 — Run the attack**
In Johnny, I used "Open password file" to load `hash1.txt`, then clicked "Start new attack." Johnny/JTR worked through its wordlist, testing candidate passwords against the hash until a match was found.

<img width="932" height="709" alt="hash 1 cracking process" src="https://github.com/user-attachments/assets/2de70307-2272-43ee-8e1b-889ef9526c16" />

**Step 6 — Verify the cracked password**
Once JTR reported a match, I opened the original locked PDF and entered the recovered password, confirming it opened successfully.

<img width="1287" height="912" alt="JTR Cracked pdf 3" src="https://github.com/user-attachments/assets/89559cee-642e-468e-bddb-abc8215a104b" />
<img width="1322" height="906" alt="JTR Cracked pdf 2" src="https://github.com/user-attachments/assets/871bbc41-3e7a-4ba3-b75b-74946e7ac7c7" />
<img width="1707" height="998" alt="cracked pdf 1" src="https://github.com/user-attachments/assets/288a7324-d7ca-4be1-bf7f-a61ed8d77a41" />

**Result:** The password was successfully cracked. 

---

### PM2 — Password Cracking with Networkwalks Tools

**Step 1 — Download the target file**
I downloaded the same locked PDF, `My Locked PDF1.pdf`, from the Networkwalks lab page.

**Step 2 — Extract the hash using the Hash Calculator**
I opened Networkwalks' browser-based Hash Calculator tool and uploaded the locked PDF. The tool read the file and returned its hash value, starting with `$pdf$...`, without needing any software installed locally.

<img width="1795" height="639" alt="Hash calculator" src="https://github.com/user-attachments/assets/9320db76-357b-4b8f-a583-e2a13adb3f45" />

**Step 3 — Copy the hash**
I copied the complete hash value exactly as returned by the tool.

**Step 4 — Crack the hash using the Password Cracker**
I opened Networkwalks' Password Cracker tool, pasted the hash value in, and started the attack. The tool tried candidate passwords against the hash until it found a match.

<img width="1316" height="903" alt="Cracked password with networkwalks" src="https://github.com/user-attachments/assets/62ced6dc-e3f2-4f7b-ae15-793e7632909d" />

**Step 5 — Verify the cracked password**
I opened the locked PDF and entered the password shown by the tool, confirming it opened successfully.

<img width="1263" height="806" alt="Locked file, opened with Networkwalks" src="https://github.com/user-attachments/assets/75f1c506-4fcf-43cf-89ab-e33d983d032a" />

**Result:** The password was successfully cracked using entirely browser-based tools, with no local software installation required, matching the result obtained in PM1 via JTR/Johnny.

---

## Concepts Learned

**Encryption vs. Hashing**
Encryption is a two-way function — data that is encrypted can be decrypted again using the correct key. Hashing, by contrast, is a one-way function: it scrambles input (like a password) into a fixed-length value called a hash, and this process cannot be reversed directly. This is exactly why password cracking tools don't "decrypt" a password hash, instead, they generate guesses, hash each guess the same way the original password was hashed, and compare the result to the target hash. A match means the guess was correct.

**Why weak passwords are risky**
Both modules reinforced the same real-world point: a simple 8-character lowercase-only password can be cracked in minutes, while a strong 12+ character mixed-case password with numbers and symbols can take years to crack through the same method. Over 24 billion username/password pairs are already available on the dark web from past breaches, and passwords like "123456" and "password" remain among the most commonly used in the world every year — meaning weak passwords are often cracked not through sophisticated attacks, but simply because they appear early in standard wordlists.

---

## Recommendations

**Use long, complex passwords**
Passwords should combine uppercase, lowercase, numbers and symbols, and be at least 12 characters long to meaningfully resist dictionary and brute-force attacks.

**Avoid common or predictable passwords**
Passwords appearing in known breach lists (such as "123456" or "password") should never be used, since they are the first candidates tried by any cracking tool.

**Use a password manager**
Rather than relying on memorable (and therefore guessable) passwords, a password manager allows for long, random, unique passwords per account or file.

**Understand that file-level password protection has limits**
Password-protecting a file (PDF, ZIP, Office document) is not equivalent to strong encryption if the password itself is weak — the protection is only as strong as the password chosen.

**Use multi-factor protection where possible**
For genuinely sensitive files or systems, rely on additional protection layers beyond a single password where the platform supports it.

---

## Conclusion

During Week 3 of my Cybersecurity & Ethical Hacking internship, I completed two password cracking modules that approached the same task from two different angles, (John the Ripper with the Johnny GUI) and a browser-based toolset (Networkwalks' own Hash Calculator and Password Cracker).

Both modules successfully recovered the password of the same locked PDF file, reinforcing that the underlying process, extract the hash, then run it through a cracking tool is consistent regardless of which specific software performs it.

I learned the important distinction between encryption and hashing, and why password cracking tools work by hashing guesses rather than decrypting anything directly. I also gained a much more concrete understanding of why password strength matters in practice: the difference between a password cracked in minutes versus one that would take years isn't abstract, it's the direct, observable result of password length and complexity.

## 👤 Author

Arinola Oluwadamilola Christianah
Cybersecurity Intern, Batch B083

LinkedIn: https://www.linkedin.com/in/christianaharinola/

## 📌 Project Information

**Program Name:** Cybersecurity program at Networkwalks | **Week:** 03 | **Repository:** GitHub
