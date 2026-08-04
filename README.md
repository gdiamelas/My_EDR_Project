# 🛡️ Windows EDR Agent Simulator (v8.1)

A lightweight Endpoint Detection & Response (EDR) agent simulator written in C for Windows systems. This project demonstrates low-level process auditing using the Win32 API and dynamic threat intelligence signature loading.

---

## 🤖 AI Generation & Educational Disclaimer
> **Notice:** This project was developed as an educational Proof-of-Concept (PoC) with the assistance of **Artificial Intelligence (AI)** to explore Windows Internal APIs, memory process management, and endpoint security concepts.

---

## ⚙️ Core Features

- **Dynamic Threat Intelligence:** Parses malware process signatures dynamically from an external file (`blacklist.txt`)[cite: 1, 2, 3].
- **Dual Execution Modes:**
  - `edr_audit.c`: Passive Audit Mode (100% Safe, flags threats without process termination)[cite: 3].
  - `edr_agent.c`: Active Response Mode (Detect & Terminate using Win32 API)[cite: 2].
- **Win32 API Integration:** Uses `CreateToolhelp32Snapshot`, `Process32First`, and `Process32Next` to inspect process memory[cite: 2, 3].
- **Case-Insensitive Matching:** Uses `_stricmp` to catch process obfuscation (e.g., `mImIkAtZ.eXe`)[cite: 2, 3].

---

## 📁 Project Structure

- `edr_audit.c` - Source code for Passive Audit Mode (Safe execution)[cite: 3].
- `edr_agent.c` - Source code for Active Kill Mode (Requires Admin privileges)[cite: 2].
- `blacklist.txt` - Threat intelligence signature list[cite: 1].
- `README.md` - Project documentation.

---

## 🚀 How to Run

### 1. Compilation
Compile using GCC or any standard C compiler on Windows:

```bash
# Compile Passive Audit Mode (Recommended)
gcc edr_audit.c -o edr_audit.exe

# Compile Active Response Mode
gcc edr_agent.c -o edr_agent.exe
