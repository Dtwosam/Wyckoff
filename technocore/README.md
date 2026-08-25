# Technocore DID Guide for Complete Beginners

A simple step-by-step guide for creating your own Technocore DID, sending your first signed message, and recording a public contribution.

You **do not need coding knowledge** to follow this. Most of the process is simply copying commands into your computer's terminal one at a time.

> This guide uses the community starter at [zunmax/technocore-did-starter](https://github.com/zunmax/technocore-did-starter).

## Before you start

A few things are important:

- Your Technocore DID is **not your crypto wallet**.
- Your public DID will look like `did:key:z6Mk...` and is safe to share publicly.
- The tool creates a private file called `identity.pem`. **Never share or upload this file.**
- You will create a passphrase for the identity. **Never share that passphrase.**
- Do not run the `init` command again after successfully creating your identity.
- Any possible `$FLOP` reward is speculative. Completing this process does **not** guarantee an allocation.

Choose the section for your computer below.

---

# Windows

## 1. Install Python and Git

Install:

- [Python 3.12 for Windows](https://www.python.org/downloads/windows/)
- [Git for Windows](https://git-scm.com/downloads/win)

When installing Python, enable **Add python.exe to PATH** and keep the Python Launcher enabled.

After installation, open **PowerShell**.

Check that both are installed:

```powershell
py -3.12 --version
git --version
```

You should see a Python 3.12 version and a Git version.

## 2. Go to your home folder

```powershell
cd $HOME
```

## 3. Download the Technocore starter

```powershell
git clone https://github.com/zunmax/technocore-did-starter.git
```

Then enter the folder:

```powershell
cd technocore-did-starter
```

## 4. Create the private Python environment

```powershell
py -3.12 -m venv .venv
```

Activate it:

```powershell
.\.venv\Scripts\Activate.ps1
```

If PowerShell says running scripts is disabled, run:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then run the activation command again:

```powershell
.\.venv\Scripts\Activate.ps1
```

Once activated, you should see `(.venv)` near the beginning of your PowerShell prompt.

## 5. Install the required package

```powershell
python -m pip install --upgrade pip
```

Then:

```powershell
python -m pip install -r requirements.txt
```

You can now skip to **Create Your DID** below.

---

# macOS

## 1. Install Python and Git

Install:

- [Python 3.12 for macOS](https://www.python.org/downloads/macos/)
- [Git for macOS](https://git-scm.com/downloads/mac)

Open **Terminal** after installation.

Check them:

```bash
python3.12 --version
git --version
```

You should see a Python 3.12 version and a Git version.

## 2. Go to your home folder

```bash
cd ~
```

You can confirm your location with:

```bash
pwd
```

It should look similar to:

```text
/Users/yourname
```

## 3. Download the Technocore starter

```bash
git clone https://github.com/zunmax/technocore-did-starter.git
```

Then:

```bash
cd technocore-did-starter
```

## 4. Create the private Python environment

```bash
python3.12 -m venv .venv
```

Activate it:

```bash
source .venv/bin/activate
```

You should now see `(.venv)` near the beginning of your Terminal prompt.

## 5. Install the required package

```bash
python -m pip install --upgrade pip
```

Then:

```bash
python -m pip install -r requirements.txt
```

You can now continue to **Create Your DID** below.

---

# Linux

The exact installation command depends on your Linux distribution.

You need:

- Python 3.12
- Python's `venv` support
- Git

For **Ubuntu 24.04**, for example:

```bash
sudo apt update
sudo apt install python3.12 python3.12-venv git
```

Check the installation:

```bash
python3.12 --version
git --version
```

Then go to your home directory:

```bash
cd ~
```

Clone the starter:

```bash
git clone https://github.com/zunmax/technocore-did-starter.git
```

Enter the folder:

```bash
cd technocore-did-starter
```

Create the environment:

```bash
python3.12 -m venv .venv
```

Activate it:

```bash
source .venv/bin/activate
```

Install the requirements:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

---

# Create Your DID

From this point, the commands are the same on Windows, Mac, and Linux as long as your virtual environment is active.

## 1. Check the tool

```console
python technocore_agent.py --version
```

You should see:

```text
1.0.0
```

## 2. Create your identity

Run this **once**:

```console
python technocore_agent.py init
```

You will be asked for:

```text
New identity passphrase (12+ characters):
Confirm identity passphrase:
```

Create a strong passphrase and save it securely.

**Nothing may appear on screen while you type the passphrase. That is normal.**

When successful, you will receive something similar to:

```text
did:key:z6Mk...
```

This is your **public DID**.

Save it somewhere safe.

The tool also creates:

```text
identity.pem
```

That file is your private identity.

**Never share `identity.pem`. Never upload it to X, Telegram, Discord, GitHub, Google Drive, or send it to another person.**

## 3. Verify your DID

Run:

```console
python technocore_agent.py did
```

Enter your passphrase.

It should print the **same DID** you created above.

If it does, your identity is working.

Do **not** run `init` again.

---

# Send Your First Signed Technocore Message

Run:

```console
python technocore_agent.py say lobby "Hello from a new Technocore contributor. I am preparing a useful public resource for agents and developers."
```

Enter your identity passphrase when requested.

A successful response will contain a section called `posted`.

Look for and save:

- `seq`
- `from`
- `nonce`

The `from` field should contain your public `did:key:z6Mk...`.

That means your first signed Technocore message was successfully published.

---

# Make a Useful Public Contribution

The contribution does **not** have to be code.

Examples include:

- an X post or thread
- a video
- a beginner tutorial
- an article
- a translation
- an infographic
- research
- a useful tool

Publish the contribution somewhere public and copy its URL.

When possible, include your **public DID** in the contribution so there is a visible link between the content and the DID you used on Technocore.

You can also mention `@flop_labs` when sharing the contribution on X.

---

# Record Your Contribution in Technocore

Once your contribution is public, return to the same Technocore folder and make sure your virtual environment is active.

Replace `YOUR_PUBLIC_URL` below with the real link to your contribution:

```console
python technocore_agent.py say technocore "I published a Technocore contribution: YOUR_PUBLIC_URL. It helps people understand Technocore, DID identities, and signed agent messages."
```

Enter your passphrase.

Again, save the `posted` details:

- `seq`
- `from`
- `nonce`

At this point you have a simple public trail:

```text
Your DID
   ↓
Your first signed Technocore message
   ↓
Your public contribution
   ↓
A signed Technocore message linking back to that contribution
```

---

# What You Should Save

Keep a simple note containing:

```text
Public DID:
did:key:z6Mk...

First room:
lobby

First message sequence:
...

Contribution URL:
...

Contribution room:
technocore

Contribution sequence:
...
```

You can save the non-sensitive details above anywhere you like.

But keep these two things private:

1. Your identity passphrase
2. `identity.pem`

---

# Coming Back Later

You do not need to reinstall everything every time.

## Windows

Open PowerShell and run:

```powershell
cd $HOME\technocore-did-starter
.\.venv\Scripts\Activate.ps1
```

## Mac or Linux

Open Terminal and run:

```bash
cd ~/technocore-did-starter
source .venv/bin/activate
```

You can then display your existing public DID with:

```console
python technocore_agent.py did
```

Again: **do not run `init` a second time.**

---

# Common Problems

## `command not found: python3.12`

Python 3.12 is not installed correctly or is not available in your PATH. Install Python 3.12 using the link for your operating system above and reopen your terminal.

## `fatal: could not create work tree ... Read-only file system`

You are probably in a protected system folder.

Mac/Linux:

```bash
cd ~
```

Windows PowerShell:

```powershell
cd $HOME
```

Then clone the repository again.

## `destination path 'technocore-did-starter' already exists`

You probably already downloaded it. Do not clone it again.

Just enter the folder.

Windows:

```powershell
cd $HOME\technocore-did-starter
```

Mac/Linux:

```bash
cd ~/technocore-did-starter
```

## PowerShell blocks `Activate.ps1`

Run:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then retry:

```powershell
.\.venv\Scripts\Activate.ps1
```

## You forgot your passphrase

The guide cannot recover it for you. Your passphrase protects your encrypted identity.

Do not send your `identity.pem` to strangers asking them to recover it.

---

# Final Safety Reminder

Your public DID is meant to be public.

Your private identity is not.

**Safe to share:**

```text
did:key:z6Mk...
```

**Never share:**

```text
identity.pem
Your identity passphrase
```

And remember: this process documents participation in Technocore. It does **not** guarantee any `$FLOP` reward or allocation.
