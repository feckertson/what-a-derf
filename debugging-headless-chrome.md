# Debugging Headless Chrome
From an OS prompt,  
`chrome --headless --disable-gpu --allow-chrome-scheme-url --remote-debugging-port=0 <URL>`  

In chrome, 
`chrome://inspect`  
Then click `Configure...` and add the `<ip_address>:<port value>` from the OS prompt.

Note that `--headless=new` is no longer a thing, but `--headless=true` (i.e., new) and `--headless=old` are acceptable. 