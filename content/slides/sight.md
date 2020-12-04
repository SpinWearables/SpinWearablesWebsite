---
title: Color Theory
keywords: color, light, electromagnetism, color theory, pigments, art
---


![Many bright minds of our civilization have studied the science behind colors in the pursuit of art.<a class="imagecredit" href="https://www.pikrepo.com/flrza/assorted-paint-kit">image credit Pikrepo</a>](/images/bookpics/assorted_paint_kit.jpg "image credit to Pikrepo")

::: notes

The premise of the presentation is to first 
describe how much of our tech does use only 3 colors
whether in screens or in print.

We explain that this is because our eyes
have only three color sensors. We do not
introduce the physical reality yet: we do not
say that there are other colors and we do not
say that there is difference between purple light
and a mixture of red and blue light. We do not go there
exactly because our eyes are not tools that can make
the distinction.

Then we play a bit with the SpinWheel and show
a simple program to change its colors.

Only then we go back to light and explain what
it is and that there is a very substantial
difference between purple and red+blue even if our
eyes can not see the difference.
We even mention the mantis shrimp.

The we talk about additional imperfections of our eyes
that we can exploit for cool effects, namely,
persistence of vision.

:::

# Perceiving Color

---

### Three main colors in our paint, our screens, and our eyes

![](/images/banners/colors_and_eye.png)

---

![An artistic rendering of a close-up of the back of the eye illustrating the rods (black) and cones (triangles colored by type). <a class="imagecredit" href="https://johnhegarty8.wixsite.com/johnhegarty">image credit Jack Hegarty</a>](/images/bookpics/rods_cones.png "Close-up cartoon of rods and cones in an eye")

---

![An up-close picture of a computer screen, showing the red, green, and blue light sources, making up the white background.<a class="imagecredit" href="https://commons.wikimedia.org/wiki/File:LCD_Pixels_Macro.jpg">image credit Wikimedia</a>](/images/bookpics/lcd_pixels_macro.jpg "An up-close picture of a computer screen, showing the red, green, and blue subpixels, making up the white background"){width=50%}

---

