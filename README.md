ATV Series VFDs to Siemens S7-1200 Function Blocks
  
  

  
    
# ATV Series VFDs to Siemens S7-1200 Function Blocks

    ATVxxx / PROFINET — Control with status and fault handling

  

  
    This folder contains a function block library for controlling Schneider Electric ATV Series VFDs via PROFINET.
       This block is designed for integration with the Siemens S7‑1200 PLCs and provide control, status, and
        fault handling for the ATVxxx Series drives.

    
      [Folder Structure](#folder-structure)
      [Function Block Overview](#fb-overview)
      [Fault & Status](#fault-status)
      [SoMove File](#somove)
      [TIA Portal Setup](#tia-portal)
      [Author](#author)
      [License](#license)
    

    
**Folder Structure**

**ATVxxx-Library-v*.*/**
            
                `ATVxxx-Library-v*.*.al15_1`: Library File
            

          
        

    
**Function Blocks Overview — *ATVxxx-ProfiNet***

![](data:image/png;base64,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)

        
          
### Inputs

          
            
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
          

          
### Outputs

          
            
- `Control_Word` : WORD — Command word to drive
            
- `Speed_Out_Hz` : INT — Output speed setpoint to drive
            
- `Status_Msg` : STRING — Text message for drive status
            
- `Is_Running` : BOOL — True if drive is running
            
- `Amps_Out` : REAL — Current motor amps
            
- `Freq_Out` : REAL — Current motor frequency
            
- `Line_Volts_Out` : REAL — Current line voltage
            
- `Is_Faulted` : BOOL — True if drive is faulted
            
- `Fault_Msg` : STRING — Text message for drive fault status
          

          
### Features

          
            
- Decodes status and fault codes to readable messages
            
- Handles drive enable/disable, run, stop, and fault reset logic

    
**Fault and Status Handling**

This function block maps drive status and fault codes to descriptive messages, making diagnostics easier. Fault reset logic is included for automatic or manual recovery.

    
**SoMove File**

The files in `SoMove-Files-TIA/` are SoMove project files for configuring the ATVxxx series drives for use with PROFINET, using static IP addressing. Use the SoMove file to help configure your ATVxxx drive as needed.

        
          
- SoMove Download: [https://www.se.com/us/en/work/products/explore/somove/](https://www.se.com/us/en/work/products/explore/somove/)
          
- SoMove Cable for connecting with ATV Drives: [TCSMCNAM3M002P](https://www.se.com/us/en/product/TCSMCNAM3M002P/connection-cable-usb-to-rj45-tesys-t-for-connection-between-pc-and-drive/)
          
- Profinet communication module for ATV Drives: [VW3A3627](https://www.se.com/us/en/product/VW3A3627/communication-module-profinet-altivar-100mbits-2-x-rj45-connectors/)
        

        
### ATV320 Setup with SoMove (Video)

        [https://youtu.be/mkD6EqSgX54](https://youtu.be/mkD6EqSgX54)
         
### ATV630 Setup with SoMove (Video)

        [https://youtu.be/GX7OG_sJxCU](https://youtu.be/GX7OG_sJxCU)

       
**TIA Portal Setup**

1. Download the ATV GSDML files and import them into your TIA Portal project:
              [PROFINET_GSDML_VW3A3627](https://www.se.com/in/en/download/document/PROFINET_GSDML_VW3A3627/)
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
          

        

        
1. Go to topology view and connect ATV320 to PLC if needed.
2. Drag a new ATVxxx function block to the ladder editor, tag the block, build, download, and go online.

        
### ATV320 Setup In TIA Portal (Video)

        [https://youtu.be/ONBzspy6DKU](https://youtu.be/ONBzspy6DKU)

  
### ATV630 Setup In TIA Portal (Video)

        [https://youtu.be/09wC5qw4LRo](https://youtu.be/09wC5qw4LRo)

    
**Author**

- [rergle@gmail.com](mailto:rergle@gmail.com)

    
**License**

This project is provided as‑is for engineering and educational use.

  

  © 2025 Rick Ergle
