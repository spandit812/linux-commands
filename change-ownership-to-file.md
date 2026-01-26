chown (change owner)  
**chown = WHO**  
**chmod = WHAT**  

```bash
sudo chown labuser:labuser dev-user.key
sudo chown labuser:labuser dev-user.crt
```

labuser:labuser  --> user:group  

Owner user → labuser  
Owner group → labuser  


1️⃣ What is rw-r--r--?

This is the symbolic (text) representation of file permissions.

It is always 9 characters, grouped into 3 sets:  

rw- r-- r--  
│   │   │
│   │   └── Others  
│   └────── Group  
└────────── Owner  

2️⃣ Meaning of each letter  
Symbol	Meaning  
r	read  
w	write  
x	execute  
-	permission NOT given  
So:  
rw-  
= read + write  
r--  
= read only  
3️⃣ Convert rw-r--r-- → numbers (THIS is the bridge)  
Each permission has a number value:  
Permission	Value  
r	4  
w	2  
x	1  
Now calculate per group.  
Owner: rw-  
r (4) + w (2) + - (0) = 6  
Group: r--  
r (4) + - (0) + - (0) = 4  
Others: r--  
r (4) + - (0) + - (0) = 4  
✅ Final numeric form  
rw-r--r--  →  644  
4️⃣ So when you run:  
chmod 644 file.txt  
Linux internally sets:  
rw-r--r--  
And when you run:  
ls -l file.txt  
You SEE:  
rw-r--r--  
💡 Same thing. Different notation.  
5️⃣ More examples (very important)  
chmod 600 file  
rw-------   
Only owner can read/write  
chmod 755 script.sh  
rwxr-xr-x  
Owner can do everything, others can execute  
chmod 777 file ⚠️  
rwxrwxrwx  
Everyone can do everything (usually bad)  

6️⃣ Why Linux shows rw-r--r-- instead of 644?  
Because it’s human-readable.  
Seeing:  
rw-r--r--  
You instantly know:  
Owner can write  
Others can only read  
Seeing:  
644  
You must calculate mentally.  
7️⃣ Quick memory trick 🧠  
r = 4  
w = 2  
x = 1  

**One small extra tip (good habit)**  
When you see permissions, always read them as:  
OWNER | GROUP | OTHERS  
Left → Right  

Just add them.  

---

**rw-r--r-- = 644 in this owner has read and write but group does have write permission then ultimately user would not be able to write the thing to file. Am I correct?**  

Who actually writes to a file?  
Linux checks permissions in this order:  
Is the user the OWNER? → use owner permissions  
Else, is the user in the GROUP? → use group permissions  
Else → use others permissions  
🚨 Linux does NOT combine permissions  
It stops at the first match.  

2️⃣ Apply this rule to rw-r--r-- (644)  
rw-   r--   r--  
│     │     │  
Owner Group Others  
Case 1: You are the owner  
Owner permissions apply  
rw- → ✅ you CAN write  
➡️ Group permissions are ignored  
Case 2: You are not the owner, but in the group  
Group permissions apply  
r-- → ❌ you CANNOT write  
Case 3: You are neither owner nor in group  
Others permissions apply  
r-- → ❌ you CANNOT write  
3️⃣ Important rule to remember 🧠  


Only ONE permission set applies — never all three.

---
**chmod u+w vs chmod g+w**  

1️⃣ What do u and g mean?  
Symbol	Means  
u	user (owner)  
g	group  
o	others  
a	all (u + g + o)  
2️⃣ What does +w mean?  
Symbol	Action  
+	add permission  
-	remove permission  
=	set exactly  
Permission	Meaning  
r	read  
w	write  
x	execute  
3️⃣ chmod u+w (Owner gets write)  
Command  
chmod u+w file.txt  
Meaning  
“Add write permission to the owner of the file.”  
Example  
Before:  
r--r--r--  
After:  
rw-r--r--  
✔ Owner can now write  
❌ Group unchanged  
❌ Others unchanged  
4️⃣ chmod g+w (Group gets write)  
Command  
chmod g+w file.txt  
Meaning  
“Add write permission to the group of the file.”  
Example  
Before:  
rw-r--r--  
After:  
rw-rw-r--  
✔ Group members can write  
✔ Owner unchanged  
❌ Others unchanged  
5️⃣ Side-by-side comparison  
Command	Who gets write?	Result example  
chmod u+w	Owner	rw-r--r--  
chmod g+w	Group	rw-rw-r--  
6️⃣ Why symbolic chmod is powerful  
Instead of:  
chmod 664 file.txt  
You can safely do:  
chmod g+w file.txt  
✔ No need to calculate numbers  
✔ No risk of accidentally changing others’ permissions  
7️⃣ Common real-world examples    
Remove write from group 
chmod g-w file.txt  
Add execute to owner  
chmod u+x script.sh  
Make script executable by everyone  
chmod a+x script.sh  
8️⃣ Kubernetes / DevOps relevance  
Private keys  
chmod u+rw,go-rwx dev-user.key  
Scripts in CI/CD  
chmod u+x deploy.sh  
