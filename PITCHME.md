---?image=assets/images/gitpitch-audience.jpg
@title[Platform Build Win Lab]
<br><br>
<span style="font-size:0.75em" >This slide deck has moved to:  https://gitpitch.com/tianocore-training/Platform_Build_Win_Lab/master#/</span>
<br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

Platform Build Lab MinnowBoard Max - Windows 

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  Platform Build Lab MAX Windows

  Copyright (c) 2019, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



---  
@title[Lesson Objective]

### <p align="center"<span class="gold"   >Platform Build Labs </span></p>
<span style="font-size:0.9em">Lab Setup and Build for Minnowboard Max/Turbot</span> <br>
<br>
<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp; Hardware Setup for Minnowboard Max/Turbot </span><br><br>
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp; Build a EDK II Platform using Minnowboard <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Max/Turbot </span> <br><br>
  

---?image=assets/images/binary-strings-black2.jpg
@title[Setup MAX HW Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Platform HW Setup</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Setup hardware for MinnowBoard Max/Turbot </span>

---?image=/assets/images/slides/Slide4.JPG
@title[MAX/Turbot HW]
### <p align="right"><span class="gold" >EDK II Platform (MinnowBoard MAX/Turbot)</span></p>
@snap[south-west span-45 ]
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.6em" >Intel<sup>&reg;</sup> Atom processor E3800 Series<br> &lpar;Formerly Bay Trail-I&rpar;</span></p>
<br>
@snapend
Note:

This lab shows the build process for an actual platform – Minnowboard.org

- Using Tianocore source
- Open source EDK II plus open source binary obj. packages

---?image=/assets/images/slides/Slide5.JPG
@title[Workshop Lab Hardware]
### <p align="right"><span class="gold" >MinnowBoard  MAX Workshop Lab Hardware</span></p>
@snap[south span-100 ]
<br>
<p style="line-height:80%" ><span style="background-color: #FFFFFF; font-size:0.60em; "> <font color="red">&nbsp;<b>**Warning</b> do not use any other power supply than 5V or the board will Fry&nbsp;&nbsp;</font></span></p>
<br>
@snapend
Note:

**Warning do not use any other power supply than 5V or the board will Fry


---?image=/assets/images/slides/Slide6.JPG
@title[Instructions for Lab Materials]
### <p align="right"><span class="gold" >Instructions for Lab Materials</span></p>
<span style="font-size:0.9em">Directory `C:\PlatformBuildLab2_FW\FW\PlatformBuildLab` </span>
<div class="left">
 <ul style="list-style-type:none">
   <li><span style="font-size:0.8em">FTDI Driver for Serial UART Cable (COM Port)  <a href="http://www.ftdichip.com/FTDrivers.htm "> ftdichip.com/FTDrivers.htm </a></span> </li>
   <li><span style="font-size:0.8em">TeraTerm (terminal software for COM Port)  <a href="https://en.osdn.jp/projects/ttssh2/releases/"> ttssh2/releases/</a></span> </li>
 </ul>
</div>
<div class="right">
<div class="left1"> &nbsp;</span>
</div>

@snap[south span-100 ]
<p style="line-height:60%" align="left" ><span style="font-size:0.57em;" >
&nbsp; Note: Download  FTDI Driver and TeraTerm as described in the Readme.txt for each directory 
</span></p>
@snapend

Note:

---?image=/assets/images/slides/Slide7.JPG
@title[Setup MinnowBoard Max Test System]
<p style="line-height:85%" align="right"><span class="gold" >@size[1.1em](<b>Setup MinnowBoard Max Test System</b>)</span></p>
@snap[north-west span-60 ]
<br>
<br>
<p style="line-height:50%"><span style="font-size:0.7em"><b>Hardware:</b></span></p>
<ul style="list-style-type:none; line-height:0.5;">
  <li><span style="font-size:0.5em">- System Under Test (SUT) - MinnowBoard Max  </span>  </li>
  <li><span style="font-size:0.5em">- USB to 3.3V TTL Cable  (6 pin to USB Type A) </span>  </li>
  <li><span style="font-size:0.5em">- 5V power supply </span>  </li>
</ul>


<p style="line-height:50%"><span style="font-size:0.6em">
Connect the USB w/ 6 pin header to SUT (MAX) <br><br>
Connect the USB Type A connector to Host (Laptop) <br><br>
On your Host  <b>Go</b> to the "<b>Device Manager</b>" in the control panel <br><br>
Under the "<b>Other devices</b>" category you will see a yellow  @fa[exclamation-triangle gp-bullet-gold ]   with a warning icon next to it.  <br><br>
You may already have this driver installed if you do not see a @fa[exclamation-triangle gp-bullet-gold ]   warning under "<b>Other devices</b>" 
</span> </p>
@snapend

Note:

- Hardware:
  - System Under Test (SUT) – MinnowBoard Max
  - USB to 3.3V TTL Cable  (6 pin to USB Type A)
  -  5V power supply

- Connect the USB w/ 6 pin header to SUT (MAX)

- Connect the USB Type A connector to Host (Laptop)

- On your Host  Go to the “Device Manager” in the control panel. 

- Under the "Other devices" category you will see a yellow   !   with a warning icon next to it. 


- You may already have this driver installed if you do not see a  !  warning under “Other devices”


---?image=/assets/images/slides/Slide8.JPG
@title[Setup COM port on Host]
<p style="line-height:80%" align="right"><span class="gold" >@size[1.1em](<b>Setup COM port on Host</b>)</span></p>
<p style="line-height:40%"><span style="font-size:0.6em"><br> &bull; Right click yellow  @fa[exclamation-triangle gp-bullet-gold ]   and select "Update Driver Software" from the <b>Device Manager menu</b></span></p>

@snap[north-west span-75 ]
<br>
<br>
<br>
<p style="line-height:40%"><span style="font-size:0.6em">
 &bull; Select "Browse my computer for driver software" <br><br>
 &bull; Click the <b>Browse</b>  button – Click @fa[check-square gp-bullet-white] on "Include subfolders"<br><br>
 &bull; Browse to the location of the folder for the FTDI driver<br><br>
 &bull; Click on the folder and press <b>OK</b>
@snapend


@snap[south-west span-30 ]
<p style="line-height:50%"><span style="font-size:0.6em">
&bull; Press <b>Next</b><br>
&nbsp;&nbsp;Driver will be installed
</span> </p>
<br>
<br>
<br>
<br>
<br>
@snapend

Note:
- Right click yellow   !  and select "Update Driver Software“ from the Device Manager menu 
- Select "Browse my computer for driver software”.
- Click the Browse  button. – Click on “Include subfolders”
- Browse to the location of the folder you unzipped earlier for the FIDI driver.
- Click on the folder and press OK.
- Press Next.  
- Driver will be installed



---?image=/assets/images/slides/Slide9.JPG
@title[Setup TeraTerm]
<p style="line-height:80%" align="right"><span class="gold" >@size[1.1em](<b>Setup TeraTerm</b>)</span></p>
@snap[north-west span-35 ]
<br>
<br>
<p style="line-height:50%"><span style="font-size:0.7em">
Unzip and Install TeraTerm<br><br>
Open TeraTerm Software<br><br>
Select the serial port assigned
</span></p>
@snapend


@snap[south-east span-55 ]
<br>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.6em">
Go to <b>Setup &minus;&gt; Serial Port</b> and set the following:<br>
  &nbsp;&nbsp;&bull; Baud: 115200<br>
  &nbsp;&nbsp;&bull; Parity: None<br>
  &nbsp;&nbsp;&bull; Data Bits: 8<br>
  &nbsp;&nbsp;&bull; Stop Bits: 1<br>
  &nbsp;&nbsp;&bull; Flow Control: Xon/Xoff
</span></p>
@snapend

Note:
- Unzip and Install TeraTerm
- Open TeraTerm Software
- Select the serial port assigned 

- Go to Setup- Serial Port and set the following:
  - Baud: 115200
  - Parity: None
  - Data Bits: 8
  - Stop Bits: 1
  - Flow Control: Xon/Xoff


---?image=/assets/images/slides/Slide10.JPG
@title[Power on MinnowBoard MAX]
<p style="line-height:80%" align="right"><span class="gold" >@size[1.1em](<b>Power on MinnowBoard MAX</b>)</span></p>
@snap[north-west span-100 ]
<br>
<br>
<p style="line-height:60%"><span style="font-size:0.8em">
Connect the Power supply cable to the MinnowBoard  MAX
<br>
<br>
MinnowBoard MAX should boot to the UEFI Shell in the TeraTerm window.
</span></p>
@snapend

Note:
- Connect the Power supply cable to the MinnowBoard  MAX
- MinnowBoard MAX should boot to the UEFI Shell in the TeraTerm window.


---?image=assets/images/gitpitch-audience.jpg
@title[End of Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;End of Lab </span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; @fa[chevron-right gp-bullet-cyan]  &nbsp;&nbsp;to continue  </span>
 

---?image=assets/images/binary-strings-black2.jpg 
@title[Lab 3 -Build Max/Turbot Section]
<br><br><br><br><br>
## <p align="center"><span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Build MinnowBoard Turbot</span></p>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>


---?image=/assets/images/slides/Slide4.JPG
@title[MAX/Turbot HW]
### <p align="right"><span class="gold" >EDK II Platform (MinnowBoard MAX/Turbot)</span></p>
@snap[south-west span-45 ]
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.6em" >Intel<sup>&reg;</sup> Atom processor E3800 Series<br> &lpar;Formerly Bay Trail-I&rpar;</span></p>
<br>
@snapend
Note:

-  Intel® Atom processor E3800 Series  (Formerly Bay Trail-I)


---?image=/assets/images/slides/Slide14.JPG
@title[MinnowBoard MAX/ Turbot Platform]
<br>
<p align="left"><span class="gold" ><b>Where to get Open Source<BR> MinnowBoard Max</b></span></p>

@snap[north-west span-65  ]
<br>
<br>
<br>
<br>
<br>
<ul style="list-style-type:disc; line-height:0.85;">
 <li><span style="font-size:0.8em;" > Open Source <a href="https://github.com/tianocore/tianocore.github.io/wiki/MinnowBoardMax">Max Development Wiki</a> </span> </li>
 <li><span style="font-size:0.8em;" > How to Download  & Build: <a href="https://github.com/tianocore/edk2-platforms/blob/master/Platform/Intel/Vlv2TbltDevicePkg/Readme.md">Readme.md</a> </span> </li>

</ul>
@snapend

Note:
- Step by step if NOT downloading Lab release of Minnowboard MAX/Turbot 

---
@title[Download MinnowBoard MAX Lab Source]
### <p align="right"><span class="gold" >Download MAX Lab Source</span></p>
<span style="font-size:0.9em" >Download the PlatformBuildLab2_FW.zip from : </span> @fa[github gp-bullet-white] <span style="font-size:0.7em"><a href="https://github.com/tianocore-training/PlatformBuildLab2_FW/archive/master.zip">github.com PlatformBuildLab_FW.zip</a></span><br>
<br>
<span style="font-size:0.9em" >OR<br>Use `git clone` to download the PlatformBuildLab_FW<span>
```
$ git clone https://github.com/tianocore-training/PlatformBuildLab2_FW.git
```
<span style="font-size:0.9em" >Directory PlatformBuildLab_FW will be created</span>
```
   FW 
    - PlatformBuildLab
       - asl				                    - Asl Compiler 
       - FTDI-Driver		                    - Serial / USB cable 
       - MaxWS                                  - Minnowboard Max Source 
	   - TeraTerm                               - Terminal app
```

Note:


---?image=/assets/images/slides/Slide16.JPG
@title[Preparing to Build]
<p align="right"><span class="gold" >@size[1.1em](<b>Preparing to Build  </b>)</span>
<span style="font-size:0.75em;" >  </span></p>

<p style="line-height:70%"><span style="font-size:0.8em">
Directory <font face="Consolas">C:\PlatformBuildLab2_FW\FW\PlatformBuildLab</font> from Download or zip
</span></p>

@snap[north-west span-60 ]
<br>
<br>
<br>
<br>
<br>
<br>
<p style="line-height:70%"><span style="font-size:0.8em">
@size[1.10em](<font color="#87E2A9"> &#10102;</font>) &nbsp; Copy <font face="Consolas">\asl</font> Folder to <font face="Consolas">C:\</font><br><br><br>
</span></p>

@snapend

@snap[south span-100 ]
<p style="line-height:60%" align="left" ><span style="font-size:0.57em;" >
&nbsp; Note: Download  Asl compiler as described in the Readme.txt
</span></p>
@snapend

Note:
<pre>
Copy \asl Folder to C:\
</pre>

---?image=/assets/images/slides/Slide17.JPG
@title[Get the Minnowboard Max Source]
<p align="right"><span class="gold" >@size[1.1em](<b>Copy Minnowboard Max Source  </b>)</span>
<span style="font-size:0.75em;" >  </span></p>


@snap[north-west span-20 ]
<br>
<br>
<p style="line-height:40%"><span style="font-size:0.8em"><br>@size[1.1em](<font color="#87E2A9"> &#10103;</font>)</span></p>
@snapend

@snap[north-east span-93 ]
<br>
<br>
<p style="line-height:70%" align="left"><span style="font-size:0.8em">
Open a VS Command Prompt<br>
Create a working space source directory under the home directory<br></span>
<font face="Consolas"><span style="background-color: #000000; font-size:0.50em; "> 
C:\&gt; mkdir FW</span></font></span><br><br>
<span style="font-size:0.7em">
From the <font face="Consolas">FW/PlatformBuildLab</font> folder, copy and paste folder "<font face="Consolas">..FW/MaxWS" to "C:/FW/MaxWS"</font>
</span></p>

@snapend


Note:
- Open a VS prompt  
- Create a working  space source directory under the home directory
   - bash$ mkdir FW
- From the FW/PlatformBuildLab folder, copy and paste folder “FW/Max” to ~src
 



---
@title[Platform Source Directory Structure]
<p align="right"><span class="gold" >@size[1.1em](<b>Platform Source Directory Structure   </b>)</span>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-100 ]
<br>
<br>
<p style="line-height:60%" align="left" ><span style="font-size:0.6em; font-family:Consolas;" >
./MaxWs/ <br>&nbsp;&nbsp;
	edk2/<br>&nbsp;&nbsp;&nbsp;&nbsp;
       <font face="Arial">@size[.8em](&lpar;EDK II common packages&rpar;)</font><br>&nbsp;&nbsp;&nbsp;&nbsp;
		BaseTools/<br>&nbsp;&nbsp;
	edk2-platforms/<br>&nbsp;&nbsp;&nbsp;&nbsp;
       Platform/Intel/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
		   Vlv2TbltDevicePkg /<br>&nbsp;&nbsp;&nbsp;&nbsp;
 	   silicon/Intel/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          Vlv2DeviceRefCodePkg/<br>&nbsp;&nbsp;
	edk2-non-osi/<br>&nbsp;&nbsp;
	nasm/ &ast;&ast;<br>&nbsp;&nbsp;
	openssl/ &ast;&ast;<br>&nbsp;&nbsp;
<br><br><br>&nbsp;
</span></p>

@snapend


@snap[north-east span-90  fragment]
<br>
<br>
<p style="line-height:60%" align="left" ><span style="font-size:0.6em; font-family:Consolas;" >
<br>
@color[yellow](&#10094;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar; )<br>&nbsp;&nbsp;&nbsp;&nbsp;
<br>&nbsp;&nbsp;&nbsp;&nbsp;
<br>&nbsp;&nbsp;
<br>&nbsp;&nbsp;&nbsp;&nbsp;
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@color[yellow](&#10094;&horbar;&horbar;&horbar;&horbar; )<br>&nbsp;&nbsp;&nbsp;&nbsp;
</span></p>

@snapend


@snap[south span-100 ]
<p style="line-height:30%" align="left" ><span style="font-size:0.5em;" >
&nbsp; &ast;&ast;Nasm compiler and &ast;&ast;Openssl may need to be downloaded per the Readme.txt file in each directory
</span></p>
<br>
@snapend

Note:
-  Platform Source Directory Structure
   -  Build from /Vlv2TbltDevicePkg  directory

---?image=/assets/images/slides/Slide39.JPG
@title[Platform Source Directory Structure]
### <p align="right"><span class="gold" >Platform Source Directory Structure </span></p>


Note:
-  Platform Source Directory Structure
   -  Build from /Vlv2TbltDevicePkg  directory

---
@title[Steps to Build & Install Firmware]
<br>
### <p align="center"><span class="gold" >Steps to Build & Install Firmware</span></p>
<ul style="list-style-type:none; line-height:0.9;">
  <li><span style="font-size:0.9em">@size[1.125em](<font color="yellow"> &#10102;</font>)&nbsp; Open VS Command prompt </span></li>
  <li><span style="font-size:0.9em">@size[1.125em](<font color="yellow"> &#10103;</font>)&nbsp; Cd to  project directory :    <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="font-size:0.6em">`C:/fw/Max/edk2-platforms/Vlv2TbltDevicePkg` </span></li>
  <li><span style="font-size:0.9em">@size[1.125em](<font color="yellow"> &#10104;</font>)&nbsp; Invoke the build process</span></li>
  <li><span style="font-size:0.9em">@size[1.125em](<font color="yellow"> &#10105;</font>)&nbsp; Locate build output (.BIN file for BIOS image)</span></li>
  <li><span style="font-size:0.9em">@size[1.125em](<font color="yellow"> &#10106;</font>)&nbsp; Flash binary image onto the platform</span></li>
  <li><span style="font-size:0.9em">@size[1.125em](<font color="yellow"> &#10107;</font>)&nbsp; Reset and verify new firmware</span></li>
</ul>
<br>
<br>
<span style="font-size:0.9em"><font color="yellow"><i><b>Next slides will follow the above steps</b></i></font></span>


Note:

Slide says it all
 
---?image=/assets/images/slides/Slide41.JPG
@title[Open a VS Command Prompt]
### <p align="right"><span class="gold" >Open a VS Command Prompt </span></p>
<p style="line-height:80%" align="left"><span style="font-size:0.8em">Follow Steps from <a href="https://gitpitch.com/tianocore-training/Platform_Build_Win_Lab/master#/2">here</a> to Pin the Visual Studio Command Prompt to the Windows Task Bar <br>
@size[1.25em](<font color="yellow"> &#10102;</font>)&nbsp;&nbsp;Open a Visual Studio Command Prompt<span></p>


Note:

---
@title[Platform Build Scripts]
<p align="right"><span class="gold" >@size[1.1em](<b>Platform Build Scripts</b>)</span></p>

@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:70%" align="center"><span style="font-size:0.8em">Platform Build Scripts<br>&nbsp; </span></p>)
<p style="line-height:80%"><span style="font-size:0.8em">Many Platform have a bash or bat script file to pre or post process the EDK II build process</span></p>

<p style="line-height:70%"><span style="font-size:0.7em">For MinnowBoard MAX : `Build_IFWI.bat or Build_IFWI.sh` <br></span>
<span style="font-size:0.7em"><Example:<br>
&nbsp;Build_IFWI  <br>
&nbsp;&nbsp;&ndash; pre build processing <br>
&nbsp;&nbsp;&ndash;  calls `vlv_bld` - a platform script to preform the EDK II `build` <br> 
&nbsp;&nbsp;&ndash; determines date <br>
&nbsp;&nbsp;&ndash; board ID<br>
&nbsp;&nbsp;&ndash; post build stitching<br>
</span></p>

Note:

For the platform edk II builds usually a script is called that will do pre and post build processing.  
There is also this capability that is part of the .dsc but many developers have not taken advantage of this feature


---?image=/assets/images/slides/Slide42.JPG
@title[Build Process for DEBUG]
### <p align="right"><span class="gold" >Build Process for DEBUG BIOS </span></p>
<p style="line-height:80%" align="left"><span style="font-size:0.8em">
From the VS command Prompt ... Enter:<br>
@size[1.25em](<font color="yellow"> &#10103;</font>)&nbsp;&nbsp;</span>
<font face="Consolas"><span style="background-color: #000000; font-size:0.650em; "> 
&nbsp;cd c:\FW\Max\edk2-Platforms\Vlv2TbltDevicePkg&nbsp;&nbsp;</span></font></span><br>
<span style="font-size:0.8em">
@size[1.25em](<font color="yellow"> &#10104;</font>)&nbsp;&nbsp;</span>
<font face="Consolas"><span style="background-color: #000000; font-size:0.650em; "> 
&nbsp;Build_IFWI.bat /l MNW2 Debug&nbsp;&nbsp;</span></font></p>


Note:

- From the VS Command Prompt … ENTER:

<pre>
$ cd C:\FW\Max\edk2-Platforms\Vlv2TbltDevicePkg 
$ Build_IFWI.bat /l MNW2 Debug
</pre>

---
@title[Examine Command Line & Build Parameters]
<p align="right"><span class="gold" >@size[1.1em](<b>Examine Build Parameters</b>)</span></p>

@snap[north-west span-100 ]
<br>
<br>
@box[bg-black text-yellow rounded my-box-pad2  ](<p style="line-height:60%" align="left"><span style="font-size:0.65em; font-family:Consolas; " >&nbsp;&nbsp;build<br><br><br>&nbsp;&nbsp;</span></p>)
@snapend


@snap[north-east span-85  fragment]
<br>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.60em; font-family:Consolas; " >
<font color="#75deFF">-D SYMBOLIC_DEBUG=TRUE&nbsp;&nbsp;  -D LOGGING=TRUE<br>
 . . . -D <i> Option &lpar;n&rpar;</i> </font>
</span></p>
@snapend


@snap[north-east span-30  fragment]
<br>
<br>
<p style="line-height:40%" align="left"><span style="font-size:0.8em"><br></span></p>
@box[bg-white text-black rounded my-box-pad2  ](<p style="line-height:70%" align="left"><span style="font-size:0.8em"><font color="blue"><b>&nbsp;&nbsp;MACROS</font><br>&nbsp;&nbsp;Logging<br>&nbsp;&nbsp;Symbolic Debug<br>&nbsp;&nbsp;</b></span></p>)
@snapend


@snap[north-west span-100 fragment ]
<br>
<br>
<br>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.8em"><font color="#87E2A9"><br><br><b>Properties from `Conf\Target.txt`</b></font></span></p>
<table id="recTable">
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>TARGET</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](DEBUG)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><b>Build Mode</b></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>TARGET_ARCH</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](IA32 X64)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><b>CPU Architecture</b></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>TOOL_CHAIN_TAG</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](VS2013x86)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><b>VS Tool Chain</b></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>ACTIVE_PLATFORM</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:040%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](Vlv2TbltDevicePkg /PlatformPkgX64)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><b>Platform DSC file</b></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:040%"><span style="font-size:0.460em; font-family:Consolas; " ><b>MAX&lowbar;CONCURRENT&lowbar; THREAD_NUMBER</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](1)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025" width="35%"><p style="line-height:010%"><span style="font-size:0.6em" ><b>Thread Count</b></span></p></td>
	</tr>
</table>


@snapend

---
@title[Examine Platform Parameters]
<p align="right"><span class="gold" >@size[1.1em](<b>Platform Build and PCD Parameters</b>)</span></p>

@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:70%" align="center"><span style="font-size:0.8em">Platform Parameters<br>&nbsp; </span></p>)
<p style="line-height:80%"><span style="font-size:0.8em">Many Platform Parameters are defined in  a top .DSC file that controls  PCD and build switches</span></p>

<p style="line-height:70%"><span style="font-size:0.7em">For MinnowBoard MAX : `PlatformPkgConfig.dsc` <br>Example:</span></p>

```xml
 #
 # TRUE is ENABLE. FASLE is DISABLE.
 #
  //  . . .
 DEFINE SECURE_BOOT_ENABLE = TRUE
 DEFINE USER_IDENTIFICATION_ENABLE = FALSE
 DEFINE VARIABLE_INFO_ENABLE = FALSE
 DEFINE S3_ENABLE = TRUE
 DEFINE CAPSULE_ENABLE = TRUE
 DEFINE CAPSULE_RESET_ENABLE = TRUE
  // . . .

```

Note:

many will have "ifdef" statements in the major .dsc file in order to enable a feature or not


---?image=/assets/images/slides/Slide51.JPG
@title[Build Process for Release]
### <p align="right"><span class="gold" >Build Process for Release</span></p>
<p style="line-height:80%" align="left"><span style="font-size:0.8em">
From the VS command Prompt ... Enter:<br>
</span><br>
<span style="font-size:0.8em">
@size[1.25em](<font color="yellow"> &#10104;</font>)&nbsp;&nbsp;</span>
<font face="Consolas"><span style="background-color: #000000; font-size:0.650em; "> 
&nbsp;Build_IFWI.bat /l MNW2 Release&nbsp;&nbsp;</span></font></p>


@snap[north-east span-30  fragment]
<br>
<br>
<p style="line-height:40%" align="left"><span style="font-size:0.8em"><br></span></p>
@box[bg-white text-black rounded my-box-pad2  ](<p style="line-height:70%" align="left"><span style="font-size:0.8em"><font color="blue"><b>&nbsp;&nbsp;Note MACROS</font><br>&nbsp;&nbsp;Logging<br>&nbsp;&nbsp;Symbolic Debug<br>&nbsp;&nbsp;<font color="blue">Set to FALSE</font><br>&nbsp;&nbsp;</b></span></p>)
@snapend



Note:
From VS Prompt enter:
```
$ cd Vlv2TbltDevicePkg 
$ Build_IFWI.bat /l MNW2 Release
```

---
@title[DEBUG & RELEASE Differences]
### <p align="right"><span class="gold" >DEBUG & RELEASE Differences</span></p>

@box[bg-purple-pp text-white rounded my-box-pad2 fragment](<p style="line-height:70%"><span style="font-size:0.9em" >Slower boot because the time it takes to display debug info <br>&nbsp; </span></p>)
@box[bg-green-pp text-white rounded my-box-pad2 fragment](<p style="line-height:70%"><span style="font-size:0.9em" >Larger image because of debug code & embedded info<br>&nbsp;  </span></p>)
@box[bg-gold2 text-white rounded my-box-pad2  fragment](<p style="line-height:70%"><span style="font-size:0.9em" >Uses the serial port for debug string output<br>&nbsp; </span></p>)
@box[bg-royal text-white rounded my-box-pad2  fragment](<p style="line-height:80%"><span style="font-size:0.9em" >Contains detailed debug strings that show the<br> boot progress and various `ASSERT` / `TRACE` errors<br>&nbsp; </span></p>)

 
Note:

### DEBUG build …
- Contains detailed debug strings that show the boot process, along with various ASSERT/TRACE errors
- Uses the serial port for debug string output
- Larger image than RELEASE, due to the embedded debug info
- Slower boot than RELEASE, due to the time it takes to display the debug info


### RELEASE build …
- Does not contain the debug strings
- Does not use the serial port for debug output
- Smaller image than DEBUG
- Faster boot than DEBUG

---?image=/assets/images/slides/Slide57.JPG
@title[Build Process Completed]
### <p align="right"><span class="gold" >Build Process Completed</span></p>
<span style="font-size:0.9em" >@size[1.25em](<font color="yellow"> &#10105;</font>)&nbsp;&nbsp;Locate the build .BIN image</span>

@snap[south-west span-100  ]
<p style="line-height:80%" align="left"><span style="font-size:0.9em" >

The platform build script post build process will stitch the multiple firmware volumes generated by the EDK II build process into the final <b> .BIN</b> image.<br><br>
The script displays the location of the final <b>.BIN </b> file<br><br>
</span></p>
@snapend

Note:
- The EDK II build generates multiple firmware volumes, which are combined in the .BIN image
- typically the platform script will call a stitching process to combine all the images together in  post processing after the EDK II build

---?image=/assets/images/slides/Slide55_1.JPG
@title[Flash onto the MinnowBoard MAX]
### <p align="right"><span class="gold" >Flashing the New BIOS</span></p>
@snap[north-west span-100  ]
<br>
<br>
<span style="font-size:0.9em" >@size[1.25em](<font color="yellow"> &#10106;</font>)&nbsp;&nbsp;Flash the binary image</span>
@snapend


<br>
1.  <span style="font-size:0.85em" >&nbsp;&nbsp;Access Max Binary image file from build folder</span>
  - <span style="font-size:0.75em" >`C:/fw/Max/Vlv2TbltDevicePkg/Stitch`</span>
  - <span style="font-size:0.75em" >DEBUG 	MNW2MAX1.X64.D01.0098._date_.bin</span>
  - <span style="font-size:0.75em" >RELEASE	MNW2MAX1.X64.R01.0098._date_.bin</span>
2. <span style="font-size:0.85em" >&nbsp;&nbsp;Copy BIN files to a USB Thumb drive</span>
3. <span style="font-size:0.85em" >&nbsp;&nbsp;Copy </span><span style="font-size:0.65em" >`MinnowBoard.MAX.FirmwareUpdateX64.efi`</span><span style="font-size:0.85em" > to a USB thumb &nbsp;&nbsp;drive from `$.../FW/PlatformBuildLab`</span>
4. <span style="font-size:0.85em" >&nbsp;&nbsp;Boot to UEFI Shell on Max and type "`FS0:`"</span>

Note:
1.  Access Max Binary image file from build folder
  - `C:/fw/Max/Vlv2TbltDevicePkg/Stitch`
  - DEBUG 	MNW2MAX1.X64.D01.0098._date_.bin
  - RELEASE	MNW2MAX1.X64.R01.0098._date_.bin
2. Copy BIN files to a USB Thumb drive
3. Copy MinnowBoard.MAX.FirmwareUpdateX64.efi to a USB thumb drive from $.../FW/PlatformBuildLab
4. Boot to UEFI Shell on Max and type "FS0:"



---?image=/assets/images/slides/Slide56_1.JPG
@title[Flash onto the MinnowBoard MAX 02]
### <p align="right"><span class="gold" >Flashing the New BIOS</span></p>

<p style="line-height:70%"><span style="font-size:0.85em" >5.  &nbsp;&nbsp;Run update `.efi` utility with either BIN file </span> <span style="font-size:0.65em" >&lpar;<i>Note</i> the “TAB” Key <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;will fill out the command line for you &rpar;</span></p>

```
FS0:\> MinnowBoard.MAX.FirmwareUpdateX64.efi MNW2MAX1.X64.0098.D01.1801181447.bin
```
<br>
<span style="font-size:0.75em" >Wait for the new firmware update to finish</span>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p style="line-height:70%"><span style="font-size:0.85em" >6. &nbsp;&nbsp;Reset and boot new firmware</span></p>

 
Note:
5. Run update .efi utility with either BIN file  (Note the “TAB” Key will fill out the command line for you 
```
FS0:\> MinnowBoard.MAX.FirmwareUpdateX64.efi MNW2MAX1.X64.0098.D01.1801181447.bin
```

6. Reset and boot new firmware


---?image=/assets/images/slides/Slide57_1.JPG
@title[Verify after Firmware Update]
### <p align="right"><span class="gold" >Verify after Firmware Update</span></p>
@snap[north-west span-100  ]
<br>
<br>
<span style="font-size:0.9em" >@size[1.25em](<font color="yellow"> &#10107;</font>)&nbsp;&nbsp;Reboot and Verify</span>
@snapend

<br>
- <span style="font-size:0.85em" >Verify that the Firmware was updated by checking the Date</span>
- <span style="font-size:0.85em" >At the shell prompt type “exit”</span>
- <span style="font-size:0.85em" >The EDK II front page will show the BIOS ID with Date/time stamp</span>


Note:

- Verify that the Firmware was updated by checking the Date
- At the shell prompt type “exit”
- The EDK II front page will show the BIOS ID with Date/time stamp


---  
@title[Summary]
##### <p align="center"<span class="gold"   >Summary </span></p><br>

 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;Pin Visual Studio Command Prompt to Windows <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Task Bar  </span><br><br>
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;<a href='https://gitpitch.com/Laurie0131/Platform_Build_Win_Lab/master#/9'>Lab 1:</a> Build a EDK II Platform using Nt32 package </span><br><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;<a href='https://gitpitch.com/Laurie0131/Platform_Build_Win_Lab/master#/21'>Lab 2:</a> Hardware Setup for Minnowboard Max/Turbot </span><br><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;<a href='https://gitpitch.com/Laurie0131/Platform_Build_Win_Lab/master#/30'>Lab 3:</a> Build a EDK II Platform using Minnowboard <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Max/Turbot </span> <br><br>
 

---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<br>
![Questions](/assets/images/questions.JPG =10x) 

---
@title[return to main]
<p align="center"><span class="gold"   >@size[1.2em](<b>Return to Main Training Page</b>)</span></p>
<br>
<br>
<br>
<br>
<br>
<p align="center"><span style="font-size:0.9em">Return to Training Table of contents for next presentation <a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">link</a></span></p>

@snap[north span-30 ]
<br>
<br>
<br>
<a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">
![trainingLogo](/assets/images/returnTrainingLogo.png)</a>
@snapend

---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<br><br><br>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)


---
@title[Acknowledgements]
#### <p align="center"><span class="gold"   >Acknowledgements</span></p>

```c++
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2019, Intel Corporation. All rights reserved.
**/

```


---?image=assets/images/binary-strings-black2.jpg
@title[Backup Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Back up</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>

---  
@title[Build Errors]
<br>
<br>
<br>
<br>
##### <p align="center"<span class="gold"   >Build Errors</span></p><br>


---
@title[Build Error- RC.exe ]
<p align="right"><span class="gold" ><b>Build Error- RC.exe </b></span></p>
<p style="line-height:90%"><span style="font-size:0.9em" >Because RC.Exe is not found, Error Message:</span></p>

```
   "c:\Program Files (x86)\Windows Kits\8.0\bin\x64\rc.exe" 
/Foc:\edkii.svn\Build\NT32IA32\DEBUG_VS2013x86\IA32\MdeModulePkg\Application\HelloWorld\HelloWorld\OUTPUT
\HelloWorldhii.lib 
c:\edkii.svn\Build\NT32IA32\DEBUG_VS2013x86\IA32\MdeModulePkg\Application\HelloWorld\HelloWorld\OUTPUT\He
lloWorldhii.rc
'c:\Program' is not recognized as an internal or external command,
operable program or batch file.
 
NMAKE : fatal error U1077: '"c:\Program Files (x86)\Windows Kits\8.0\bin\x64\rc.exe' : return code '0x1'
Stop.

```

<p style="line-height:90%"><span style="font-size:0.9em" >Find where the RC.EXE is located on your VS Installation:  </span></p>

<p style="line-height:90%"><span style="font-size:0.9em" >Example (VS 2013):  The RC.exe is located on this machine: <br>
<span style="font-size:0.5em" >`C:\Program Files (x86)\Windows Kits\8.1\bin\x64` </span></span></p>
<span style="font-size:0.9em" >Edit `Conf/tools_def.txt` </span>

Note:


+++
@title[Build Error- RC.exe 02]
<p align="right"><span class="gold" ><b>Build Error- RC.exe Cont...</b></span></p>

<span style="font-size:0.9em" >Edit `Conf/tools_def.txt` </span><br>
<p style="line-height:90%"><span style="font-size:0.9em" >Search for your installation of Visual Studio (2013 or 2015)</span></p>
<p style="line-height:90%"><span style="font-size:0.9em" >Update according to the path for where the RC.EXE is found </span></p>

```
# Microsoft Visual Studio 2013 Professional Edition
DEFINE WINSDK8_BIN       = c:\Program Files\Windows Kits\8.1\bin\x86\
DEFINE WINSDK8x86_BIN    = c:\Program Files (x86)\Windows Kits\8.1\bin\x64
 
# Microsoft Visual Studio 2015 Professional Edition
DEFINE WINSDK81_BIN       = c:\Program Files\Windows Kits\8.1\bin\x86\
DEFINE WINSDK81x86_BIN    = c:\Program Files (x86)\Windows Kits\8.1\bin\x64

```


Note:
---
@title[Build Error- C1041 ]
<p align="right"><span class="gold" ><b>Build Error: fatal error C1041: </b></span></p>
<p style="line-height:90%"><span style="font-size:0.9em" >Build Error from fatal error C1041: cannot open program database</span></p>

<p style="line-height:90%"><span style="font-size:0.9em" >This Error is usually because the location you are building is being shared by another application in Windows.  Example: Syncplicity may cause this</span></p>

<span style="font-size:0.9em" >Error Message:</span>

```
k:\fw\edk2\MdePkg\Library\BaseLib\LinkedList.c : fatal error C1041: cannot open program 
database 
'k:\fw\edk2\build\nt32ia32\debug_vs2013x86\ia32\mdepkg\library\baselib\baselib\vc120.pdb'; if 
multiple CL.EXE write to the same .PDB file, please use /FS
NMAKE : fatal error U1077: '"C:\Program Files (x86)\Microsoft Visual Studio 
12.0\Vc\bin\cl.exe"' : return code '0x2'
Stop.

```

<p style="line-height:90%"><span style="font-size:0.9em" ><b>Solution:</b>  Try using a Workspace that is not shared
</span></p>


---?image=/assets/images/slides/Slide66.JPG
@title[Support for VS 2015 for MinnowBoard MAX]
### <p align="right"><span class="gold" >Support for VS 2015 for<br>MinnowBoard MAX</span></p>
 
Note:
- The Open Source Max release does not support VS 2015
- To work around do the following:
	- Copy the file 
	- “`..Max/edk2/conf/tools_def_VS2015x86.txt`” to 	“`..Max/edk2/conf/tools_def.txt`”
- Check out the differences:  
- There is a check for VS140COMNTOOLS and if defined setup for VS 2015
- See that tools_def.txt  replaces /Wx and /W4 with /w to turn off warnings as errors


---?image=/assets/images/slides/Slide67.JPG
@title[Visual Studio Resource Compiler Error – Rc.exe]
<p align="right"><span class="gold" >Visual Studio Resource Compiler Error – Rc.exe</span></p>
 
Note:
- The Rc.exe was not found and the build fails
- Find where rc.exe is located and update the  tools_def.txt

- Update `Max/edk2/conf/tools_def.txt`
<pre>
- # Microsoft Visual Studio 2013 Professional Edition
- DEFINE WINSDK8x86_BIN    = C:\Program Files (x86)\Windows Kits\8.1\bin\x64

- # Microsoft Visual Studio 2015 Professional Edition
- DEFINE WINSDK81x86_BIN   = C:\Program Files (x86)\Windows Kits\8.1\bin\x64

- # Microsoft Visual Studio 2017 Professional Edition
- DEFINE WINSDK10_BIN      =  Location of Rc.exe
</pre>


---?image=/assets/images/slides/Slide66.JPG
@title[Support for VS 2017 for MinnowBoard MAX]
### <p align="right"><span class="gold" >Support for VS 2017 for<br>MinnowBoard MAX</span></p>
 
Note:
- The Open Source Max release does not support VS 2017
- To work around do the following:
	- Copy the file 
	- “`..Max/edk2/conf/tools_def_VS2015x86.txt`” to 	“`..Max/edk2/conf/tools_def.txt`”
- Check out the differences:  
- See that tools_def.txt  replaces /Wx and /W4 with /w to turn off warnings as errors
-  At MS Command Prompt
  `>Set  TOOL_CHAIN_TAG=VS2010x86 `

