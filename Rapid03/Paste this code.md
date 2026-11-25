I am preparing an older **HP Z400 workstation (Intel Xeon W3670, 16 GB RAM)** for research at York University's Electronic Machine Intelligence Lab (EMIL), under Professor Sebastian Magierowski.

**Current situation:**
- The computer previously ran Ubuntu 16.04 and Windows 7.
- Ubuntu 22.04 and 26.04 successfully booted from USB, but their installers froze during setup and disk detection.
- I have now successfully booted **Ubuntu 16.04.7 LTS from a USB drive** into the live desktop (`ubuntu@ubuntu`).
- The professor and EECS IT technician Nam Tran authorized erasing only the original 1 TB Seagate HDD to create a clean Ubuntu system.
- Two other drives contain existing Windows and laboratory data and **must not be modified**.
- The intended hostname is `rapido3`, and my username should be `abdul`.

**My objective:**

Help me safely prepare this workstation with a clean, usable Ubuntu installation, preferably a currently supported version. Ubuntu 16.04 is being used for compatibility testing, not yet approved as the permanent operating system.

**Important rules:**

1. Guide me step by step as a beginner.
2. Provide commands that I can copy and paste directly into Terminal.
3. Explain what each command does and whether it is read-only or destructive.
4. First identify all physical disks using their models, full serial numbers, sizes, and partitions.
5. Never erase, format, resize, or modify a disk without confirming it is the specifically authorized Seagate HDD.
6. Preserve the other two drives, their data, and their bootloaders.
7. Help me understand why newer Ubuntu installers freeze and identify a safe solution.
8. Do not recommend installing unsupported Ubuntu 16.04 permanently without EECS IT approval.
9. After successful installation, help me configure networking, SSH, Python, Git, VS Code, and basic research tools.
10. Help me collect hardware and software specifications for Professor Magierowski's laboratory inventory spreadsheet.

**Start from my current Ubuntu 16.04.7 live USB desktop. First help me identify the drives safely, then guide me through the next appropriate step. Do not assume the disk names remain consistent between boots.**
