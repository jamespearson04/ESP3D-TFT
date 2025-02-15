# Direct ESP3D commands (V3.x)

## Conventions
1 - add space to separate parameters
2 - if parameter has space add \\ in front of space to not be seen as separator
3 - json json=YES json=TRUE json=1 are paremeters to switch output to json
By default output is plain text, to get json formated output
add json or json=yes after main parameters   
The json format is {
    cmd:"<command id>", //the id of requested command
    status:"<ok/error>" //give if it is success or an failure
    data:"<response>" // response corresponding to answer in json format too
}

## Commands
* Show commands help   
    `[ESP]<command id> json=<no>`

* Set/Get STA SSID   
    `[ESP100]<SSID> json=<no> pwd=<admin password for set/get & user password to get>`

* Set STA Password   
    `[ESP101]<Password> <NOPASSWORD> json=<no> pwd=<admin password>`

* Set/Get STA IP mode (DHCP/STATIC)   
    `[ESP102]<mode> json=<no> pwd=<admin password>`

* Set/Get STA IP/Mask/GW/DNS  
    `[ESP103]IP=<IP> MSK=<IP> GW=<IP> DNS=<IP> json=<no> pwd=<admin password>`

* Set/Get sta fallback mode which can be WIFI-AP, BT, OFF  
    `[ESP104]<state> json=<no> pwd=<admin password>`

*  Set/Get AP SSID   
    `[ESP105]<SSID> json=<no> pwd=<admin password>`

* Change AP Password   
    `[ESP106]<Password> <NOPASSWORD> json=<no> pwd=<admin password>`

* Set/Get AP IP   
    `[ESP107]<IP> json=<no> pwd=<admin password>`

* Set/Get AP channel   
    `[ESP108]<channel> json=<no> pwd=<admin password>`

* Set/Get radio state which can be STA, AP, BT, CONFIG, OFF  
    `[ESP110]<state> json=<no> pwd=<admin password>`

* Get current IP or IP/MSK/GW/DNS  
    `[ESP111]<ALL> json=<no>`

* Get/Set hostname   
    `[ESP112]<Hostname> json=<no> pwd=<admin password>`

* Get /Set Boot radio state which can be ON, OFF   
    `[ESP114]<state> json=<no> pwd=<user/admin password>`

* Get/Set immediate network(WiFi/BT/Ethernet) state which can be ON, OFF   
    `[ESP115]<state> json=<no> pwd=<admin password>`

* Get/Set HTTP state which can be ON, OFF   
    `[ESP120]<state> json=<no> pwd=<admin password>`

* Get/Set HTTP port   
    `[ESP121]<port> json=<no> pwd=<admin password>`

* Get/Set Telnet state which can be ON, OFF, CLOSE   
    `[ESP130]<state> json=<no> pwd=<admin password>`

* Get/Set Telnet port    
    `[ESP131]<port> json=<no> pwd=<admin password>`

* Sync / Set / Get current time   
    `[ESP140]<SYNC> <srv1=XXXXX> <srv2=XXXXX> <srv3=XXXXX> <zone=xxx> <dst=YES/NO> <time=YYYY-MM-DDTHH:mm:ss> <NOW> json=<no> pwd=<admin password>`

* Get/Set display/set boot delay in ms / Verbose boot   // Not used in ESP3D-TFT
    `[ESP150]<delay=time in milliseconds><verbose=ON/OFF>pwd=<admin password>`

* Get/Set WebSocket state which can be ON, OFF   
    `[ESP160]<state> json=<no> pwd=<admin password>`

* Get/Set WebSocket port    // Not used in ESP3D-TFT
    `[ESP161]<port> json=<no> pwd=<admin password>`

* Get/Set Camera command value / list all values in JSON/plain  // Not used in ESP3D-TFT
label can be: light/framesize/quality/contrast/brightness/saturation/gainceiling/colorbar/awb/agc/aec/hmirror/vflip/awb_gain/agc_gain/aec_value/aec2/cw/bpc/wpc/raw_gma/lenc/special_effect/wb_mode/ae_level   
    `[ESP170]<label=value> json=<no> pwd=<admin password>`