![The [halftone technique](https://en.wikipedia.org/wiki/Halftone) is a good example of this, where microscopic dots of different sizes and colors are used to make the illusion of a smooth color at a distance. <a class="imagecredit" href="https://en.wikipedia.org/wiki/File:Halftoningcolor.svg">image credit Wikimedia</a>](/images/bookpics/halftone.png "The halftone technique.")

---

### Additive (light-based) color mixing

A white ball illuminated by three colored lights of different brightness.

<style>
#acolortests {
  font-size: 2rem;
  text-align: left;
  background: white;
  padding: 2rem;
  color: black;
}
#acolortests .explain {
  font-size: 1rem;
  width: 80%;
  margin: 0 auto;
}
#acolortests input {
  width: 20%;
  margin: 0;
}
#acolortests span {
  display: inline-block;
  text-align: center;
  vertical-align: middle;
}
#acolortests .spacer {
  width:5%;
}
#acolortests .vis {
  width: 20%;
  height: 2em;
  line-height: 2em;
  border: solid 1px;
  border-color: black;
  color: white;
}
#aredshow {border-color: red !important;}
#agreenshow {border-color: green !important;}
#ablueshow {border-color: blue !important;}
#acolortests .svganim {
  text-align: center;
  width: 100%;
  margin: 0 auto;
}
</style>
<div id="acolortests">
<div><input type="range" min="0" max="255" value="255" id="ared"><span class="spacer"></span><input type="range" min="0" max="255" value="255" id="agreen"><span class="spacer"></span><input type="range" min="0" max="255" value="255" id="ablue"></div>
<div><span class="vis" id="aredshow">255</span><span class="spacer">+</span><span class="vis" id="agreenshow">255</span><span class="spacer">+</span><span class="vis" id="ablueshow">255</span><span class="spacer">=</span><span class="vis" id="argbshow">&nbsp;</span></div>
<div class="svganim">
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg" markdown=0> <filter id="alight"> <feDiffuseLighting id="asvgred" in="SourceGraphic" result="lightr" lighting-color="#f00" diffuseConstant="1.5"> <fePointLight x="50" y="150" z="80" /> <!--<feSpotLight x="15" y="20" z="40" limitingConeAngle="25" pointsAtX="50" pointsAtY="50" pointsAtZ="20"/>--> </feDiffuseLighting> <feDiffuseLighting id="asvggreen" in="SourceGraphic" result="lightg" lighting-color="#0f0" diffuseConstant="1.5"> <fePointLight x="100" y="30" z="80" /> <!--<feSpotLight x="100" y="-10" z="40" limitingConeAngle="25" pointsAtX="100" pointsAtY="60" pointsAtZ="0"/>--> </feDiffuseLighting> <feDiffuseLighting id="asvgblue" in="SourceGraphic" result="lightb" lighting-color="#00f" diffuseConstant="1.5"> <fePointLight x="150" y="150" z="80" /> <!--<feSpotLight x="185" y="20" z="40" limitingConeAngle="25" pointsAtX="150" pointsAtY="50" pointsAtZ="20"/>--> </feDiffuseLighting> <feComposite in="SourceGraphic" in2="lightr" result="sourceWithR" operator="arithmetic" k1="1" k2="0" k3="0" k4="0"/>    <feComposite in="SourceGraphic" in2="lightg" result="sourceWithG" operator="arithmetic" k1="1" k2="0" k3="0" k4="0"/>    <feComposite in="SourceGraphic" in2="lightb" result="sourceWithB" operator="arithmetic" k1="1" k2="0" k3="0" k4="0"/>    <feComposite in="sourceWithR" in2="sourceWithG" result="sourceWithRG" operator="arithmetic" k1="0" k2="1" k3="1" k4="0"/>    <feComposite in="sourceWithRG" in2="sourceWithB" result="sourceWithRGB" operator="arithmetic" k1="0" k2="1" k3="1" k4="0"/>    </filter> <circle cx="100" cy="100" r="80" fill="white" stroke="black" stroke-opacity="1" filter="url(#alight)" /> </svg>
</div>
<script>
function achangeColor(){
  var r = document.getElementById("ared").value;
  var g = document.getElementById("agreen").value;
  var b = document.getElementById("ablue").value;
  document.getElementById("argbshow").style["background-color"]=`rgb(${r},${g},${b})`;
  document.getElementById("aredshow").innerHTML=r;
  document.getElementById("aredshow").style["background-color"]=`rgb(${r},0,0)`;
  document.getElementById("asvgred").setAttribute("lighting-color",`rgb(${r},0,0)`);
  document.getElementById("agreenshow").innerHTML=g;
  document.getElementById("agreenshow").style["background-color"]=`rgb(0,${g},0)`;
  document.getElementById("asvggreen").setAttribute("lighting-color",`rgb(0,${g},0)`);
  document.getElementById("ablueshow").innerHTML=b;
  document.getElementById("ablueshow").style["background-color"]=`rgb(0,0,${b})`;
  document.getElementById("asvgblue").setAttribute("lighting-color",`rgb(0,0,${b})`);
}
document.getElementById("ared").oninput = achangeColor;
document.getElementById("agreen").oninput = achangeColor;
document.getElementById("ablue").oninput = achangeColor;
achangeColor();
</script>
</div>

---

### Subractive (pigment-based) color mixing

|Primary Pigment Color<br>(a.k.a. subtractive)  | Complemented by Primary Light Color<br>(a.k.a. additive)
|---    |---    
|Cyan<br>(absorbs red and reflects green and blue) | Red
|Magenta<br>(absorbs green and reflects red and blue) | Green
|Yellow<br>(absorbs blue and reflects red and green) | Blue

---

### Subractive (pigment-based) color mixing

Three color droplets overlapping on a white sheet of paper.

