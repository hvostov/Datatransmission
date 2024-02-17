# Data transmission

## Description
This project implements a simple socket connection between a client and a server. As the client you can 
use basic shell commands to traverse the host pc, even transferring files from the server to the client.

## Dependencies

This project depends on the following libraries and tools:

- [CMake](https://cmake.org/) (version 3.12 or higher) as a build system.
- [SQLite3](https://www.sqlite.org/) as a database engine for managing users.
- [Winsock Library](https://docs.microsoft.com/en-us/windows/win32/winsock/windows-sockets-start-page-2) (`Ws2_32.lib`) for TCP/IP networking.
- C++ Compiler with support for C++23 standard.

## Unix( + extra) Command Descriptions

Below are descriptions of several commonly-used Unix commands:

- `ls`: This command lists all files and directories in the current directory. Example usage: `ls` or to list the files and directories in some other directory: `ls /path/to/directory`.

- `cd`: This command changes the current directory to the one specified. Example usage: `cd /path/to/directory`.

- `pwd`: This command prints the working directory, i.e., the directory you are currently within. Example usage: `pwd`.

- `cat`: This command concatenates and displays the content of files. Example usage: `cat my_file.txt`.

- `echo`: This command outputs the inputs. Example usage: `echo Hello, World!`.

- `mkdir`: This command creates a new directory. Example usage: `mkdir new_directory`.

- `rmdir`: This command removes a directory. However, it only removes empty directories. Example usage: `rmdir /path/to/directory`.

- `rm`: This command removes files or directories. Example usage: `rm my_file.txt`.

- `touch`: This command creates an empty file. Example usage: `touch new_file.txt`.

- `mv`: This command moves or renames files or directories. Example usage: `mv old_name.txt new_name.txt` or `mv file /path/to/new/location`.

- `cp`: This command copies files or directories. Example usage: `cp source_file target_file`.

- `find`: This command searches for files in a directory hierarchy. Example usage: `find . -name my_file.txt`.

- `grep`: This command searches text using patterns. Example usage: `grep "my pattern" file.txt`.

- `exit`: This command exits the shell. Simply type `exit` and hit enter.

- `copy_to`: This command copies a file to the client's PC. Example usage: `copy_to file.txt`.

- `copy_from`: this command copies a file from the client's PC to the server. Example usage: `copy_from file.txt`.

- `move_startup`: This command runs the host executable on startup. Usage: `move_startup`.

- `remove_startup`: This command reverts the previous command. Usage: `remove_startup`.

- `check_startup`: This command checks if the exe file gets started on startup. Usage: `check_startup`.

- `run`: This command runs executables and .bat scripts. Usage: `run script.bat`.

## How it works:

The server (`HostExec.exe`) and the client engage in a Tcp socket connection. Once the connection is established, a basic shell is started on the client PC, allowing for communication between the client and the server.

`HostExec.exe` can be called with the following command-line flags:

- `-p PORT` – specifies the port number for the server to listen on. Replace "PORT" with your desired port number. If this flag is not provided, the application will use a default port.
- `-n NAME PASSWORD` – adds a user with the given "NAME" and "PASSWORD". This allows the server to handle multiple users with different credentials.
- `-r NAME` – removes a user with the specified "NAME". This can be used to withdraw access from a specific user.
- `-h` – prints the usage message, listing these flags and explaining how to use them.
- `--set-startup` - Set the executable to start on boot.

For example, to start the server on port 9000, add a user named "john" with the password "password", and remove a user named "mary" while adding the executable to the startup, you would use the following command:
```bash 
  .\HostExec.exe -p 9000 -n john password -r mary --set-startup
```

`ReceiverExec.exe` can be called with the following command-line flags:

- `-s SERVER_IP` – specifies the IP of the server to connect to. Replace "SERVER_IP" with the actual IP address of your server.
- `-p PORT` – specifies the port number to connect to on the server. Replace "PORT" with the desired port number.
- `-u USERNAME` – specifies the username to use when connecting to the server. Replace "USERNAME" with the registered username on the server.
- `-w PASSWORD` – specifies the password to use when connecting to the server. Replace "PASSWORD" with the corresponding password registered for the username on the server.
- `-h` – prints the usage message, listing these flags and explaining how to use them.

For example, to connect to a server with IP address `192.168.0.10` on port `9000` using the username "john" and the password "password", you would use the following command:
```bash
  .\ReceiverExec.exe -s 192.168.0.10 -p 9000 -u john -w password
```

## Installation: 

Follow the steps below to install the project:

1. **Clone the Repository**

    First, clone the repository to your local machine using git:
   ```bash
    git clone https://github.com/Shu-AFK/Datatransmission
   ```

2. **Navigate to the project directory**

   Go to the project directory via the command line:

    ```bash
    cd Datatransmission
    ```
   
3. **Make the project**

   The project uses CMake as its build system, you can download it as follows:
   - Open a web browser and navigate to the official CMake download page: https://cmake.org/download/
   - Under "Current Release", find the "Binary distributions" section.
   - Download the Windows win64-x64 Installer, or Windows x86 installer for 32-bit Windows.
   - After the download is complete, you can install CMake by running the installer and following the prompts.
   - During installation, you will be asked whether to add CMake to the system PATH. It's recommended to do so to be able to run CMake from the command line from anywhere.

   Now you can build the project as follows:

    ```bash
    mkdir build && cd build
    cmake -G "MinGW Makefiles" ..
    make
    ```
   
   or by simply running:
   ```bash
      .\build.bat
   ```
   
4. **Move the files**

    Building the project results in two executable files.
     - Move the HostExec.exe file to the PC you want to access.
     - Move the ReceiverExec.exe file to the PC you want to excess the Host PC from.

5. **Run both files**

    Lastly you can run the HostExec.exe file using (please make sure to run with admin privileges):
    For Optional and non-optional flags please [Jump to How It Works](#how-it-works)

    ```bash
    .\HostExec.exe 
   ```
   
    Now you can run the ReceiverExec.exe file using:
    
    ```bash
    .\ReceiberExec.exe 
   ```
   
    And the connection should be established.

## Contributing
Any contributions you make are **greatly appreciated**.

Please see the detailed steps in our [CONTRIBUTING.md](CONTRIBUTE.md) file. These steps will guide you through the process of

1. Forking the project
2. Committing your changes
3. Opening a pull request

Please explain any changes to the codebase in detail in your pull request and make sure
you resolve any conflicts with the main branch before submitting the pull request.
Also, please make sure to write good documentation for any feature added.


## License
Distributed under the MIT License. See [LICENSE](LICENSE.txt) for more information.
