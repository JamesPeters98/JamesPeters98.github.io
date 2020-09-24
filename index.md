## Portfolio

### Projects
#### [Java](#java-projects)
* [Minecraft Spigot Plugin - Chests++](#minecraft-spigot-plugin---chests)
* [Master's Project - N-Body Simulations & Their Applications](#masters-project---n-body-simulations--their-applications)
* [Simulating B Meson Events in the LHCb](#simulating-b-meson-events-in-the-lhcb)
* [GameBoy (DMG) Emulator](#gameboy-dmg-emulator)
* [Custom CPU Assembler](#custom-cpu-assembler)
* [Hibernate - Football Simulator](#hibernate---football-simulator)

#### [Python](#python-projects)
* [Sequence Card Game](#sequence-card-game)
* [Python Stats Module](#python-stats-module)

#### [C/C++](#cc-projects)
* [Custom CPU/ROM Arduino](#custom-cpurom-using-arduino)

---

### Java Projects 

#### [Minecraft Spigot Plugin - Chests++](https://github.com/JamesPeters98/ChestsPlusPlus)

This is my largest personal project in Java, which makes use of the Bukkit/Spigot plugin api to create modifcations to the Minecraft server experience. The plugin is quite in depth and adds a range of features such as 'linking' Chests over infinite distances and worlds, filtering chests using Hoppers and Auto-Crafting - along with a range of other useful features.

<p align="center">
<img src="https://camo.githubusercontent.com/3ca42289c124bad4db92f273e1c057ff65ee247e/68747470733a2f2f692e696d6775722e636f6d2f543143713674382e706e67"/>
</p>

Some key points about this project include:

1. A custom Travis CI workflow - since some plugins require access to public methods in the Minecraft source code the plugin must be built against a decompiled Minecraft source, this source cannot be distributed and therefore must be decompiled directly on the CI server itself. To achieve this I had to modify the BuildTools project that is normal used to decompile the source code so that it would only decompile new source code if changes were detected in the git repo. This change was made in this [PR](https://hub.spigotmc.org/stash/projects/SPIGOT/repos/buildtools/commits/19d26b6581b57fdb0b75577c32fd525c4371860e).

2. Maven submodules - since each version of Minecraft adds/removes features from the game the plugin api and original Minecraft source code is changed. To be able to support multiple versions of Minecraft a submodule api is used to interface with the new or changed methods or the API or Minecraft source code. 

3. Pull Requests to the Spigot api - To help remove the amount of code that has to be changed for each version of Minecraft I made some PR's ([Here](https://hub.spigotmc.org/stash/projects/SPIGOT/repos/craftbukkit/commits/8fb65851f12f78c26ca979377370395e64c8a61f) and [here](https://hub.spigotmc.org/stash/projects/SPIGOT/repos/bukkit/commits/eeb1042f1ac356cc989dd1c4e35b37ee0ab93891)) to the Spigot API in order to achieve some features that I needed for my plugin, for instance it wasn't possible to set a Chest's animation state which was required due to the custom inventory implementation used.

---
#### [Master's Project - N-Body Simulations & Their Applications](https://github.com/JamesPeters98/Java-NBody-Simulation)

For my Thesis I created a gravitational N-Body simulator in Java. I implemented four different integrators of different orders: a 1st, 2nd and two 4th order - the Euler, Leapfrog, Yoshida and Runge-Kutta respectively. This project provided me with a platform to showcase my skills in Java academically and further developed them along with my problem solving and analytical skills. 

An aspect of this project I am particularly proud of is my derivation for the conditions of an eclipse, using vector geometry and trigonemetry. Along with the derivation for an estimation of the intensity of the eclipse too.

---
#### [Simulating B Meson Events in the LHCb](https://github.com/JamesPeters98/PHYS488-Project)

This was a group project in my 3rd year of my degree where the goal was to simulate the production and detection of B mesons in the LHCb detector. My role in the group was to implement an algorithm to fit straight lines in 3 dimensions, and then using those straight lines find the nearest point to the set of those lines - which turns out to be much more complicated than in 2 dimensions. I used a combination of Principal Component Analysis and a Least squares approach to fit the lines and then solve for a point P using Gaussian elimination.

I also implemented the 3D graphing library using Orson Charts to visualise our events and help debug our simulation:

<img src="https://i.imgur.com/ohexefc.gif"/>

For this project I'm particularly proud of how I implemented multithreading for the simulation which improved our performance compared to our peers. This meant we could produce much more data in a shorter timespan. My personal investigation using the simulation was on the effects of resolution on the detector.

This project demonstrated my ability to program with a team, which I took lead of and helped distribute the workload.After completing the project we presented our findings to a panel which required good verbal communication.

---
#### [GameBoy (DMG) Emulator](https://github.com/JamesPeters98/JavaGameboyEmulator)

I decided to start this project to learn more about low level computing as this was something I'm extremely interested about but something I hadn't dove into properly. The original Gameboy felt like a good place to start since it was familiar to me, it was 8 bit, and is one of the most well documented console. I chose Java for this project since at the time I was most familiar with it and starting a project as daunting as emulation I didn't want any bugs to be introduced due to silly mistakes within the language. (It turns out Java isn't great when dealing with emulation since it doesn't provide unsigned types, which can be a pain when debugging and dealing with bitwise operations.)

In it's current state I have managed to get the emulator to boot past the Bootrom and into the Tetris intro and menu!

<img src="https://raw.githubusercontent.com/JamesPeters98/JavaGameboyEmulator/master/images/GameBoyEmu.gif"/>

---
#### [Custom CPU Assembler](https://github.com/JamesPeters98/Custom-CPU)

After working on the Gameboy emulator I wanted to further explore assembly language and how it relates to the bare metal cpu. For this I decided to create a custom CPU and ROM using Arduino's (This is explained in my C++ section). I already had the opcode table and binary code working on the CPU so I decided to write an assembler in Java. The basics of the assembler was actually quite easy: first all comments and extra white space was removed, second the type of command was decided based on the tabbing of the code, and second the command matching was just a simple regex pattern. 

This enabled the following code to be compiled into raw binary data, and also as a C file containing a byte array:

<script src="https://gist-it.appspot.com/https://github.com/JamesPeters98/Custom-CPU/blob/master/Assembler/rom.asm"></script>

---
#### [Hibernate - Football Simulator](https://github.com/JamesPeters98/Hibernate-Football)

This is a personal project I decided to create to learn the Hibernate framework. It scrapes 18000 players and their stats and information and stores them in a database. It makes use of Java’s persistence API for object mapping. It makes use of the Hungarian algorithm to calculate every teams best formation and team sheet, and using this generates attack and defensive ratings. I also built a simple UI to run a simple league simulation and see the league table.

<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://www.youtube.com/embed/sa5dl1AiVEY' frameborder='0' allowfullscreen></iframe></div>
---
---

---
### Python Projects

#### [Sequence Card Game](https://github.com/JamesPeters98/Sequence-Card-Game)

This is a simple Python game using PyGame, it's an implementation of the sequence card game with a UI to play it. I plan to use reinforcement learning to develop an AI to play the game and eventually beat human players.

<img src="https://raw.githubusercontent.com/JamesPeters98/Sequence-Card-Game/master/image.png" />

#### [Python Stats Module](https://github.com/JamesPeters98/Stats-Workshops)

During my final year of my masters I completed a statistics course in Python, this involved multiple workshops completing various statistical analysis'. The course ended with a project that involved the fitting of curves with the use of 'scipy' and it's optimisation library. Calculating Chi^2 plots, residual plots and significance values. The goal of the project was to calculate the mass of the Higgs using the plot of counts vs energy.

The final report can be read [here](https://github.com/JamesPeters98/Stats-Workshops/blob/master/Mini-Project/Particle_Project.pdf)

---
---

### C/C++ Projects

#### [Custom CPU/ROM using Arduino](https://github.com/JamesPeters98/Custom-CPU)

I started this project to strength my skills in C++ as well as developing my knowledge of low level computing. It involves two arduinos, one acting as an EEPROM and the other as a CPU (It actually acts more like a SoC, combining the CPU, RAM, GPU and RAM). Both Arduinos were conneted to a common bus, that was just a breadboard containing LED's for the address and data pins. The cpu has an 8 bit design and currently has a 16KB address space.

The CPU has a basic opcode matrix that include methods for NOP, HALT, JUMPs, LOAD, STORE, CALL, RET, POP, PUSH, ADD, SUB, INC, DEC, AND, OR. And currently has Zero and Carry flags. I based it off a combination of the 6502 and the original Gameboy.

In it's current configuration using the rom built using the [Java based Assembler](#custom-cpu-assembler) it is able to output the following 'Hello World' program.

<img src="https://camo.githubusercontent.com/21e872b72579a8e73f984af1cea40c5d8591490f/68747470733a2f2f692e696d6775722e636f6d2f354157624772532e706e67" />


---
<p style="font-size:11px">Page template forked from <a href="https://github.com/evanca/quick-portfolio">evanca</a></p>
<!-- Remove above link if you don't want to attibute -->