<style>
#scolortests {
  font-size: 2rem;
  background: white;
  color: black;
  text-align: left;
  padding: 2rem;
}
#scolortests input {
  width: 20%;
  margin: 0;
}
#scolortests span {
  display: inline-block;
  text-align: center;
  vertical-align: middle;
}
#scolortests .spacer {
  width:5%;
}
#scolortests .vis {
  width: 20%;
  height: 2em;
  line-height: 2em;
  border: solid 1px;
  border-color: black;
  color: black;
}
#sredshow {border-color: cyan !important;}
#sgreenshow {border-color: magenta !important;}
#sblueshow {border-color: yellow !important;}
#scolortests .svganim {
  text-align: center;
  width: 200px;
  height: 200px;
  margin: 0 auto;
  position: relative;
}
#scolortests .svganim > span {
  border-radius: 50%;
  width: 100px;
  height: 100px;
  position: absolute;
  mix-blend-mode: multiply;
}
#scolortests .svganim > #mblob {
  left: 50px;
  top: 30px;
  border-radius: 32% 58% 69% 43% / 48% 32% 59% 55%;
}
#scolortests .svganim > #cblob {
  left: 40px;
  top: 40px;
  border-radius: 38% 62% 63% 37% / 41% 44% 56% 59%;
}
#scolortests .svganim > #yblob {
  left: 60px;
  top: 40px;
  border-radius: 31% 45% 74% 35% / 38% 56% 51% 87%;
}
</style>
<div id="scolortests">
<div><input type="range" min="0" max="255" value="255" id="sred"><span class="spacer"></span><input type="range" min="0" max="255" value="255" id="sgreen"><span class="spacer"></span><input type="range" min="0" max="255" value="255" id="sblue"></div>
<div><span class="vis" id="sredshow">255</span><span class="spacer">+</span><span class="vis" id="sgreenshow">255</span><span class="spacer">+</span><span class="vis" id="sblueshow">255</span><span class="spacer">=</span><span class="vis" id="srgbshow">&nbsp;</span></div>
<div class="svganim"><span id="cblob"></span><span id="yblob"></span><span id="mblob"></span></div>
<script>
function schangeColor(){
  var complement_r = document.getElementById("sred").value;
  var complement_g = document.getElementById("sgreen").value;
  var complement_b = document.getElementById("sblue").value;
  document.getElementById("srgbshow").style["background-color"]=`rgb(${255-complement_r},${255-complement_g},${255-complement_b})`;
  document.getElementById("sredshow").innerHTML=complement_r;
  document.getElementById("sredshow").style["background-color"]=`rgb(${255-complement_r},255,255)`;
  document.getElementById("cblob").style["background-color"]=`rgb(${255-complement_r},255,255)`;
  document.getElementById("sgreenshow").innerHTML=complement_g;
  document.getElementById("sgreenshow").style["background-color"]=`rgb(255,${255-complement_g},255)`;
  document.getElementById("mblob").style["background-color"]=`rgb(255,${255-complement_g},255)`;
  document.getElementById("sblueshow").innerHTML=complement_b;
  document.getElementById("sblueshow").style["background-color"]=`rgb(255,255,${255-complement_b})`;
  document.getElementById("yblob").style["background-color"]=`rgb(255,255,${255-complement_b})`;
}
document.getElementById("sred").oninput = schangeColor;
document.getElementById("sgreen").oninput = schangeColor;
document.getElementById("sblue").oninput = schangeColor;
schangeColor();
</script>
</div>
 	  
---

![](/images/banners/colors_and_eye.png)

---

