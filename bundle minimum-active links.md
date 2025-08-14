## 🔗 bundle minimum-active links – Cisco

### 📌 Purpose
The `bundle minimum-active links` command sets the **minimum number of active links** required before a **bundle** (EtherChannel / Port-Channel) can be brought up or remain operational.

---

### 📖 Context
- Used in **link bundling** (aggregating multiple physical links into one logical link).  
- Purpose:
  - **Increase bandwidth** by combining multiple links.  
  - **Improve reliability** through redundancy.  
- Optional command — can be used to implement **1:1 link protection**.

---

### ⚙ How 1:1 Link Protection Works
- Highest-priority link → **Active**.  
- Second-highest-priority link → **Hot-Standby**.  
- If the active link fails, the standby link takes over.

---

### 🛠 Command Syntax
```plaintext
bundle minimum-active links <number>

<number> = Minimum active links required.

Range: 1 to 32.