* Save frame to target path and filename (default target = today date, default name=timestamp.jpg)  // Not used in ESP3D-TFT
    `[ESP171] <path=target path> <filename=target filename>`

* Get/Set Ftp state which can be ON, OFF, CLOSE   
    `[ESP180]<state> json=<no> pwd=<admin password>`

* Get/Set Ftp ports    
    `[ESP181]ctrl=<port> active=<port> passive=<port> json=<no> pwd=<admin password>`

* Get/Set WebDav state which can be ON, OFF, CLOSE   
    `[ESP190]<state> json=<no> pwd=<admin password>`

* Get/Set WebDav port    
    `[ESP191]<port> json=<no> pwd=<admin password>`

* Get/Set SD Card Status   
    `[ESP200]<RELEASE> <REFRESH> json=<no> pwd=<user/admin password>`  
    `RELEASE` will force the release of SD from ESP3D if SD is shared  
    `REFRESH` will refresh the SD info is available`  

* Get/Set pin value   
    `[ESP201]P=<pin> V=<value> [PULLUP=YES RAW=YES ANALOG=NO ANALOG_RANGE=255]pwd=<admin password>`
    - if no V=<value> get P=<pin> value   
    - if V=<value> 0/1 set INPUT_PULLUP value, but for GPIO16(ESP8266) INPUT_PULLDOWN_16     
    - if PULLUP=YES set input pull up (for GPIO16(ESP8266) INPUT_PULLDOWN_16), if not set input     
    - if RAW=YES do not set pinmode just read value      

    Note: Flash pins according chip cannot be used

* Get/Set SD card speed divider factor 1 2 4 6 8 16 32   
    `[ESP202]<div factor> json=<no> pwd=<user/admin password>`

* Get Sensor Value / type/Set Sensor type   // Not used in ESP3D-TFT
    `[ESP210]<type=NONE/xxx> <interval=XXX in millisec> json=<no> pwd=<user/admin password>`

* Output to esp screen status   
    `[ESP214]<Text> json=<no> pwd=<user/admin password>`

* Touch Calibration 
    `[ESP215]<CALIBRATE> json=<no> pwd=<user password>`

* Get ESP pins definition  // Not used in ESP3D-TFT
    `[ESP220]json=<no> pwd=<user password>`

* Play sound   
    `[ESP250]F=<frequency> D=<duration> json=<no> pwd=<user password>`   
    Note: No parameter just play beep

* Delay command  
    `[ESP290]<delay in ms> json=<no>pwd=<user password>`

* Get full EEPROM settings content   
    `[ESP400]json=<no> pwd=<admin password>`   
    Note: do not give any passwords

*Set EEPROM setting   
    position in EEPROM, type: B(byte), I(integer/long), S(string), A(IP address / mask)    
    `[ESP401]P=<position> T=<type> V=<value> json=<no> pwd=<user/admin password>`   

* Get/Set Check update at boot state which can be ON, OFF   
    `[ESP402]<state> json=<no> pwd=<admin password>`

* Get available AP list (limited to 15)   
    output is JSON or plain text according parameter   
    `[ESP410]json=<no> <pwd=admin/user>`

* Get current settings of ESP3D   
    Output is JSON or plain text according parameter   
    `[ESP420]json=<no> <pwd=admin/user>`

* Set ESP State   
    `cmd` can be  `RESTART` to restart board or `RESET` to reset all setting to  defaults values    
    `[ESP444]<cmd> json=<no> <pwd=admin>`   

* Get available ESP3D list   
    output is JSON or plain text according parameter   
    `[ESP450]json=<no> <pwd=admin/user>`

* Get/Set UI language
   output is JSON or plain text according parameter
   `[ESP460]json=<no> <DUMP> <pwd=admin/user> <language code>`
* Get/Set connection status   
    `[ESP500] json=<no> pwd=<admin password>`

* Get/Set session timeout   
    `[ESP500]<timeout> json=<no> pwd=<admin password>`

* Change admin password    
    `[ESP550]<password> json=<no> pwd=<admin password>` 

* Change user password   
    `[ESP555]<password> json=<no> pwd=<admin/user password>`    

* Send Notification   
    `[ESP600]msg json=<no> pwd=<admin/user password>`

* Set/Get Notification settings   
    `[ESP610]type=<NONE/PUSHOVER/EMAIL/LINE/IFTTT> T1=<token1> T2=<token2> TS=<Settings> json=<no> [pwd=<admin password>]`    
    Get will give type and settings only, not the protected T1/T2

* Send Notification using URL   
    `[ESP620]URL=<encoded url> json=<no> pwd=<admin/user password>`

* Read / Stream  / Process FS file   
    `[ESP700]<filename> json=<no> pwd=<admin/user password>`

* Query and Control ESP700 stream  
    `[ESP701]action=<PAUSE/RESUME/ABORT> json=<no> pwd=<admin/user password>`

* Format ESP Filesystem   
    `[ESP710]FORMATFS json=<no> pwd=<admin password>`
 
* Format SD Filesystem   // Not used in ESP3D-TFT   
    `[ESP715]FORMATSD json=<no> pwd=<admin password>`

* List ESP Filesystem   
    `[ESP720]<Root> json=<no> pwd=<admin password>`

* Action on ESP Filesystem
    Action can be `rmdir` to remove empty directory / `remove` to delete file / `mkdir` to create directory / `exists` to check if file or directory exists / `create` create an empty file   
    `[ESP730]<Action>=<path> json=<no> pwd=<admin password>`

* List SD Filesystem    
    `[ESP740]<Root> json=<no> pwd=<admin password>`

* Action on SD Filesystem   
    Action can be `rmdir` to remove empty directory / `remove` to delete file / `mkdir` to create directory / `exists` to check if file or directory exists / `create` create an empty file    
    `[ESP750]<Action>=<path> json=<no> pwd=<admin password>`

* List Global Filesystem   
    `[ESP780]<Root> json=<no> pwd=<admin password>`

* Action on Global Filesystem   
    Action can be `rmdir` to remove empty directory / `remove` to delete file / `mkdir` to create directory / `exists` to check if file or directory exists / `create` create an empty file  
    `[ESP790]<Action>=<path> json=<no> pwd=<admin password>`

* FW Informations  
    `[ESP800]json=<no> pwd=<admin password> <time=YYYY-MM-DDTHH:mm:ss> <version=3.0.0-a11> <setup=0/1>`

* Get state / Set Enable / Disable Serial Communication   
    `[ESP900]<ENABLE/DISABLE> json=<no> pwd=<admin/user password>`
    
* Get / Set Serial Baud Rate
    `[ESP901]<BAUD RATE> json=<no> pwd=<admin/user password>`

* Get / Set USB-Serial Baud Rate
    `[ESP902]<BAUD RATE> json=<no> pwd=<admin/user password>`

* Get state / Set Enable / Disable buzzer   
    `[ESP910]<ENABLE/DISABLE> json=<no> pwd=<admin/user password>`

* Get state / Set state of  output message clients   // Not used in ESP3D-TFT
    `[ESP920]<SERIAL / SCREEN / REMOTE_SCREEN/ WEBSOCKET / TELNET /BT / ALL>=<ON/OFF> json=<no> pwd=<admin/user password>`  

* Get state / Set Enable / Disable Serial Bridge Communication   // Not used in ESP3D-TFT
    `[ESP930]<ENABLE/DISABLE> json=<no> pwd=<admin/user password>`    

* Get / Set Serial Bridge Baud Rate // Not used in ESP3D-TFT
    `[ESP931]<BAUD RATE> json=<no> pwd=<admin/user password>`

* Get / Set Serial Output // Only used in ESP3D-TFT with board having the feature
    `[ESP950]<SERIAL/USB> json=<no> pwd=<admin/user password>`

* Set quiet boot if strapping pin is High   
    `[ESP999]QUIETBOOT pwd=<admin/user password>`