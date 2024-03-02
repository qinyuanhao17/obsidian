---
date: 2024-03-02T15:58:00
---
- On your Desktop, right click and go to ``New->Shortcut``

- For the location you need to copy the following target

    - ` %windir%\System32\cmd.exe "/K" <path-to-activation-script> "<path-to-qudi-environment>"&& cd "<path-to-qudi-directory>" && python "start.py" `

    - In order for the shortcut to work on every windows setup, you need to specify 3 things :

        - `<path-to-activation-script>` : the path to the Anaconda activate.bat file, for example

        `C:\ProgramData\Miniconda3\Scripts\activate.bat`.

        - `<path-to-qudi-environment>` : this can be found using command `conda info --envs` in a terminal.

        - `<path-to-qudi-directory>` : the path where Qudi's `start.py` can be found.  

- Click ``Next``

- Give the name you want fot the shortcut : ``Qudi``

- Click ``Finish``

==Full example:==
```
%windir%\System32\cmd.exe "/K" E:\anaconda\Scripts\activate.bat "C:\Users\quantunlab2023\.conda\envs\odmr" && cd "C:\Users\quantunlab2023\.conda\envs\odmr\cw_odmr20240229" && python "control_panel.py"
```