![An up-close picture of some of the SpinWheel's LEDs, showing the red, green, and blue subpixels.](/images/bookpics/LED_close-up.jpg "An up-close picture of five SpinWheel LEDs, showing the red, green, and blue subpixels.")

---

<link rel="stylesheet" href="/simspinwheel/simspinwheel.css">
<script src='/simspinwheel/simspinwheel.js'></script>
<div class="ssw-codecontent" markdown=0>
<pre class="ssw-codeblock">
void setup() {
  SpinWheel.begin();
}
void loop() {
</pre>
<textarea class="ssw-codeblock">
  SpinWheel.setLargeLEDsUniform(255, 255, 255);
</textarea>
<pre class="ssw-codeblock">
  SpinWheel.drawFrame();
}
</pre>
</div>

# Light is an Electromagnetic Wave

---

### Waves are traveling motion

A wave is a repetitive motion traveling through a medium. Some examples are shown in the table below.

|Type of Wave  |Medium
|---		|---
|Ocean wave     |Water
|Sound wave   	|Air
|Light   	|?

---

### Wavelength and Color

<style>
#wavewidget {
  text-align: center;
  background: white;
  color: black;
}
#wavewidget .vis {
  width: 40%;
  font-size: 2rem;
  height: 4rem;
  line-height: 4rem;
  border: solid 1px;
  border-color: black;
  display: block;
  margin: auto;
  text-shadow:
    -1px -1px 0 white,
    1px -1px 0  white,
    -1px 1px 0  white,
    1px 1px 0   white;
}
</style>
<div id="wavewidget">
<div>Pick a wavelength :</div>
<div>300nm <input style="width:60%;top:0.5rem;position:relative;" type="range" min="300" max="800" value="500" id="waveSlider"> 800nm</div>
<div><span class="vis"><span id="waveView"></span>nm</span></div>
<svg id="tagsvgwave" width="800" height="100" viewBox="0 0 800 100"> <defs> <path id="svgwave" fill=none stroke=black stroke-width="2" d="M0 50 C 40 90, 60 90, 100 50 C 140 10, 160 10, 200 50 C 240 90, 260 90, 300 50 C 340 10, 360 10, 400 50 C 440 90, 460 90, 500 50 C 540 10, 560 10, 600 50 C 640 90, 660 90, 700 50 C 740 10, 760 10, 800 50 C 840 90, 860 90, 900 50 C 940 10, 960 10, 1000 50 C 1040 90, 1060 90, 1100 50 C 1140 10, 1160 10, 1200 50 C 1240 90, 1260 90, 1300 50 C 1340 10, 1360 10, 1400 50 C 1440 90, 1460 90, 1500 50 C 1540 10, 1560 10, 1600 50 C 1640 90, 1660 90, 1700 50 C 1740 10, 1760 10, 1800 50 C 1840 90, 1860 90, 1900 50 C 1940 10, 1960 10, 2000 50 C 2040 90, 2060 90, 2100 50 C 2140 10, 2160 10, 2200 50 C 2240 90, 2260 90, 2300 50 C 2340 10, 2360 10, 2400 50 C 2440 90, 2460 90, 2500 50 C 2540 10, 2560 10, 2600 50 C 2640 90, 2660 90, 2700 50 C 2740 10, 2760 10, 2800 50 C 2840 90, 2860 90, 2900 50 C 2940 10, 2960 10, 3000 50 C 3040 90, 3060 90, 3100 50 C 3140 10, 3160 10, 3200 50 C 3240 90, 3260 90, 3300 50 C 3340 10, 3360 10, 3400 50 C 3440 90, 3460 90, 3500 50 C 3540 10, 3560 10, 3600 50 C 3640 90, 3660 90, 3700 50 C 3740 10, 3760 10, 3800 50 C 3840 90, 3860 90, 3900 50 C 3940 10, 3960 10, 4000 50 C 4040 90, 4060 90, 4100 50 C 4140 10, 4160 10, 4200 50 C 4240 90, 4260 90, 4300 50 C 4340 10, 4360 10, 4400 50 C 4440 90, 4460 90, 4500 50 C 4540 10, 4560 10, 4600 50 C 4640 90, 4660 90, 4700 50 C 4740 10, 4760 10, 4800 50 C 4840 90, 4860 90, 4900 50 C 4940 10, 4960 10, 5000 50 C 5040 90, 5060 90, 5100 50" /> </defs> <use xlink:href="#svgwave" x="0" y="0"> <animate attributeName="x" from="0" to="-200" dur="3s" repeatCount="indefinite"/> </use> </svg>
<script>
var waveSlider = document.getElementById('waveSlider');
var waveView = document.getElementById('waveView');
var waveSVG = document.querySelector("#svgwave");
var waveSVGtag = document.querySelector("#tagsvgwave");
var waveAnim = document.querySelector("#wavewidget animate");
var waveVis = document.querySelector("#wavewidget .vis");
// From Spectra Lab Report
function waveLengthToRGB(Wavelength){
    var Gamma = 0.80;
    var IntensityMax = 255;
    var factor;
    var Red,Green,Blue;
    if((Wavelength >= 380) && (Wavelength<440)){
        Red = -(Wavelength - 440) / (440 - 380);
        Green = 0.0;
        Blue = 1.0;
    }else if((Wavelength >= 440) && (Wavelength<490)){
        Red = 0.0;
        Green = (Wavelength - 440) / (490 - 440);
        Blue = 1.0;
    }else if((Wavelength >= 490) && (Wavelength<510)){
        Red = 0.0;
        Green = 1.0;
        Blue = -(Wavelength - 510) / (510 - 490);
    }else if((Wavelength >= 510) && (Wavelength<580)){
        Red = (Wavelength - 510) / (580 - 510);
        Green = 1.0;
        Blue = 0.0;
    }else if((Wavelength >= 580) && (Wavelength<645)){
        Red = 1.0;
        Green = -(Wavelength - 645) / (645 - 580);
        Blue = 0.0;
    }else if((Wavelength >= 645) && (Wavelength<781)){
        Red = 1.0;
        Green = 0.0;
        Blue = 0.0;
    }else{
        Red = 0.0;
        Green = 0.0;
        Blue = 0.0;
    };
    // Let the intensity fall off near the vision limits
    if((Wavelength >= 380) && (Wavelength<420)){
        factor = 0.3 + 0.7*(Wavelength - 380) / (420 - 380);
    }else if((Wavelength >= 420) && (Wavelength<701)){
        factor = 1.0;
    }else if((Wavelength >= 701) && (Wavelength<781)){
        factor = 0.3 + 0.7*(780 - Wavelength) / (780 - 700);
    }else{
        factor = 0.0;
    };
    // Don't want 0^x = 1 for x <> 0
    var r = Red==0.0 ? 0 : Math.round(IntensityMax * Math.pow(Red * factor, Gamma));
    var g = Green==0.0 ? 0 : Math.round(IntensityMax * Math.pow(Green * factor, Gamma));
    var b = Blue==0.0 ? 0 : Math.round(IntensityMax * Math.pow(Blue * factor, Gamma));
    return [r,g,b];
}
function waveUpdate() {
  var t = waveSlider.value;
  waveView.innerHTML = t;
  var s = t/800;
  waveSVG.style.transform = `scale(${s},1)`;
  // XXX an attempt to make it work in Safari, otherwise not needed
  waveSVGtag.style.display='inline-block';
  console.log(waveSVGtag.offsetHeight); // no need to store this anywhere, the reference is enough
  waveSVGtag.style.display=''; 
  // XXX end workaround
  waveAnim.setAttribute("to", `${-200*s}`);
  waveAnim.setAttribute("dur",`${3*s}s`);
  var rgb = waveLengthToRGB(t);
  waveVis.style["background-color"]=`rgb(${rgb[0]},${rgb[1]},${rgb[2]})`;
}
waveSlider.oninput = waveUpdate;
var totalsamples = 400;
waveUpdate();
</script>

