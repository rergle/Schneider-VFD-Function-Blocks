ATV Series VFDs to Siemens S7-1200 Function Blocks
      
# ATV Series VFDs to Siemens S7-1200 Function Blocks

  ATVxxx / PROFINET — Control with status and fault handling 
  This folder contains a function block library for controlling Schneider Electric ATV Series VFDs via PROFINET.
  This block is designed for integration with the Siemens S7‑1200 PLCs and provide control, status, and
  fault handling for the ATVxxx Series drives.

    
## Folder Structure
- **ATVxxx-Library-v*.*/**
               -`ATVxxx-Library-v*.*.al15_1`: Library File
            
   
## Function Blocks Overview — *ATVxxx-ProfiNet***
- put pic here>
         
- ***Inputs:***        
- `Status_Word` : WORD — VFD status word (from drive)        
- `Enable` : BOOL — Enable the function block - Maintained Input       
- `E_Stop` : BOOL — Puts the VFD in E-Stop/Fast Stop state if true - Maintained Input        
- `Speed_In_Hz` : REAL — Set desired speed in Hz `00.0Hz to 120.0Hz`        
- `Run_Fwd` : BOOL — Starts the drive forward - Maintained Input         
- `Run_Rev` : BOOL — Starts the drive reverse - Maintained Input        
- `Reset_Fault` : BOOL — Reset drive faults - Momentary Input        
- `Fault_Code` : WORD — Fault code from drive       
- `Amps_In` : UINT — Amps feedback from drive        
- `Freq_In` : INT — Frequency feedback from drive       
- `Line_Volts_In` : UINT — Line voltage reading from drive


- ***Outputs:***       
- `Control_Word` : WORD — Command word to drive        
- `Speed_Out_Hz` : INT — Output speed setpoint to drive         
- `Status_Msg` : STRING — Text message for drive status         
- `Is_Running` : BOOL — True if drive is running         
- `Amps_Out` : REAL — Current motor amps        
- `Freq_Out` : REAL — Current motor frequency        
- `Line_Volts_Out` : REAL — Current line voltage        
- `Is_Faulted` : BOOL — True if drive is faulted         
- `Fault_Msg` : STRING — Text message for drive fault status
          

          
- **Features:**

  - Decodes status and fault codes to readable messages
  - Handles drive enable/disable, run, stop, and fault reset logic

## Fault and Status Handling

This function blocks maps drive status and fault codes to descriptive messages, making 
diagnostics easier. Fault reset logic is included for automatic or manual recovery.

## SoMove File

The files in `SoMove-Files-TIA/` are SoMove project files for configuring the ATVxxx 
series drives for use with PROFINET, using Static IP addressing.
Use the SoMove file to help configure your ATVxxx drive as needed.
          
- SoMove Download: [https://www.se.com/us/en/work/products/explore/somove/](https://www.se.com/us/en/work/products/explore/somove/)
          
- SoMove Cable for connecting with ATV Drives: [TCSMCNAM3M002P](https://www.se.com/us/en/product/TCSMCNAM3M002P/connection-cable-usb-to-rj45-tesys-t-for-connection-between-pc-and-drive/)
          
- Profinet communication module for ATV Drives: [VW3A3627](https://www.se.com/us/en/product/VW3A3627/communication-module-profinet-altivar-100mbits-2-x-rj45-connectors/)
        

        
### ATV320 Setup with SoMove (Video)
[![Watch the video](https://img.youtube.com/vi/mkD6EqSgX54/0.jpg)](https://youtu.be/mkD6EqSgX54)
 
         
### ATV630 Setup with SoMove (Video)

        - video here

       
**TIA Portal Setup**

1. Download the ATV GSDML files and import them into your TIA Portal project: [PROFINET_GSDML_VW3A3627](https://www.se.com/in/en/download/document/PROFINET_GSDML_VW3A3627/)
2. Open the Libraries tab and from the Global libraries menu select Open global library
3. Select the `"ATVxx-Library-v*.*"` library file and load it into the project
4. In the new Library, navigate to `"ATVxx-Library-v*.* > Master copies"`
5. Drag the Function Block into the `"Program blocks"` folder
6. (Optionaly)Drag the "VFD_Tags" into the `"PLC tags"` folder.
7. Open “Device configuration” and set the PLC IP address.
8. In Network view, find in the Catalog:
              *Other field devices > PROFINET IO > Drives > Schneider Electric > ATV320 / 630 > ATV320 / 630*
9. Add the ATV320 / 630 and assign a network connection.
10. Open the ATV320 / 630 “Properties” → “General” → *PROFINET interface[X1]* → “Ethernet addresses” and select “IP address is set directly at device”.
11. Right‑click the ATV320 / 630 → “Assign device name”, search and assign a name.
12. In the Catalog select: *Module > Telegrams > Telegram 101 (4PKW/6PZD)*.
13. Add the Telegram to the project, then go to *Properties > General* and open “Module parameters”.
14. Add the following registers to the Telegram:
            
    #### Telegram Registers          
- `OCA1  8501` — Command Register : WORD              
- `OCA2  8502` — Reference Frequency : INT            
- OCA3
- OCA4
- OCA5
- OCA6             
- `OMA1  3201` — Status Register : WORD            
- `OMA2  8604` — Output velocity in Motor RPM : INT            
- `OMA3  3207` — Mains Voltage : UINT            
- `OMA4  3204` — Motor Current : UINT            
- `OMA5  7121` — Last error occurred : WORD           
- `OMA6  3202` — Motor Frequency : INT

15. Select the “IO tags” tab in the Telegram and tag the following (start 4 words down from the top):

#### Data From Drive            
- Blank — `%IW68`         
- Blank — `%IW70`        
- Blank — `%IW72`
- Blank — `%IW74`           
- `Status_Word`------`%IW76` — 3201          
- `Motor_Rpms_In`---`%IW78` — 8604          
- `Line_Volts_In`---`%IW80` — 3207          
- `Amps_In`-----------`%IW82` — 3204            
- `Fault_Code`-------`%IW84` — 7121            
- `Freq_Fdbk_In`----`%IW86` — 3202
             
#### Data To Drive            
- Blank — `%QW68`         
- Blank — `%QW70`          
- Blank — `%QW72`           
- Blank — `%QW74`            
- `Control_Word` — `%QW76` — 8501            
- `Speed_Out_Hz` — `%QW78` — 8502            
- Blank — `%QW80`            
- Blank — `%QW82`            
- Blank — `%QW84`            
- Blank — `%QW86`
          

        

        
16. Go to topology view and connect ATV320 to PLC if needed.
17. Drag a new ATVxxx function block to the ladder editor, tag the block, build, download, and go online.

        
### ATV320 Setup In TIA Portal (Video)

        - [https://youtu.be/ONBzspy6DKU](https://youtu.be/ONBzspy6DKU)

  
### ATV630 Setup In TIA Portal (Video)

       - [https://youtu.be/09wC5qw4LRo](https://youtu.be/09wC5qw4LRo)

    
**Author**

- [rergle@gmail.com](mailto:rergle@gmail.com)

    
**License**

This project is provided as‑is for engineering and educational use.

  

  © 2025 Rick Ergle
