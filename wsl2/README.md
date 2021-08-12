# WSL2

Do you have a windows machine but like softwarer development on a mac? Once you have completed the below steps you should
be able to do most things mac user can, including homebrew and bash scripting.

## Installing WLS2
[Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

## Docker
Docker support is much better in WSL2. You can install docker for windows, and it has native support for WSL2 in the settings.
This means that all the usual `docker` commands work in the terminal.

[Using Docker in WSL 2 and VS Code](https://code.visualstudio.com/blogs/2020/03/02/docker-in-wsl2)

## Terminal
The normal WSL2 Ubuntu command line isn't very good because it doesn't support multiple tabs. You'll want to install Windows Terminal.
[Install and set up Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/get-started).

## Accessing windows directories from terminal
By default, your windows files are located at `/mnt/<drive_letter>`. So, your C: drive is at `/mnt/c`.

## Localhost forwarding
By default, starting up server / docker might not work very well because, while the containers and apps will start in the shell,
you may not be able to access them. For example, you might start a django app, and it will run successfully, but you won't
be able to hit it on http://localhost:8000/admin. This is because WSL2 is actually running a virtual machine and the app is running
on localhost on the machine itself. There are way to get around this by pointing to the specific IP of the machine on the windows side,
but by far the easier way around this is to make sure that localhost forwarding is turned on.

1. Go to `C:\Users\<YOUR_USER>` on windows
2. Creaet a file called `.wslconfig`
3. Add the following to the file: 

```
[wsl2]
localhostForwarding=true
```

4. Save, and restart the WLS2 machine. You can do this by starting up a command prompt or a powershell terminal and running `wsl --shutdown`
5. Start up a new shell to get the WSL2 vm running again

## Additional Links
[Docker Desktop WSL 2 backend](https://docs.docker.com/docker-for-windows/wsl/)

## Unsupported unix/mac functionality
- Brew services

## TODOs
- Different shells like zsh?
- `open` for something like `open file.html` so it opens in your browser does not seem to work on a mounted windows drive.
If you run `open /mnt/c/file.html`, it asks your browser to open that exact file path, but of course windows can't find that
because it should be `C:/file.html`. No solution found yet.