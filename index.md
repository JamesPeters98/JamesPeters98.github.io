## Portfolio

---

### Java Projects 

[Minecraft Spigot Plugin - Chests++](https://github.com/JamesPeters98/ChestsPlusPlus)

This is my largest personal project in Java, which makes use of the Bukkit/Spigot plugin api to create modifcations to the Minecraft server experience. The plugin is quite in depth and adds a range of features such as 'linking' Chests over infinite distances and worlds, filtering chests using Hoppers and Auto-Crafting - along with a range of other useful features.

<p align="center">
<img src="https://camo.githubusercontent.com/3ca42289c124bad4db92f273e1c057ff65ee247e/68747470733a2f2f692e696d6775722e636f6d2f543143713674382e706e67"/>
</p>

Some key points about this project include:

1. A custom Travis CI workflow - since some plugins require access to public methods in the Minecraft source code the plugin must be built against a decompiled Minecraft source, this source cannot be distributed and therefore must be decompiled directly on the CI server itself. To achieve this I had to modify the BuildTools project that is normal used to decompile the source code so that it would only decompile new source code if changes were detected in the git repo. This change was made in this [PR](https://hub.spigotmc.org/stash/projects/SPIGOT/repos/buildtools/commits/19d26b6581b57fdb0b75577c32fd525c4371860e).

2. Maven submodules - since each version of Minecraft adds/removes features from the game the plugin api and original Minecraft source code is changed. To be able to support multiple versions of Minecraft a submodule api is used to interface with the new or changed methods or the API or Minecraft source code. 

3. Pull Requests to the Spigot api - To help remove the amount of code that has to be changed for each version of Minecraft I made some PR's ([Here](https://hub.spigotmc.org/stash/projects/SPIGOT/repos/craftbukkit/commits/8fb65851f12f78c26ca979377370395e64c8a61f) and [here](https://hub.spigotmc.org/stash/projects/SPIGOT/repos/bukkit/commits/eeb1042f1ac356cc989dd1c4e35b37ee0ab93891)) to the Spigot API in order to achieve some features that I needed for my plugin, for instance it wasn't possible to set a Chest's animation state which was required due to the custom inventory implementation used.

---
[Master's Project - N-Body Simulations & Their Applications](https://github.com/JamesPeters98/Java-NBody-Simulation)

For my Thesis I created a gravitational N-Body simulator in Java. I implemented four different integrators of different orders: a 1st, 2nd and two 4th order - the Euler, Leapfrog, Yoshida and Runge-Kutta respectively. This project provided me with a platform to showcase my skills in Java academically and further developed them along with my problem solving and analytical skills. 

An aspect of this project I am particularly proud of is my derivation for the conditions of an eclipse, using vector geometry and trigonemetry. Along with the derivation for an estimation of the intensity of the eclipse too.

---
[Simulating B Meson Events in the LHCb](https://github.com/JamesPeters98/PHYS488-Project)

This was a group project in my 3rd year of my degree where the goal was to simulate the production and detection of B mesons in the LHCb detector. My role in the group was to implement an algorithm to fit straight lines in 3 dimensions, and then using those straight lines find the nearest point to the set of those lines - which turns out to be much more complicated than in 2 dimensions. I used a combination of Principal Component Analysis and a Least squares approach to fit the lines and then solve for a point P using Gaussian elimination.

I also implemented the 3D graphing library using Orson Charts to visualise our events and help debug our simulation:

<img src="https://i.imgur.com/ohexefc.gif"/>

For this project I'm particularly proud of how I implemented multithreading for the simulation which improved our performance compared to our peers. This meant we could produce much more data in a shorter timespan. My personal investigation using the simulation was on the effects of resolution on the detector.

This project demonstrated my ability to program with a team, which I took lead of and helped distribute the workload.After completing the project we presented our findings to a panel which required good verbal communication.

---
[GameBoy (DMG) Emulator](https://github.com/JamesPeters98/JavaGameboyEmulator)

I decided to start this project to learn more about low level computing as this was something I'm extremely interested about but something I hadn't dove into properly. The original Gameboy felt like a good place to start since it was familiar to me, it was 8 bit, and is one of the most well documented console. I chose Java for this project since at the time I was most familiar with it and starting a project as daunting as emulation I didn't want any bugs to be introduced due to silly mistakes within the language. (It turns out Java isn't great when dealing with emulation since it doesn't provide unsigned types, which can be a pain when debugging and dealing with bitwise operations.)

In it's current state I have managed to get the emulator to boot past the Bootrom and into the Tetris intro and menu!

<img src="https://raw.githubusercontent.com/JamesPeters98/JavaGameboyEmulator/master/images/GameBoyEmu.gif"/>

---
[Custom CPU Assembler](https://github.com/JamesPeters98/JavaGameboyEmulator)

After working on the Gameboy emulator I wanted to further explore assembly language and how it relates to the bare metal cpu. For this I decided to create a custom CPU and ROM using Arduino's (This is explained in my C++ section). I already had the opcode table and binary code working on the CPU so I decided to write an assembler in Java. The basics of the assembler was actually quite easy: first all comments and extra white space was removed, second the type of command was decided based on the tabbing of the code, and second the command matching was just a simple regex pattern. 

This enabled the following code to be compiled into raw binary data:
<details><summary>Rom.asm</summary>
<p>
  
```asm
; This is a test comment!

VRAM = $401 ; Start of line 0 on LCD.
STRING = hello-world

VALUE = $0F00 ; Start of RAM - 2 bytes long
VALUE_2 = $0F01 ; Second byte of value - 2 bytes long

MOD10 = $0F02 ; 2 bytes long
MOD10_2 = $0F03 ; 2 bytes long

.start:
    LOAD r0 #$00        ; This loads 0 into register 0.
    LOAD r1 #%10000000  ; This loads 80 into register 1.
    STORE r0 $400       ; This loads 0 into the display register
    PUSH r1             ; Pushes value of register 1 onto the stack.

    ;; PRINT STRING
    LOAD r2 #$00        ; This stores 0 into register 2. This is the starting position on the LCD.
    LOAD r16,STRING     ; Load address for start of string into 16bit register.
    CALL print_string   ; jump to subroutine to print string.

    ;; PRINT STRING
    LOAD r2 #40                 ; This stores 40 into register 2. This is the second line on the LCD.
    LOAD r16,second-line        ; Load address for start of string into 16bit register.
    CALL print_string           ; jump to subroutine to print string.

    ;; Call LCD update
    POP r1              ; Pops the value stored on the stack into register 1.
    STORE r1 $400       ; This pushes %10000000 to 0x400 to tell the CPU to push VRAM to the display.

    ;; Convert number to decimal
    LOAD r16,number         ; Loads number into register
    ;CALL convert_number     ; Calls convert number function

end:
    HALT

print_string:
    ; This section writes each character to VRAM which is located at 0x401 -> 0x450 (80 bytes - 40 bytes per line.) only 16 bytes visible per line.
    LOAD r0,r16         ; Loads character from String into register 0.
    RET Z               ; Jump if Loaded a Zero (End of String)
    STORE VRAM,r2       ; Stores character into VRAM.
    INC r16             ; Increment register r16 to select next character.
    INC r2              ; Increment position in VRAM.
    JMP print_string    ; loop until reach null termination character.

convert_number:
    LOAD r0,r16
    STORE r0 VALUE
    INC r16
    STORE r0 VALUE_2

    LOAD r0 #0
    STORE r0 MOD10
    STORE r0 MOD10_2

    ; Rotates the byte
    ROL VALUE
    ROL VALUE_2
    ROL MOD10
    ROL MOD10_2

;; Strings
hello-world:
    String "Hello James!" ; This creates a null-terminated ASCII String.

second-line:
    String "Test String!" ;

number:
    .word 1234
```

</p>
</details>

---

### Category Name 2

- [Project 1 Title](http://example.com/)
- [Project 2 Title](http://example.com/)
- [Project 3 Title](http://example.com/)
- [Project 4 Title](http://example.com/)
- [Project 5 Title](http://example.com/)

---




---
<p style="font-size:11px">Page template forked from <a href="https://github.com/evanca/quick-portfolio">evanca</a></p>
<!-- Remove above link if you don't want to attibute -->
