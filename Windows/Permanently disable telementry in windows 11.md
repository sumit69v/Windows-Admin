## 🛡️ How to Permanently Disable Telemetry in Windows 11

Telemetry in Windows 11 collects diagnostic and usage data to help Microsoft improve system performance and security. However, many users prefer to limit or disable this data collection for privacy reasons. This guide outlines five effective methods to reduce or disable telemetry.

---

### 📊 What Is Telemetry?

Telemetry is the automated collection and transmission of data from your device to Microsoft. It includes:

- Device performance
- Usage patterns
- System health
- Voice clips and activity history

Microsoft uses this data to improve Windows services, but some of it may be shared in anonymized form with third parties.

---

### 🔧 Methods to Disable Telemetry

#### 1. **Turn Off Optional Diagnostic Data**

- Go to **Settings** → **Privacy & Security** → **Diagnostics & Feedback**
- Disable **Send optional diagnostic data**
- Also disable:
  - **Store my activity history**
  - **Contribute voice clips**
  - All toggles under **General**

> 📝 This reduces telemetry but does not eliminate it entirely.

---

#### 2. **Use Registry Editor**

- Open **Run** (`Win + R`) → type `regedit`
- Navigate to:  
  `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\DataCollection`
- Create a new DWORD:
  - Name: `AllowTelemetry`
  - Value: `0`

> ⚠️ Be cautious when editing the registry.

---

#### 3. **Disable Telemetry Services via Services.msc**

- Open **Run** → type `services.msc`
- Locate and disable:
  - **Connected User Experiences and Telemetry**
  - **dmwappushsvc**

---

#### 4. **Use Task Scheduler**

- Open **Task Scheduler**
- Navigate to:  
  `Task Scheduler Library > Microsoft > Windows > Customer Experience Improvement Program`
- Disable all tasks listed

---

#### 5. **Use Group Policy Editor (Pro & Enterprise Only)**

- Open **Run** → type `gpedit.msc`
- Navigate to:  
  `Computer Configuration > Administrative Templates > Windows Components > Data Collection and Preview Builds`
- Double-click **Allow Telemetry** → Set to **Disabled**
