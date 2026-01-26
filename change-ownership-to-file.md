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


Just add them.
