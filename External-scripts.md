Due to security reasons, the execution of external scripts is restricted to Python scripts. This limitation can easily be overcome by using a Python script that acts as intermediary between Medusa and one or more non-Python scripts.

The Python script in that case should look like this:
```
import subprocess
import sys

subprocess.call(['my_cmd', 'my_script'] + sys.argv[1:])
# If you need to run more scripts (optional)
# subprocess.call(['my_cmd2', 'my_script2'] + sys.argv[1:])
```

Replace `my_cmd` and `my_script` and save the code as `script.py` (or the name you prefer).
Now you can use that file as external script within Medusa to run the non-Python scripts.