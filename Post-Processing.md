Extra Scripts:
For Windows user running Python scripts please Use:
<full_path_to_python_interpreter>\pythonw.exe <script_name>.py

Example: 
C:\Python27\pythonw.exe C:\Script\test.py

Use single back slashes, SickRage/Python will escape them and make them double.

Parameters that are passed:


sys.argv[0]: Filepath to Script
sys.argv[1]: Final full path to the episode file
sys.argv[2]: Original full path of the episode file
sys.argv[3]: Show indexer ID
sys.argv[4]: Season number
sys.argv[5]: Episode number
sys.argv[6]: Episode Air Date