# Data Transmission Project

## 1. Project Overview

This project implements a simple socket connection between a client and a server. It provides basic shell commands that allow clients to navigate the host PC, including the ability to transfer files from the server to the client.

## 2. Dependencies

This project relies on the following libraries and tools:

- [CMake](https://cmake.org/) (version 3.12 or higher) for the build system.
- [SQLite3](https://www.sqlite.org/) for users' database handling.
- [Winsock Library](https://docs.microsoft.com/en-us/windows/win32/winsock/windows-sockets-start-page-2) (`Ws2_32.lib`) for TCP/IP networking.
- A C++ Compiler with support for C++23 standard.

## 3. Full Unix Commands and Extensions implemented

### 3.1 Unix Commands

| Command | Description                                                | Example Usage                  |
|---------|------------------------------------------------------------|--------------------------------|
| `ls`    | Lists all files and directories in the current directory.  | `ls /path/to/directory`        |
| `cd`    | Changes the current directory to the specified one.        | `cd /path/to/directory`        |
| `pwd`   | Prints the absolute path of the current working directory. | `pwd`                          |
| `cat`   | Concatenates and displays the contents of files.           | `cat my_file.txt`              |
| `echo`  | Outputs the input string.                                  | `echo Hello, World!`           |
| `mkdir` | Creates a new directory.                                   | `mkdir new_directory`          |
| `rmdir` | Removes a directory if it is empty.                        | `rmdir /path/to/directory`     |
| `rm`    | Removes files or directories.                              | `rm my_file.txt`               |
| `touch` | Creates a new empty file.                                  | `touch new_file.txt`           |
| `mv`    | Moves or renames files or directories.                     | `mv old_name.txt new_name.txt` |
| `cp`    | Copies files or directories.                               | `cp source_file target_file`   |
| `find`  | Searches for files in a directory hierarchy.               | `find . -name my_file.txt`     |
| `grep`  | Searches text using patterns.                              | `grep "my pattern" file.txt`   |
| `exit`  | Exits the shell.                                           | `exit`                         |

### 3.2 Extension Commands

| Command          | Description                                           | Example Usage        |
|------------------|-------------------------------------------------------|----------------------|
| `copy_to`        | Copies a file to the client's PC.                     | `copy_to file.txt`   |
| `copy_from`      | Copies a file from the client's PC to the server.     | `copy_from file.txt` |
| `move_startup`   | Runs the host executable on startup.                  | `move_startup`       |
| `remove_startup` | Cancels the `move_startup` command.                   | `remove_startup`     |
| `check_startup`  | Checks whether the executable file starts on startup. | `check_startup`      |
| `run`            | Runs executables and .bat scripts.                    | `run script.bat`     |

## 4. Usage

Both the server (`Server.exe`) and the client (`Client.exe`) interact over a TCP socket connection. Once the connection is established, the client runs a basic shell, facilitating communication between both ends.

### 4.1 Server Usage: `Server.exe`

Here's how you can call `Server.exe` with several command-line flags:
```shell
.\HostExec.exe -p PORT -n NAME PASSWORD -r NAME --set-startup
```

Read more about these flags [here](FLAGS_FOR_SERVER).

### 4.2 Client Usage: `CLient.exe`

`CLient.exe` can be called similarly, but with different flags:
```shell
.\CLient.exe -s SERVER_IP -p PORT -u USERNAME -w PASSWORD
```

Read more about these flags [here](FLAGS_FOR_CLIENT).

## 5. Installation & Setup

To set up this project on your machine, follow the steps outlined below:

### 5.1 Clone the repository

Clone the repository onto your local machine using the following command in your command line:
```shell
git clone https://github.com/Shu-AFK/Datatransmission.git
```

### 5.2 Navigate to the project directory

Using the command line, navigate into the newly created project directory:
```shell
cd Datatransmission
```

### 5.3 Build the project 

Next, you'll need to build the project. You can do this by running the provided `build.bat` script. In the command prompt, execute the script like this: (make sure the folder with the sqlite3 .dll is in your PATH)
```shell
.\build.bat "C:\path\to\SQLite"
```

The batch script will create a `build` directory if one doesn't exist, configure the project using CMake with the provided SQLite path, and then build the project in release mode.

### 5.4 Run the project

After building the project, you can run the server and client applications. These applications are `Server.exe` and `Client.exe`, with the flags specified earlier.

## 6. Contributing

We welcome all contributions! Please read our [CONTRIBUTING.md](CONTRIBUTE.md) for detailed information on how you can contribute.

## 7. License

This project is distributed under the MIT License. See our [LICENSE](LICENSE.txt) for more details.