</div>

---

![The Electromagnetic Spectrum, only a small portion of which is visible to our eyes. <a class="imagecredit" href="https://commons.wikimedia.org/wiki/File:EM_spectrumrevised.png">image credit Wikimedia</a>](/images/bookpics/EM_spectrum.png "The Electromagnetic Spectrum"){style="width:100%;max-width:100%"}


---

![White light being split into colors by a prism. The white light shines on the prism from the bottom left, and a big part of it is refracted and split as it passes through the prism. <a class="imagecredit" href="https://www.pexels.com/photo/optical-glass-triangular-prism-3845161/">image credit Pexels</a>](/images/bookpics/optical_glass_triangular_prism.jpg "Picture of a white light being split into colors by a prism")

---

![An artistic rendering of a close-up of the back of the eye illustrating the rods (black) and cones (triangles colored by type). <a class="imagecredit" href="https://johnhegarty8.wixsite.com/johnhegarty">image credit Jack Hegarty</a>](/images/bookpics/rods_cones.png "Close-up cartoon of rods and cones in an eye")

---

<iframe src="https://theoatmeal.com/comics/mantis_shrimp" style="width:80%;height:50vh;"></iframe>

The Oatmeal comics has a story about the mantis shrimp: an animal that can distinguish 12 different base colors.

