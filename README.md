# 🔐 Week 3 – Password Cracking with John the Ripper & NetworkWalks Tools

### Password Security Assessment | Cybersecurity Internship | NETWORKWALKS

---

## 📌 Project Overview

This project documents the completion of **Week 3 – Project Modules 1 and 2: Password Cracking** as part of my cybersecurity training with **NETWORKWALKS**.

The project focuses on understanding how password-protected PDF documents can be assessed using password-recovery tools. It explores two approaches:

- **Project Module 1 (W3-PM1):** Password Cracking with John the Ripper (JTR).
- **Project Module 2 (W3-PM2):** Password Cracking with NetworkWalks Tools.

Both modules demonstrate how password-protected files can be assessed by extracting their encryption-related hash data and testing candidate passwords against it.

The practical exercises provided an opportunity to understand dictionary attacks, wordlists, PDF password protection, and the importance of choosing strong and unpredictable passphrases.

## 🎯 Objectives

The main objectives of this project were to:

- Understand how password-protected PDF files are secured.
- Extract PDF password hashes into a format supported by password-auditing tools.
- Verify the installation and functionality of John the Ripper.
- Use John the Ripper to perform a dictionary-based password audit.
- Explore Johnny, the graphical interface for John the Ripper.
- Use NetworkWalks browser-based tools to perform a comparable exercise.
- Compare the effectiveness of different wordlists.
- Verify recovered passwords against the original training documents.
- Document the process, observations, results, and lessons learned.

## 🛡️ Purpose of the Lab

The purpose of this lab is to demonstrate how security professionals assess the strength of password-protected files.

Password auditing helps identify weak or predictable passwords that could expose protected information if an unauthorised person obtains a copy of the encrypted file.

The exercises use instructor-provided training documents in a controlled learning environment.

⚠️ **Important:** All password-recovery activities documented in this repository were performed for the assigned training exercises using supplied lab files. These techniques must only be used on files that you own or have explicit permission to assess.

## 🏗️ Lab Architecture

The project used a Windows host environment with Kali Linux running inside Oracle VirtualBox for the John the Ripper exercises. Browser-based NetworkWalks tools were used for the second module.

### Lab Environment Summary

| Component | Configuration |
|---|---|
| Host Operating System | Windows 11 |
| Virtualisation Platform | Oracle VirtualBox |
| Virtual Machine | Kali Linux |
| Module 1 | John the Ripper and supporting utilities |
| Graphical Interface | Johnny |
| Hash Extraction | `pdf2john` |
| Wordlist | `rockyou.txt` |
| PDF Verification | `qpdf` |
| Module 2 | NetworkWalks Hash Calculator and Password Cracker |
| Browser | Firefox |
| Target Files | NetworkWalks-provided password-protected PDF documents |
| Network Configuration | NAT |

## 🪜 Project Procedure

# Phase 1: Project Module 1 – Password Cracking with John the Ripper

### Step 1. Verify John the Ripper

John the Ripper was checked inside the Kali Linux environment to confirm that the tool was installed and functional before proceeding.

Command used:

```bash
john --test
```

<details>
<summary>Evidence: John the Ripper tool verification</summary>

Screenshot: `01-john-test.png`

</details>

### Step 2. Identify the Correct Training PDF

The password-protected PDF supplied for the exercise was identified before beginning the password audit.

The correct target file is important because the provided download bundle may contain multiple PDF documents with different passwords.

### Step 3. Extract the PDF Hash

The PDF encryption-related hash data was extracted using the `pdf2john` utility bundled with John the Ripper.

This process converts the PDF's password-protection information into a format that John can use during password auditing.

The extracted hash was saved in a text file for use during the exercise.

<details>
<summary>Evidence: PDF hash extraction</summary>

Screenshot: `02-hash-extraction.png`

</details>

### Step 4. Perform the Password Audit

John the Ripper was used to test password candidates against the extracted hash.

A dictionary-based approach was used to evaluate the supplied training document.

The wordlist provides candidate passwords that the tool can test against the hash.

### Step 5. Review the Recovered Password

After the password audit completed, the results were reviewed to determine whether a matching password had been recovered.

The recovered result was also checked using John the Ripper's result-display functionality.

<details>
<summary>Evidence: Password recovery and results</summary>

- `03-cracked-password.png`
- `04-john-show.png`

</details>

### Step 6. Verify the PDF

The recovered password was used to verify access to the original training PDF.

The exercise also included using `qpdf` to verify the recovered password and assess the protected document.

<details>
<summary>Evidence: Final verification</summary>

Screenshot: `05-flag-captured.png`

</details>

---

# Phase 2: Project Module 2 – Password Cracking with NetworkWalks Tools

### Step 1. Open the NetworkWalks Hash Calculator

The NetworkWalks Hash Calculator was used as the browser-based option for extracting password-related hash data from the supplied PDF exercise file.

The resulting hash information was used as input for the password-cracking exercise.

<details>
<summary>Evidence: Hash calculator</summary>

Screenshot: `01-hash-calculator.png`

</details>

### Step 2. Test the Available Password Candidates

The NetworkWalks Password Cracker was used to test candidate passwords against the extracted hash.

The exercise demonstrated how the size and contents of a wordlist affect the outcome of a dictionary attack.

### Step 3. Review the Results

The initial wordlist contained approximately 100 candidate passwords. It did not recover the password `good-luck`.

