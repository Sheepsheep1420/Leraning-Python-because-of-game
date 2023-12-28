```py

import win32gui
from win32process import GetWindowThreadProcessId

pid = 15424


def callback(hwnd, hwnds):
    if all([GetWindowThreadProcessId(hwnd)[1] == pid, win32gui.IsWindowVisible(hwnd)]):
       print(win32gui.GetWindowText(hwnd), hwnd)
       hwnds.append(hwnd)
    return True


hwnd_list = []
win32gui.EnumWindows(callback, hwnd_list)
hwnd = hwnd_list[0]

```
