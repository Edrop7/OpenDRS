<h1 align="center">
  <br>
  <a href="http://www.amitmerchant.com/electron-markdownify"><img src="https://raw.githubusercontent.com/Edrop7/OpenDRS/master/Git-Resources/teamsecretformulalogo.png" alt="Senior capstone team logo" width="10%" height="10%"></a>
  <br>
  OpenDRS
  <br>
</h1>

<h4 align="center">A public domain active aero rear wing package for <a href="https://www.fsaeonline.com/" target="_blank">FSAE</a>.</h4>
<!--
<p align="center">
  <a href="https://badge.fury.io/js/electron-markdownify">
    <img src="https://badge.fury.io/js/electron-markdownify.svg"
         alt="Gitter">
  </a>
  <a href="https://gitter.im/amitmerchant1990/electron-markdownify"><img src="https://badges.gitter.im/amitmerchant1990/electron-markdownify.svg"></a>
  <a href="https://saythanks.io/to/bullredeyes@gmail.com">
      <img src="https://img.shields.io/badge/SayThanks.io-%E2%98%BC-1EAEDB.svg">
  </a>
  <a href="https://www.paypal.me/AmitMerchant">
    <img src="https://img.shields.io/badge/$-donate-ff69b4.svg?maxAge=2592000&amp;style=flat">
  </a>
</p>
-->

<p align="center">
  <a href="#About-This-Project">About This Project</a> •
  <a href="#External-Software-Needed">External Software Needed</a> •
  <a href="#Overview">Overview</a> •
  <a href="#credits">Credits</a> •
  <a href="#related">Related</a> •
  <a href="#license">License</a>
</p>

<p align="center">
    <img src="https://raw.githubusercontent.com/Edrop7/OpenDRS/master/Git-Resources/OpenDRSmove.gif" width="150%" height="150%">
</p>

## About This Project

**Background:**

This repository contains the documentation of the work done by 4 FIU B.S. Mechanical Engineering students for their senior capstone project in 2023-2024. They were supporting the FIU FSAE competition team (Panther Motorsports) to implement a rear wing active aero package design ideated to improve race performance in the dynamic portion of the Michigan speedway track events in 2024.

**Novel intellectual property generated for FSAE teams:**
* A comprehensive benchmarked design architecture with use instructions and a report
* Validation of CFD simulation methodology
* Validation of ANSYS composites toolbox methodology for structural components
* Methodology for judging the cost vs benefit of potential future work
* A script to benchmark new active aero packages using OptimumLap

**Critical project targets were:**
* a 5% reduction in lap time
* a cost under $5000
* safety factors above 1.2
* following FSAE rules/regulations to avoid DQ



## External Software Needed

