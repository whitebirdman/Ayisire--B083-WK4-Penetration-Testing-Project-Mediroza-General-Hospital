# Milestone 2 — PDF Encryption & Password Recovery

## Objective

The objective of Milestone 2 was to analyze and recover the passwords protecting the three PDF laboratory reports obtained during Milestone 1.

**Written permission:** Granted as part of the Network Walks laboratory exercise.

All three reports were successfully downloaded from the authenticated patient portal.

---

## 1. Obtaining the Reports

Following the successful authentication bypass documented in Milestone 1, the authenticated patient portal provided access to three encrypted PDF reports.

The three files were downloaded for the password-recovery exercise.

📸 **Evidence:** `images/M2-01-three-pdfs.png`

---

## 2. Hash Extraction & Password Recovery

The Network Walks **Hash Calculator** and **Password Cracker** tools were used to process the encrypted PDF files.

Workflow:

```text
Encrypted PDF
     ↓
Hash extraction
     ↓
Password-cracking tool
     ↓
Wordlist testing
     ↓
Password recovered
     ↓
PDF contents accessed
```

The three reports were individually hashed and tested against available password candidates.

---

## 3. Report 1

The hash for Report 1 was generated using the Network Walks Hash Calculator and subsequently submitted to the Network Walks Password Cracker.

The password was successfully recovered:

```text
123456
```

📸 **Evidence:**

* `images/M2-02-report1-hash.png`
* `images/M2-03-report1-cracked.png`

The recovered password was then used to successfully open the encrypted PDF.

---

## 4. Report 2

Report 2 was processed using the same general workflow.

The password was successfully recovered:

```text
password
```

The recovered password was then used to access the encrypted PDF.

📸 **Evidence:**

* `images/M2-04-report2-hash.png`
* `images/M2-05-report2-cracked.png`

---

## 5. Report 3

Report 3 required a different approach.

The Network Walks Password Cracker initially failed to recover the password because its available wordlist was limited to approximately **100 candidate words**.

The recovered password was:

```text
!@#$%^&
```

### Wordlist Testing

Several approaches were attempted:

| Attempt | Wordlist / Method                      | Result                                    |
| ------- | -------------------------------------- | ----------------------------------------- |
| 1       | Network Walks default password cracker | Failed                                    |
| 2       | `rockyou.txt`                          | Not practical for the available tool/size |
| 3       | `fasttrack.txt`                        | Failed                                    |
| 4       | Nmap-related wordlist                  | Failed                                    |
| 5       | John the Ripper default password list  | **Successful**                            |

The successful approach used the John the Ripper password list and recovered:

```text
!@#$%^&
```

📸 **Evidence:**

* `images/M2-06-report3-hash.png`
* `images/M2-07-report3-wordlist-tests.png`
* `images/M2-08-report3-jtr-success.png`

---

## 6. Results

| Report   | Password   | Recovery Result        |
| -------- | ---------- | ---------------------- |
| Report 1 | `123456`   | Successfully recovered |
| Report 2 | `password` | Successfully recovered |
| Report 3 | `!@#$%^&`  | Successfully recovered |

All three encrypted PDFs were successfully opened after recovering their passwords.

---

## 7. Key Observation

The exercise demonstrated that password recovery success depends heavily on the quality and coverage of the wordlist being tested.

The Network Walks Password Cracker successfully recovered the first two passwords using its available candidate list. However, the third password consisted entirely of special characters and was not present within the tool's limited candidate list.

Alternative wordlists were therefore tested before John the Ripper's available password list successfully recovered the third password.

This demonstrated why password-recovery exercises may require different tools and wordlists rather than relying on a single approach.

---

## 8. Evidence

The following screenshots document the Milestone 2 process:

```text
images/
├── M2-01-three-pdfs.png
├── M2-02-report1-hash.png
├── M2-03-report1-cracked.png
├── M2-04-report2-hash.png
├── M2-05-report2-cracked.png
├── M2-06-report3-hash.png
├── M2-07-report3-wordlist-tests.png
└── M2-08-report3-jtr-success.png
```

> **Privacy:** The actual PDF files and confidential medical information are not included in the public repository. Screenshots should be redacted before publication.

---

## Milestone 2 Conclusion

All three encrypted laboratory-report PDFs were successfully processed and their passwords recovered.

Reports 1 and 2 were recovered using the Network Walks hashing and password-cracking workflow. Report 3 required additional wordlist testing before John the Ripper successfully recovered its password.

This completed the Milestone 2 requirement:

> **Recovered contents of all three files with proof of successful access.**

