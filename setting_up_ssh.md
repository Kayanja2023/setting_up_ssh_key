#  GitHub SSH Key Setup 

This README documents the successful setup of an SSH connection between a local machine and GitHub for the user **Andile Michael Kayanja Lwanga (`Kayanja2023`)**.

---

##  Objective
Establish a secure and password-less connection to GitHub using SSH, enabling streamlined cloning, pushing, and pulling from remote repositories.

---

##  SSH Key Generation

**Command used:**
```bash
ssh-keygen -t ed25519 -C "KayanjaLwanga@outlook.com"
```

- The key pair was saved to the default path:
  - Private key: `C:\Users\Dell\.ssh\id_ed25519`
  - Public key: `C:\Users\Dell\.ssh\id_ed25519.pub`
- A passphrase was added for enhanced security.

---

##  Public Key Copied to Clipboard

**PowerShell Command:**
```powershell
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub | Set-Clipboard
```

This ensured the **correct public key** was copied in OpenSSH format.

---

##  Key Added to GitHub

- Navigated to: [https://github.com/settings/keys](https://github.com/settings/keys)
- Clicked: **"New SSH key"**
- Title: `new_ssh`
- Pasted the public key into the Key field
- Clicked **"Add SSH key"**
- GitHub confirmed: **“You have successfully added the key.”**

---

##  SSH Connection Verified

**Tested with:**
```bash
ssh -T git@github.com
```

**Result:**
```
Hi Kayanja2023! You've successfully authenticated, but GitHub does not provide shell access.
```

---

##  Cloning a Repository (Example)

```bash
git clone git@github.com:Kayanja2023/your-repo-name.git
```

Replace `your-repo-name` with the actual repository you wish to clone.

---

##  Cleanup / Missteps Resolved

- Accidentally attempted to upload a **private key** → Resolved by deleting old key pair and regenerating it correctly.
- Used **PowerShell instead of CMD** to run `Remove-Item` and clipboard commands properly.

---

##  Lessons Learned

- GitHub only accepts public keys in **OpenSSH format** (e.g., starting with `ssh-ed25519`).
- **Private keys must never be uploaded** or shared.
- PowerShell offers better support for Git-related operations on Windows than CMD.

---

##  Useful Commands Summary

| Task                             | Command |
|----------------------------------|---------|
| Generate SSH Key                 | `ssh-keygen -t ed25519 -C "you@example.com"` |
| Copy public key to clipboard     | `Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub | Set-Clipboard` |
| Test SSH connection              | `ssh -T git@github.com` |
| Clone repo using SSH             | `git clone git@github.com:username/repo.git` |
| Change remote to SSH             | `git remote set-url origin git@github.com:username/repo.git` |

---

## Status

**SSH Authentication to GitHub: Fully Operational**  
Ready to use for cloning, pushing, and pulling from remote repositories via SSH.

---
