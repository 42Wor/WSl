# WSl
# Running WSL & Commands

These commands are executed from the Windows command line (CMD, PowerShell, Windows Terminal), *not* from within a WSL Linux shell.

## Basic WSL Usage

| Command                  | Description                                                                                                   | Example(s)                                                                                                  |
| ------------------------ | ------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `wsl` or `wsl.exe`       | Launches the default WSL distribution into its home directory.                                                | `wsl`                                                                                                       |
| `wsl [command]`           | Runs a specific Linux command in the default distribution without fully entering the interactive shell.       | `wsl ls -la` (Lists all files/directories, including hidden ones, in the current directory)                |
| `wsl ~`                   | Launches the default WSL distribution, ensuring you start in the Linux home directory (`~`).                 | `wsl ~`                                                                                                     |
| `wsl --exec <Command>` or `wsl -e <Command>` | Explicitly runs a command in the default distribution.  Useful for scripting.                                                                     | `wsl -e apt update` (Updates package lists in the default distribution)                                    |
| `wsl --distribution <DistroName>` or `wsl -d <DistroName>` | Launches the specified distribution.                                                                                             | `wsl -d Ubuntu-20.04` (Launches Ubuntu 20.04)                                                           |
| `wsl -d <DistroName> [command]` | Runs a command in a specific distribution.                                                                         | `wsl -d Debian -- uname -a` (Shows kernel information for the Debian distribution)                           |
| `wsl --user <UserName>` or `wsl -u <UserName>` | Runs WSL or a command as the specified Linux user (within WSL). Default is the user configured during initial setup. | `wsl -u root apt update` (Updates package lists as the root user)<br>`wsl -d Ubuntu -u myuser node myscript.js` (Runs a Node.js script as 'myuser' in the 'Ubuntu' distribution) |

## Managing Distributions

| Command                                  | Description                                                                                                                               | Example(s)                                                                                                 |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `wsl --list` or `wsl -l`                 | Lists all installed WSL distributions.                                                                                                    | `wsl -l`                                                                                                     |
| `wsl --list --online` or `wsl -l -o`       | Lists distributions available for installation from the Microsoft Store.                                                                | `wsl -l -o`                                                                                                    |
| `wsl --list --running` or `wsl -l --running` | Lists only the distributions that are currently running.                                                                                    | `wsl -l --running`                                                                                             |
| `wsl --list --verbose` or `wsl -l -v`     | Lists installed distributions with details like state (Running/Stopped), version (WSL 1 or WSL 2), and default status.                   | `wsl -l -v`                                                                                                    |
| `wsl --set-default <DistroName>` or `wsl -s <DistroName>` | Sets the specified distribution as the default one to launch when you just type `wsl`.                                           | `wsl -s Ubuntu-20.04` (Sets Ubuntu 20.04 as the default distribution)                                     |
| `wsl --set-version <DistroName> <Version>` | Converts a distribution between WSL 1 and WSL 2. `<Version>` must be either `1` or `2`.  Note: This can take a considerable amount of time. | `wsl --set-version Ubuntu-20.04 2` (Converts Ubuntu 20.04 to WSL 2)                                       |
| `wsl --unregister <DistroName>`           | **WARNING:** Completely removes a distribution and *all* its data. Use with extreme caution!  This cannot be easily undone.                     | `wsl --unregister LegacyDebian` (Removes the "LegacyDebian" distribution)                               |
| `wsl --install [-d <DistroName>]`         | Installs the default Ubuntu distribution (or prompts if no default is configured). Use `-d` to install a specific distro from the online list.  | `wsl --install` (Installs the default Ubuntu distribution)<br>`wsl --install -d Debian` (Installs Debian) |
| `wsl --export <DistroName> <FileName.tar>` | Exports a distribution's filesystem to a TAR archive file.  Useful for backups and transferring distributions.                        | `wsl --export Ubuntu D:\backups\ubuntu_backup.tar` (Exports the Ubuntu distribution to the specified TAR file) |
| `wsl --import <DistroName> <InstallLocation> <FileName.tar> [--version <1\|2>]` | Imports a distribution from a TAR file.  Specify a new distribution name, the installation location, the path to the TAR file, and optionally the WSL version. | `wsl --import MyUbuntu C:\wsl_vhds\MyUbuntu D:\backups\ubuntu_backup.tar --version 2` (Imports the TAR file as a new distribution named "MyUbuntu" using WSL version 2, installing it in the specified directory) |

## System Information & Control

| Command        | Description                                                                                               | Example(s) |
| -------------- | --------------------------------------------------------------------------------------------------------- | ---------- |
| `wsl --shutdown` | Immediately terminates all running WSL distributions and the WSL 2 lightweight utility VM.                 | `wsl --shutdown` |
| `wsl --update`   | Checks for and installs the latest WSL version (kernel, etc.). Requires administrator privileges. | `wsl --update`   |
| `wsl --status`   | Shows general WSL configuration information (default distro, kernel version, etc.). (Newer WSL versions). | `wsl --status`   |
| `wsl --version`  | Displays detailed version information about WSL components.                                               | `wsl --version`  |

## Advanced / Other

| Command                                                              | Description                                                                                                                                                           | Example(s)                                                                                                                                          |
| --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `wsl --mount <DiskPath> [--partition <Index>] [--type <FileSystem>]` | (WSL 2 only) Mounts a physical disk or VHD directly into WSL. Requires administrator privileges.                                                                     | `wsl --mount \\.\PHYSICALDRIVE1 --partition 2 --type ext4` (Mounts the second partition of the first physical drive as ext4)                       |
| `wsl --unmount [<DiskPath>]`                                          | (WSL 2 only) Unmounts a mounted disk. If no path is given, unmounts all mounted disks. Requires administrator privileges.                                               | `wsl --unmount \\.\PHYSICALDRIVE1` (Unmounts the specified drive)<br>`wsl --unmount` (Unmounts all mounted drives)                             |

## Getting Help

| Command      | Description                                                                                                                                                                                                   | Example(s) |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| `wsl --help` | Displays the built-in help message listing available commands and options. This is often the most up-to-date reference.  It will show command options specific to the version of WSL installed on your system. | `wsl --help` |