# Other limitations of our Eyes

---

### Persistence of vision

<p style="color:red;font-size:0.7em;">Warning: This demo involves rapidly flashing bright colors.</p>

<style>
#povtests {
  background: white;
  color: black;
  padding: 2rem;
  font-size: 2rem;
  text-shadow:
    -1px -1px 0 white,
    1px -1px 0  white,
    -1px 1px 0  white,
    1px 1px 0   white;
}
#povtests input {
  width: 30%;
  margin: 0;
}
#povtests span {
  display: inline-block;
  text-align: center;
  vertical-align: middle;
}
#povtests .vis {
  width: 30%;
  height: 2em;
  line-height: 2em;
}
#povshow {
  background-color: red;
  animation-name: flicker;
  animation-duration: 1s;
  animation-iteration-count: infinite;
  animation-timing-function: step-start;
  animation-play-state: paused;
}
@keyframes flicker {
  0%   {background-color: red;}
  50% {background-color: blue;}
}
</style>
<div id="povtests">
<div><input type="range" min="80" max="2000" value="1000" id="time"><span class="vis" id="timeshow"></span><span class="vis" id="povshow">&nbsp;</span></div>
<button id="start">Start</button>
<button id="stop">Stop</button>
<script>
var t = document.getElementById("time").value;
var squarestyle = document.getElementById("povshow").style;
function getT(){
  t = document.getElementById("time").value;
  document.getElementById("timeshow").innerHTML = `${t}ms`;
  squarestyle["animation-duration"] = `${t/1000}s`;
}
function startCycle(){
  squarestyle["animation-play-state"]="running";
}
function stopCycle(){
  squarestyle["animation-play-state"]="paused";
}
document.getElementById("time").oninput = getT;
document.getElementById("start").onclick = startCycle;
document.getElementById("stop").onclick = stopCycle;
getT();
</script>
</div>

Pick the frequency at which the rectangle will change colors from blue to red and back.

---

### Implemented on the SpinWheel

```cpp
// BE CAREFUL IF YOU HAVE EPILEPSY AS THIS WILL CAUSE FLASHING COLORS!!!
#include "SpinWearables.h"
using namespace SpinWearables;

void setup() {
  // Initialize all of the hardware on the SpinWheel.
  SpinWheel.begin();
}

// BE CAREFUL IF YOU HAVE EPILEPSY AS THIS WILL CAUSE FLASHING COLORS!!!
// Change this value! Experiment!
int delay_time_in_milliseconds = 500;

void loop() {
  // Show red...
  SpinWheel.setLargeLEDsUniform(255, 0, 0);
  SpinWheel.drawFrame();
  // Wait...
  delay(delay_time_in_milliseconds);
  // Show blue...
  SpinWheel.setLargeLEDsUniform(0, 0, 255);
  SpinWheel.drawFrame();
  // Wait...
  delay(delay_time_in_milliseconds);  
}
```

---

![If you move the SpinWheel rapidly in front of your eyes, you will see the purple color separate in two distinct streaks of red and blue.](/images/bookpics/fast_pov_streak.jpg "Picture of a fast-moving SpinWheel")

---

![Understanding the interplay between color and light enables  
the creation of wondrous technology and art. <a class="imagecredit" href="https://www.pikrepo.com/fqyvu/multicolored-strobe-lights">image credit Pikrepo</a>](/images/bookpics/disco_lights.jpg)

# Suggested lessons and activities

---

TODO
