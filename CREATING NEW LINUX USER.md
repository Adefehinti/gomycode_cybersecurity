 # **Project: Secure Administrative User Provisioning in Kali Linux**
## Overview
This project demonstrates the secure creation of a Linux user with elevated privileges (Sudo access). Instead of using the high-risk "Root" account for daily operations, I established a secondary administrative account. This practice is a cornerstone of System Hardening and secure server management.

## Objective
The goal was to create a functional, secure administrative environment by:

Provisioning a new user with a dedicated home directory.

Granting Sudo (SuperUser Do) permissions safely.

Testing the "Sudoers" configuration to ensure administrative commands work without logging in as Root.

## Tools Used
Kali Linux: The operating system environment.

Terminal (Zsh): Used for command-line execution.

Sudo Utility: The system tool used to delegate administrative authority.

## Steps Taken
Identity Creation: Used sudo adduser Yimika to create the account. This automatically set up the group, home directory, and shell.

Password Hardening: Assigned a complex password. I ensured the password met "Best Practice" standards (mix of symbols, numbers, and cases).

Granting Sudo Access: Executed sudo usermod -aG sudo Yimika

Note: The -aG flag is critical—it Appends the user to the Group without removing them from their existing groups.

Permission Validation: Switched to the new user and attempted to run sudo apt update. Successfully running this command proved the user had administrative power.





**verification and testing**


To ensure the lab was successful, I performed the following tests

1.Identification Verification: Switched to the new account and confirmed identity using whoami

2.Priviledge Escalation Test:Executed sudo whoami.The system correctly prompted for a password and returned Root, confirming that the sudoers configuration was active

3. Administative Functional test:Successfully ran sudo apt update, proving the account can perform system maintenance with needing root permission.

**Screenshots**



<img width="655" height="465" alt="Screenshot 2026-02-13 115044" src="https://github.com/user-attachments/assets/5b6ddeeb-cb54-473f-a4a7-60aa83a02898" />




<img width="658" height="476" alt="Screenshot 2026-02-13 115515" src="https://github.com/user-attachments/assets/9454282f-726a-4bf3-8ae4-22870c0429f4" />





<img width="649" height="495" alt="Screenshot 2026-02-13 120920" src="https://github.com/user-attachments/assets/91f1e797-1c3b-4bd6-8d28-ab6fde9b06e1" />




<img width="665" height="555" alt="Screenshot 2026-02-13 121551" src="https://github.com/user-attachments/assets/002ed40e-416b-47e2-81cf-e09045ae1217" />





<img width="653" height="505" alt="Screenshot 2026-02-13 123127" src="https://github.com/user-attachments/assets/fde38ddc-07be-44c0-b383-0930b78a489f" />



"Troubleshooting & Problem Solving," 

"Challenge: During the user creation phase, the new user Yimika initially lacked administrative permissions, resulting in a 'not in sudoers file' error.

Solution: I successfully resolved this by switching to the root environment and using the usermod utility to append the user to the %sudo group. This reinforced my understanding of Linux group-based access control (RBAC)."







## Security Implications
The "Root" Risk: Using the Root account directly is dangerous; one wrong command can delete the entire OS. Using a Sudo user provides a "safety break" because you must intentionally type sudo before dangerous actions.

Accountability: In a corporate environment, if five people share the "Root" password, you don't know who deleted a file. If five people have their own Sudo accounts, the logs show exactly who did what.

Principle of Least Privilege: Even though this user has Sudo access, they still operate as a "normal" user for 99% of their tasks, reducing the risk of accidental system damage.

## Key Takeaways
Efficiency vs. Security: I learned how to balance the need for speed (Sudo access) with the need for security (individual accounts).

Linux Groups: I gained a deep understanding of how Linux uses "Groups" to manage permissions across the entire system.

System Hardening: Creating a non-root admin is the very first step I would take when setting up a new server for an employer.
