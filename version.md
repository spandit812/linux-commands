---
lsb_release -a 
cat /etc/os-release

Check the linux standard base (LSB) linux distribution version.

---
**save below lines in lsb.sh**

#!/bin/bash

if [ "$(lsb_release -is)" = "Ubuntu" ]; then

  echo "Ubuntu detected"

fi

**run it by:**
./lsb.sh

---
