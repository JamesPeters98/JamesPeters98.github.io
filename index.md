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
