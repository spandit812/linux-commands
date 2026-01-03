<pre>
<b>1. To write text into single or multiple files:</b>
      echo welcome | tee abc.txt def.txt
<b>2. To write output of the command:</b>
      whoami | tee login
<b>3. To write multiple lines usig EOF into a file :</b>
      tee exaple.txt 0<< EOF
                  THIS IS FIRST LINE
                  THIS IS SECOND LINE
            EOF

</pre>