A comparison using `rockyou.txt`, containing approximately 14.3 million entries, recovered the matching password in 1.26 seconds.

These results demonstrated that the contents of a wordlist can make a significant difference to the outcome of a dictionary-based password audit.

<details>
<summary>Evidence: Password-cracking process</summary>

- `02-cracker-in-progress.png`
- `03-cracked-successfully.png`

</details>

### Step 4. Verify the Recovered Result

The recovered password was checked against the relevant supplied training document to confirm that the result was correct.

<details>
<summary>Evidence: Verification</summary>

Screenshot: `04-flag-captured.png`

</details>

---

## 🔎 Results & Observations

The two modules provided an opportunity to compare a locally operated password-auditing tool with browser-based password-auditing tools.

| Test / Observation | Result |
|---|---|
| John the Ripper verification | Tool functionality checked before the exercise |
| PDF hash extraction | Hash extracted using `pdf2john` |
| NetworkWalks short wordlist | Approximately 100 entries; did not recover `good-luck` |
| `rockyou.txt` comparison | Approximately 14.3 million entries |
| Recorded recovery time | 1.26 seconds |
| PDF verification | Recovered result checked against the training document |

### Key Observations

1. **Hash extraction is an important first step.** Password-auditing tools need the appropriate hash representation before they can test candidate passwords.

2. **Wordlist selection matters.** A password that is not present in a wordlist will not be recovered by that dictionary attack, regardless of how long the list is searched.

3. **Different tools can perform similar tasks.** John the Ripper and NetworkWalks tools provided different interfaces for exploring the same general password-auditing concept.

4. **Offline password attacks are different from online login attempts.** A person with a copy of a protected document can test password guesses without relying on the document owner's login system or its account-lockout controls.

---

## 🐞 Problems Encountered & Solutions

This section records the practical problems encountered during the exercises and the corresponding solutions.

| Problem | Observation / Resolution |
|---|---|
| Multiple PDF documents in the download bundle | Confirmed the correct target before proceeding because different files could have different passwords. |
| Short wordlist did not recover the password | Recognised that the candidate password was not successfully recovered with the available short list. A larger comparison wordlist was used in the assigned training exercise. |
| Hash formatting | Ensured the extracted hash was saved in the expected format before using it as input. |

Further problems and their exact resolutions should be added here when supported by the screenshots or terminal output.

---

## 💡 What I Learned

Through these exercises, I developed a better understanding of password protection, hash extraction, and dictionary-based password auditing.

The most important concepts I learned include:

### 1. Hash Extraction

I learned how PDF password-protection information can be extracted into a format that password-auditing software can process.

### 2. John the Ripper

I gained practical exposure to John the Ripper and learned about its role in auditing password strength using candidate passwords.

### 3. Dictionary Attacks

I learned how dictionary attacks work by testing candidate passwords against an extracted hash.

### 4. Wordlist Effectiveness

The comparison between the short wordlist and `rockyou.txt` demonstrated that a password's presence or absence in a wordlist can determine whether a dictionary attack succeeds.

### 5. File-Level Password Protection

I learned that password-protected files can be vulnerable to offline password guessing when weak or predictable passphrases are used.

### 6. Tool Comparison

Using both John the Ripper and NetworkWalks tools helped me understand how different interfaces can support similar password-auditing exercises.

### 7. Evidence and Documentation

I learned the importance of documenting each stage of a technical exercise, including tool verification, hash extraction, test results, password recovery, and final verification.

---

## 🔐 Security & Ethical Use

This project was completed strictly for educational purposes using instructor-provided training files.

The techniques explored in this project should only be used for authorised security assessments.

Key security recommendations:

- Use long, unique, and unpredictable passphrases to protect sensitive documents.
- Avoid dictionary words, common phrases, and predictable password patterns.
- Never reuse passwords across different accounts or protected files.
- Avoid uploading confidential documents to third-party hash-extraction services.
- Prefer trusted local tools when handling sensitive documents.
- Store recovered passwords securely and avoid including real credentials in public repositories.

---

## 🔗 Tools & Resources

| Tool / Resource | Link |
|---|---|
| John the Ripper – Openwall | https://www.openwall.com/john/ |
| JtR Binaries – GitHub Releases | https://github.com/openwall/john-packages/releases/latest |
| Johnny GUI | https://openwall.info/wiki/john/johnny |
| NetworkWalks Lab Page | https://networkwalks.com/project-task-lab-password-cracking-with-john-the-ripper/ |
| NetworkWalks Hash Calculator | https://networkwalks.com/hash-calculator/ |
| NetworkWalks Password Cracker | https://networkwalks.com/password-cracker/ |

---

## 👤 Author

**Warona Baji**

Cybersecurity Intern | NETWORKWALKS

GitHub: https://github.com/WARONA-cmyk

LinkedIn: linkedin.com/in/warona-baji-300231320

---

## 📌 Project Information

| Field | Details |
|---|---|
| Program | Cybersecurity Training / Internship |
| Organisation | NETWORKWALKS |
| Instructor / Training Reference | Waqas Karim |
| Week | 03 |
| Project | Password Cracking |
| Module 1 | Password Cracking with John the Ripper |
| Module 2 | Password Cracking with NetworkWalks Tools |
| Repository | NETWORKWALKS-WK3-PASSWORD-CRACKING |

---

**Project Outcome:** This project documents practical exposure to PDF hash extraction, password auditing, dictionary attacks, wordlist comparison, and file-password verification in a controlled training environment.