To view, experiment with, or modify the files in this repository, you'll need the following software
* [OptimumLap](https://optimumg.com/product/optimumlap/)
* [MATLAB](https://www.mathworks.com/products/matlab/student.html)
* [ANSYS](https://www.ansys.com/academic/students) 
* [SimScale](https://www.simscale.com/academic-program/)
* [Arduino IDE](https://www.arduino.cc/en/software)

Additionally, to access and edit the design architecture provided, the CAD software [SolidWorks 2022](https://www.solidworks.com/product/students) is needed to view our native design files. [Fusion 360](https://www.autodesk.com/campaigns/education/fusion-360) is a free (for students) alternative to view and edit history-less STEP files for free. 

Our team used free student versions of all of the software listed above provided by the Florida International University Mechanical and Materials Engineering department.



<!--
```bash
# Clone this repository
$ git clone https://github.com/amitmerchant1990/electron-markdownify

# Go into the repository
$ cd electron-markdownify

# Install dependencies
$ npm install

# Run the app
$ npm start
```

> **Note**
> If you're using Linux Bash for Windows, [see this guide](https://www.howtogeek.com/261575/how-to-run-graphical-linux-desktop-applications-from-windows-10s-bash-shell/) or use `node` from the command prompt.
-->


## Overview

**What is OptimumLap**

OptimumLap is a free point-based numerical laptime simulator commonly used in motorsport to identify the estimated best case performance of a vehicle driving on a track. Many FSAE teams use it to benchmark the expected performance of their designs and optimize their design through data-driven decision making.


Within OptimumLap, FSAE teams upload critical vehicle data such as
* Vehicle mass
* Aerodynamic data
* Tire data
* Engine data
* Transmission data

This data is primarily sourced from suppliers of Commercial-off-the-shelf components (such as tires or engines), as well as CAD and CAE simulations.

<p align="center">
    <img src="https://raw.githubusercontent.com/Edrop7/OpenDRS/master/Git-Resources/FSAEOptimumLap.PNG">
</p>

With this data, OptimumLap can create different plots and visualizations of kinematic performance data of a vehicle across a racetrack. It can also compare different vehicle configurations within the same visualizations, as demonstrated below with a speed vs elapsed distance plot and track heat map.

<p align="center">
    <img src="https://raw.githubusercontent.com/Edrop7/OpenDRS/master/Git-Resources/SpeedVsElapsedDistance.PNG">
</p>
<p align="center">
    <img src="https://raw.githubusercontent.com/Edrop7/OpenDRS/master/Git-Resources/OptimumLap-Track.PNG">
</p>

**What is wrong with OptimumLap?**

OptimumLap currently does not support active aerodynamic packages. When setting up the vehicle with all of the data, critical values that change due to making use of an active aero package (such as drag coefficients and frontal area) are treated as constant, as most teams make use of a static aero package.

**What is in our MATLAB script**

To solve the problem with OptimumLap, our team created a MATLAB script that takes in exported kinematic data from OptimumLap and solves for the expected final lap time of a vehicle making use of active aero. The fully deployed and fully retracted configurations of the active aero package are setup and simulated as static vehicles through OptimumLap to obtain acceleration data for how they would perform in different sections of the track, and this data is used to produce a new dataset where the deployment and retraction of active aero is considered (making use of the best accelerations and decelerations).

This allows our team to both benchmark different designs for the critical project metric (laptime saved), as well as to probe for data guiding our design, such as the target coefficient of drag value in order to achieve the desired laptime reduction. More information on how to make use of this benchmarking tool is found within the benchmarking folder within this repository.

The data below is for the FIU Panther Motorsports FSAE vehicle for 2024. It may be helpful to other teams, but it is worth noting that this data does not translate equally to all FSAE vehicles. This data is based on the panther motorport competition vehicle only, and it is recommended for other teams to create their own OptimumLap configurations and use our MATLAB benchmarking tools to identify their own plots for expected performance, though this data may be used to make approximations for adoption of this project

<p align="center">
    <img src="https://raw.githubusercontent.com/Edrop7/OpenDRS/master/Git-Resources/LaptimeVsCd.PNG">
</p>



<!--
You can [download](https://github.com/amitmerchant1990/electron-markdownify/releases/tag/v1.2.0) the latest installable version of Markdownify for Windows, macOS and Linux.
-->
## Contact Us
<!--
Markdownify is an [emailware](https://en.wiktionary.org/wiki/emailware). Meaning, if you liked using this app or it has helped you in any way, I'd like you send me an email at <bullredeyes@gmail.com> about anything you'd want to say about this software. I'd really appreciate it!
-->
## Credits
<!--
This software uses the following open source packages:

- [Electron](http://electron.atom.io/)
- [Node.js](https://nodejs.org/)
- [Marked - a markdown parser](https://github.com/chjj/marked)
- [showdown](http://showdownjs.github.io/showdown/)
- [CodeMirror](http://codemirror.net/)
- Emojis are taken from [here](https://github.com/arvida/emoji-cheat-sheet.com)
- [highlight.js](https://highlightjs.org/)
-->
## Related
<!--
[markdownify-web](https://github.com/amitmerchant1990/markdownify-web) - Web version of Markdownify
-->
## Support
<!--
<a href="https://www.buymeacoffee.com/5Zn8Xh3l9" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/purple_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

<p>Or</p> 

<a href="https://www.patreon.com/amitmerchant">
	<img src="https://c5.patreon.com/external/logo/become_a_patron_button@2x.png" width="160">
</a>
-->
## You may also like...
<!--
- [Pomolectron](https://github.com/amitmerchant1990/pomolectron) - A pomodoro app
- [Correo](https://github.com/amitmerchant1990/correo) - A menubar/taskbar Gmail App for Windows and macOS
-->
## License

Public Domain

---
<!--

> [amitmerchant.com](https://www.amitmerchant.com) &nbsp;&middot;&nbsp;
> GitHub [@amitmerchant1990](https://github.com/amitmerchant1990) &nbsp;&middot;&nbsp;
> Twitter [@amit_merchant](https://twitter.com/amit_merchant)
-->
