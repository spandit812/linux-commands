
---
To get particular value from the output of the another command

Example:


<img width="409" height="57" alt="image" src="https://github.com/user-attachments/assets/859fdc17-0cd0-445e-a110-43e00498d600" />


kubectl describe service mydep2 | grep IP: | **awk** **'{print $2}'**

<img width="489" height="56" alt="image" src="https://github.com/user-attachments/assets/05f16a77-c733-4a6d-8752-0d32e09cd729" />
