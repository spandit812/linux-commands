---
<pre>
<b>Principal entrypoint of linux machine:</b>
strings /proc/1/cmdline

  This you can consider as a container

  process/1/cgroup
  process/125/cgroup

  In the linux all processes run in the same global container called /
  If I run <b>top</b>, it shows all processes running in the machine. but all proceses run the common container, /
  For the purpose of security, docker gives you feature to run applications in different container.

  <img width="686" height="80" alt="image" src="https://github.com/user-attachments/assets/e4e21d78-d618-4e09-be1a-044c8d60d0a8" />

  <img width="279" height="183" alt="image" src="https://github.com/user-attachments/assets/b42dc155-2e2b-4716-a045-ae427dc9deee" />
  <img width="698" height="333" alt="image" src="https://github.com/user-attachments/assets/9c6eda85-fcd7-4000-8ca7-d8a4761f715d" />

<img width="772" height="325" alt="image" src="https://github.com/user-attachments/assets/4a916e25-1a0c-4be5-87aa-772649aa543b" />

  <b>To see all the processes running in the global container</b>
  <img width="772" height="325" alt="image" src="https://github.com/user-attachments/assets/df2f2b1d-ce68-49bb-be0f-9ebcf9ab3ddc" />
  Ths gives global processes: ls /proc/
  This gives only processes running in the container: 
  docker exec registry ls /proc/
</pre>
