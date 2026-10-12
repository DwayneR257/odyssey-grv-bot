# 🤖 Odyssey Automated GRV Bot

An intelligent, automated desktop integration tool designed to process supplier invoice PDFs, match stock and departments locally, create missing records, and seamlessly inject Goods Received Vouchers (GRVs) directly into **Odyssey (Version 11)** using Gemini AI and Windows UI automation.

---

## 🌟 What the Bot Does

* 📁 **Folder Monitoring:** Continuously watches an `Incoming_PDFs` folder in the background for new supplier invoice PDFs.
* 🧠 **AI-Powered Extraction:** Utilizes the Google Gemini API to accurately extract supplier details, invoice reference numbers, and line items (descriptions, quantities, and unit costs).
* 🔍 **Smart Local Matching:** 
  * Matches incoming items against local `stock.csv` databases using exact, substring, and keyword-overlap logic.
  * Automatically assigns **Major** and **Sub** department codes by scanning `Major Dept.csv` and `Sub Dept.csv`.
* ⚡ **ERP UI Automation:** Automatically navigates Odyssey ERP to:
  * Create missing suppliers on the fly if they don't exist.
  * Batch-create new stock items with proper department codes, costs, and selling prices.
  * Inject final GRV line items and execute processing.
* 🔄 **Auto-Updater Integration:** Automatically checks your GitHub repository on startup for newer versions, downloads updates safely, and restarts itself seamlessly.

---

## 📂 Folder Structure

The bot expects the following local directory structure on `C:\Odysseybot2`:

```text
C:\Odysseybot2\
│
├── jarvis_grv_gemini.exe      # Main compiled automation bot
├── run_bot.vbs                # Silent background VBS launcher
├── Incoming_PDFs\             # Drop raw PDF invoices here
├── Processed\                 # Successfully processed or failed PDFs
├── Logs\                      # Daily runtime and error logs
├── Config\
│   ├── stock.csv              # Master stock database
│   └── suppliers.csv          # Master supplier database
└── Departments\
    ├── Major Dept.csv         # Major department mappings
    └── Sub Dept.csv           # Sub department mappings
```
## ⌨️ Odyssey GRV Shortcut Keys Reference

The automation script utilizes and interacts with these core shortcut mappings inside Odyssey ERP:

* **Stock Items:** `Ctrl + I`
* **Goods Receiving:** `Ctrl + G`
* **Create new GRV:** `Ctrl + C`
* **New stock inside GRV:** `Ctrl + N`
* **New supplier:** `Ctrl + U`
* **Process GRV:** `Ctrl + V`

---

## 🚀 Moving / Installing on a New PC

To move your automation program to a new PC, copy your program files, set up the required environment, and make sure your folder paths and ERP software match. Follow these steps to set it up smoothly:

### Step 1: Copy Your `C:\Odysseybot2` Folder
1. On your old PC, go to your `C:\` drive and copy the entire `Odysseybot2` folder.
2. Transfer it to the `C:\` drive of the new PC so it sits at the exact same location: `C:\Odysseybot2`.
3. This ensures your `Config\stock.csv`, suppliers, department CSVs, and folder structure (`Incoming_PDFs`, `Processed`, etc.) are fully preserved.

> **Note:** Alternatively, to create the folder structure from scratch on a new machine, open Command Prompt (`cmd`) and run:
> ```cmd
> mkdir C:\Odysseybot2
> mkdir C:\Odysseybot2\Incoming_PDFs
> mkdir C:\Odysseybot2\Processed\Success
> mkdir C:\Odysseybot2\Processed\Failed
> mkdir C:\Odysseybot2\Logs
> mkdir C:\Odysseybot2\Config
> mkdir C:\Odysseybot2\Departments
> ```

### Step 2: Download and Place the Latest `.exe`
1. Download the latest compiled `jarvis_grv_gemini.exe` release from the **Releases** tab on GitHub.
2. Place it directly inside `C:\Odysseybot2\`.

### Step 3: Ensure Odyssey is Ready
1. Ensure your Odyssey software (**Odyssey Ultimate Version 11**) is installed and functioning on the new PC.
2. Confirm the main application window title matches what the script looks for (`Odyssey Ultimate Version 11`).

### Step 4: Run and Test
1. Go to `C:\Odysseybot2` on the new PC.
2. Double-click your `run_bot.vbs` file to launch the bot silently in the background.
3. Drop a test PDF into `C:\Odysseybot2\Incoming_PDFs` to confirm it watches the folder, processes successfully, and moves it to `Processed\Success`!

---

## 🛠️ How to Use

1. Ensure Odyssey is open and logged in.
2. Launch `run_bot.vbs` from `C:\Odysseybot2\`.
3. Drop any valid supplier invoice PDF into `C:\Odysseybot2\Incoming_PDFs\`.
4. The bot will parse the document, create missing records if necessary, populate the GRV fields, and process the voucher automatically.
