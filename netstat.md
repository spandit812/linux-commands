<pre>
netstat -putan | grep '8080'
tcp6       0      0 :::8000                 :::*                    LISTEN      <b>825434</b>/PM2 v5.4.2:

825434 --> This is process ID

-p: Show the PID and program name using each socket.​

-u: Include UDP sockets.​

-t: Include TCP sockets.​

-a: Show all sockets (both listening and non-listening/established).​

-n: Disable name resolution and show numeric IPs and ports (faster, avoids DNS lookups).
</pre>
