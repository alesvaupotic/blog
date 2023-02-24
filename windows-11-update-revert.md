# Windows 11 Update Revert

# The problem

This morning my notebook started to recycle Windows Explorer after an update. Here is how it looked like:

https://user-images.githubusercontent.com/1660347/221130885-18595a77-0c61-4995-8678-edbc7590da3d.MOV

I was looking at this for like a minute an then realized I need to revert an update. 

# The Solution

After some research, I found out about `dism` command.

So, while my display was flickering, I instinctively pressed `Ctrl-Alt-Del` to get to the `Task Manager`. From there I clicked `Run new task`.

I entered `cmd` and clicked the checkbox below to run with Administrative privileges.

![image](https://user-images.githubusercontent.com/1660347/221132406-4804a6f2-693c-4285-959c-5303f968e15a.png)

Once I got the prompt, I switched to PowerShell by entering `powershell`, which I guess could be ommited. Anyway, from the PowerShell prompt, I entered 
```bash
dism /online /get-packages
```

I got back a list of installed updates and went on to remove the latest on the list with `/remove-package`:

![image](https://user-images.githubusercontent.com/1660347/221133311-a5f05b7f-e988-4956-82b5-0bdf541c79a5.png)

Fail! As you can see, it is the last listed, but not the last installed:

![image](https://user-images.githubusercontent.com/1660347/221133849-24a36da9-f75a-422a-b6fd-f06dd5e24381.png)

So, let's remove that one:

![image](https://user-images.githubusercontent.com/1660347/221133719-90457078-9b01-4458-abdd-c1f361e9eace.png)

**Success!**
After a few minutes, I got a prompt to restart the computer and it works as it should now.

PS: I disabled automatic Windows Update for a week to wait for the next KB.
