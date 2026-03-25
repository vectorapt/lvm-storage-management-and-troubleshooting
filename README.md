# 💾 LVM Disk Management & Troubleshooting Project

## Overview
This project demonstrates the design, configuration, and management of Linux storage using Logical Volume Manager (LVM), along with practical troubleshooting of common real-world storage issues.

---

## 🧠 Objectives
- Configure LVM using a dedicated disk  
- Create and manage Physical Volumes (PV), Volume Groups (VG), and Logical Volumes (LV)  
- Implement swap using LVM  
- Demonstrate dynamic resizing of storage  
- Create and manage LVM snapshots  
- Simulate and troubleshoot common storage issues  

---

## ⚙️ Environment
- OS: RHEL 9  
- Disk: 10GB (dedicated for LVM setup)  
- Shell: Bash  

---

## 🧱 Architecture
A 10GB disk was partitioned and initialized for LVM. A Volume Group was created from the Physical Volume, and Logical Volumes were allocated for data and swap. Free space was intentionally retained within the Volume Group to enable dynamic resizing and snapshot creation.

Final structure:
- Data Logical Volume: Initially 4GB, later extended to 5GB  
- Swap Logical Volume: 1GB  
- Snapshot Volume: Created using copy-on-write mechanism  
- Remaining space reserved within the Volume Group for scalability  

---

## ⚙️ Implementation Summary
The setup begins with preparing a dedicated disk and assigning it for LVM usage. A Physical Volume is initialized and grouped into a Volume Group, which acts as a flexible storage pool.

Logical Volumes are created for data storage and swap. A filesystem is configured and mounted for data access, while swap space is activated using a logical volume.

The data volume is later extended dynamically without downtime, demonstrating LVM scalability. A snapshot is also created to showcase backup and recovery concepts using copy-on-write.

---

## 💣 Fault Simulation & Troubleshooting

Two common real-world issues were simulated and resolved:

- **Logical Volume extended without resizing the filesystem:**  
  This resulted in a mismatch between the logical volume size and the usable filesystem space. The issue highlighted the separation between LVM and filesystem layers and was resolved by resizing the filesystem accordingly.

- **Incorrect filesystem table configuration:**  
  An invalid configuration prevented proper mounting. The issue was identified through validation checks and resolved by correcting the configuration before system reboot.

Preventive measures were also implemented to ensure such issues can be avoided in real-world scenarios.

---

## 🔥 Key Learnings
- LVM and filesystem layers operate independently and must be managed separately  
- Retaining free space within a Volume Group is critical for flexibility and scalability  
- Logical volumes can be extended dynamically without affecting mount configuration  
- Snapshots use a copy-on-write mechanism and are space-dependent  
- Proper validation of system configurations prevents critical failures  
- Troubleshooting storage issues requires understanding of both structure and behavior  

---

## ⚔️ Conclusion
This project demonstrates both the implementation and troubleshooting of LVM-based storage systems, reflecting real-world system administration practices focused on flexibility, scalability, and reliability.
