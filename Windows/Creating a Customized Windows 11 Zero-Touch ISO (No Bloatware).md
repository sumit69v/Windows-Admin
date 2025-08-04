# Creating a Customized Windows 11 Zero-Touch ISO (No Bloatware)

---

**Author:** Sumit Shrestha

**Date:** August 4, 2025

**Version:** 1.0

**Purpose:** This document outlines the full process of creating a customized Windows 11 installation ISO that installs automatically (zero-touch) and removes all default bloatware.

---

## 🧰 Prerequisites

Before you begin, download the following:

| Tool                          | Purpose                      | Link                                                                                                        |
| ----------------------------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Windows 11 ISO**            | Base installation media      | [Download from Microsoft](https://www.microsoft.com/software-download/windows11)                            |
| **Unattended File Generator** | Create unattended setup file | [Generate autounattend.xml files for Windows&#xA0;10/11](https://schneegans.de/windows/unattend-generator/) |
| **AnyBurn Software**          | ISO editor                   | [Download AnyBurn](https://www.anyburn.com/download.php)                                                    |
| **Hyper-V** *(optional)*      | For testing                  | Built-in on Windows Pro/Enterprise                                                                          |

---

## 📌 Step 1: Generate Unattended Installation File

1. Go to: [Generate autounattend.xml files for Windows&#xA0;10/11](https://schneegans.de/windows/unattend-generator/)
2. Fill in the following details:
   - **Windows Edition** (e.g., Windows 11 Pro)
   - **Language** (e.g., en-US)
   - **Product Key** *(Use generic or your own)*
   - **User account** and password
   - **Time zone**, **keyboard layout**, and other preferences
   - Enable **automatic partitioning** to erase and format the disk
3. Scroll to the bottom and click **“Download file”**
4. Save the file as `autounattend.xml`

---

## 📌 Step 2: Download Windows 11 ISO

1. Visit the Microsoft official site:
   
   [Download Windows 11](https://www.microsoft.com/software-download/windows11)

2. Scroll to **"Download Windows 11 Disk Image (ISO)"**

3. Choose **Windows 11 (multi-edition ISO)** → click **Download**

4. Select language and confirm download

---

## 📌 Step 3: Install and Open AnyBurn

1. Download and install AnyBurn:
   
   [Download AnyBurn](https://www.anyburn.com/download.php)

2. Open **AnyBurn**

3. Choose **“Edit Image File”**

4. Select the **Windows 11 ISO** you downloaded earlier

---

## 📌 Step 4: Add `autounattend.xml` to ISO

1. Once the ISO contents are visible in AnyBurn:
   
   - Drag and drop the `autounattend.xml` file into the **root directory** of the ISO

2. Click **Next**

3. Save the new ISO as:
   
   `Windows11-ZeroTouch.iso` or another custom name

---

## 📌 Step 5: Create Virtual Machine in Hyper-V (For Testing)

> Skip this step if you’re installing on real hardware.

1. Open **Hyper-V Manager**
2. Click **New > Virtual Machine**
3. Set:
   - **Name**: e.g., Win11-ZeroTouch
   - **Generation**: **Generation 2**
   - **Startup memory**: 4GB or more
   - **Virtual hard disk**: Create a new one (64GB+)
   - **Install from ISO**: Browse and select `Windows11-ZeroTouch.iso`
4. Complete setup and start the VM

---

## 🧪 Step 6: Test Installation

- Boot the virtual machine.
- The system should **automatically install Windows 11** using the predefined settings in the `autounattend.xml` file.
- No user interaction should be required.
- You should land directly on the desktop with your specified user account logged in.

---

## 🧼 Optional: Remove Bloatware (If Not Already Removed)

If any unwanted apps remain after installation, use PowerShell commands like:

```powershell
Get-AppxPackage *xbox* | Remove-AppxPackage
Get-AppxPackage *solitaire* | Remove-AppxPackage
```

Or use a script like [Windows10Debloater](https://github.com/Sycnex/Windows10Debloater) (still works for Windows 11 with minor tweaks).

---

## ✅ Final Outcome

You now have a fully automated Windows 11 ISO that:

- Installs without any user interaction
- Skips license agreement, region, and keyboard setup
- Automatically creates your user account
- Can optionally remove built-in bloatware

---

## 📁 File Summary

| File Name                 | Purpose                                        |
| ------------------------- | ---------------------------------------------- |
| `autounattend.xml`        | Configuration file for unattended installation |
| `Windows11.iso`           | Original Windows 11 installation ISO           |
| `Windows11-ZeroTouch.iso` | Customized ISO for deployment                  |
