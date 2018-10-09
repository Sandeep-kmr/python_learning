# python_learning
#python script to connect to remote system and do some operations. In this case i have two example. One mapping the network drive to local system and secon connect and copy file from local system to remote system.

#mapping network drive to local system.
import win32netcon, win32wnet
username="USERNAME"
password="PASSWORD"
win32wnet.WNetAddConnection2(win32netcon.RESOURCETYPE_DISK, "Z:", "\\\\SERVER\\SHAREFOLDER", None, username, password)
win32wnet.WNetCancelConnection2("\\\\SERVER\\SHAREFOLDER", 0, 0)

#copy file from local system to remote system

import win32netcon, win32wnet
import shutil
username="USERNAME"
password="PASSWORD"
win32wnet.WNetAddConnection2(0, None, "\\\\SERVER\\SHAREFOLDER", None, username, password)
shutil.copy("C:\\Users\\Sandeep\\testing.txt", "\\\\SERVER\\SHAREFOLDER")
win32wnet.WNetCancelConnection2("\\\\SERVER\\SHAREFOLDER", 0, 0)
