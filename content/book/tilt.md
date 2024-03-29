---
title: Making a Tilt Sensor
keywords: tilt sensor, gravitation, motion, acceleration
---

::: intro-box
The motion sensor in the SpinWheel can be used to detect the direction of gravity,
which in turn can be visualized, creating a colorful digital level or tilt sensor.
In this adventure, we'll cover one way to make a tilt sensor, which will also introduce vectors in a new way.
:::

## Simple Levels

On our planet, what is horizontal and what is vertical
is defined with respect to the direction of Earth's gravitational pull.
This makes it easy to measure how level a surface is
by observing whether gravity can pull something off the surface. For example, what happens if you put a ball on a table that is not level? The ball will roll off and fall to the ground.
One can even use a toy like a [ball-in-a-maze puzzle](https://en.wikipedia.org/wiki/Ball-in-a-maze_puzzle) as a simple tilt sensor.

![A toy in which the tilt can force a ball to roll in a given direction. <a class="imagecredit" href="https://commons.wikimedia.org/wiki/File:Round_maze.jpg">image credit Wikimedia</a>](/images/bookpics/round_maze.jpg)

More commonly, to check whether a surface is level or not, an actual [bubble level](https://en.wikipedia.org/wiki/Spirit_level) is used. You may have tried using one when hanging pictures or other decorations on a wall! 

To understand how a bubble level works, imagine what would happen if you took a glass of water and placed it on a table. If the table was perfectly horizontal, you would see the surface of the water in the glass appears horizontal too. What if the table has two legs that are slightly shorter than the others? Then, you might notice the surface of water in the glass appears tilted. You observe this tilt in the surface of the water because the surface is trying to remain perpendicular to gravity. 

Now, what happens if you replace your water with soda? On the tilted table, you should observe the surface of the soda in the glass shifts to remain parallel to the ground, and the bubbles in your soda still rise straight up (perpindicular to the soda's surface, but not to the bottom of the glass). Try this out and see what happens! The bubbles in your soda are made of gas (carbon dioxide in this case), and since carbon dioxide gas is less dense than your liquid soda, the gas bubbles rise to the top of the liquid soda. 

<figure><img src="/images/bookpics/level_and_glass.png" style="max-width:90%"><figcaption>Bubbles rise against gravity, both in the cylinder of the level and in a glass of carbonated water.<a class="imagecredit" href="https://monochra.com/">image credit Mariya Krastanova</a></figcaption></figure>

In a real bubble level, 
a small bubble is enclosed in a container with liquid surrounding it. 
The bubble tries to go as far up in its enclosure as possible, since the bubble is made of air and air is lighter than the surrounding liquid. This means that the bubble will rise against the direction of gravity (just think of what happened to bubbles in your soda glass). You can see this illustrated in the picture above where the bubble in the level on the tilted table rises to the highest point (to the right). 

The top of the bubble level enclosure is slightly domed. This means that
if the surface you've placed the level on is flat, the highest point in the bubble level enclosure is the center
of level and the bubble will move there (since the bubble is trying to rise as far up as it can).
If the surface is not flat, the bubble will still rise to the highest point in the enclosure, but the bubble will not be centered in this case. 

<!-- Could we maybe add some images of examples with a level and not level surface, showing what the bubble level looks like in each case? Also maybe a close up of the domed shape? Video of bubble level?
-->

![A bubble level. <a class="imagecredit" href="https://publiclab.org/notes/mathew/10-26-2015/deploying-passive-particle-monitors">image credit Public Lab</a>](/images/bookpics/onebubble.jpg)

We can program the SpinWheel to act as a level.
The SpinWheel contains a motion sensor, which is capable of measuring acceleration.
Because the sensation of accelerating cannot be distinguished
from the sensation of being pulled by gravity, 
this same sensor also reports Earth's gravity.

Before jumping into the rest of this adventure, upload the tilt sensor code from [`Examples → SpinWearables → Tilt_Sensor →  Simple`](/codedoc/examples/Tilt_Sensor/Simple/Simple.ino.html), and see how the LEDs respond to the tilt of the SpinWheel!

<figure><video src="/images/bookpics/preloaded_tilt3.mp4" muted autoplay playsinline loop></video><figcaption>   </figcaption></figure>

::: further-reading
The indistinguishability of gravity and acceleration is a fascinating topic
that has puzzled scientists and physics students for centuries.
It even inspired Einstein to work on his general theory of relativity!
You can learn more about it in our lesson on inertia and free fall.
:::


## Measuring Gravity in Two Dimensions

We can use the SpinWheel's acceleration sensor to measure the direction of gravity with respect to the surface of the SpinWheel, which gives us the tilt of that surface.
However we cannot use one single number to describe tilt, because we need both information about its left/right tilt and its forward/backward tilt.
For instance, notice how in the bubble level above,
both the direction in which the bubble has been displaced
and the distance between the bubble and the center of the dome give information
about the tilt of the surface. 
If a surface is more tilted, the bubble will move farther from the center, for instance.

Other types of bubble levels show the left/right vs forward/backward tilt more directly.
Notice how in the level shown below, we are using two separate tubes that are
perpendicular to each other,
instead of one single dome.
Now we can use one number per bubble,
simply denoting its displacement away from the middle of its tube.
These two numbers together contain all the information about the tilt of the surface.
We just described a <span class="footnote">position in the two-dimensional plane<span>Something that cannot be expressed by a single number.</span></span>,
by using a <span class=footnote>pair of numbers<span>Each giving the displacements along a single axis.</span></span>.
Mathematicians call this operation [vector decomposition](/vectors).

![A bubble level with separate sensors for each axis of tilt. <a class="imagecredit" href="https://publiclab.org/notes/mathew/10-26-2015/deploying-passive-particle-monitors">image credit Public Lab</a>](/images/bookpics/twobubble.jpg)

You can gain some more intuition about using *two* numbers to represent a position in a 2D plane below. 
Imagine that the bubble from the domed tilt sensor is at the end of the black arrow. 
The arrow gives the position of the bubble relative to the center of the dome, which depends on its tilt. 
This arrow is <span class="footnote">the two-dimensional object<span>Having both length and direction in a 2D plane.</span></span>
that we want to represent by splitting it in a component along the <span style="color:#228e2c;">$x$ axis</span>
and a component along the <span style="color:#2676b3;">$y$ axis</span>. The black arrow is called a vector.
We also depict two tube bubble levels acting as left/right and forward/backward tilt sensors.


<style>
#grid2d {
  text-align: center;
}
.grid2dcontrol > input {
  width: 40px;
}
.xcom {
  color: #228e2c;
}
.ycom {
  color: #2676b3;
}
</style>

<div id= "grid2d">
<div id="vectorGrid">
<canvas class="trajectory1D" width=400 height=400></canvas>
</div>
<div id="values">
<div class="grid2dcontrol xcom">X component: <span id="xshow">0</span></div>
<div><input type="range" min="-6" max="6"  id="xvalue"></div>
<div class="grid2dcontrol ycom">Y component: <span id="yshow">0</span></div>
<div><input type="range" min="-6" max="6"  id="yvalue"></div>
<div class="grid2dcontrol">Magnitude: <span id="magshow">0</span></div>
<!--<div class="grid2dcontrol">Angle: <span id="angshow">0</span>&deg;</div>-->
</div>
</div>

<script>
function canvas_arrow(context, fromx, fromy, tox, toy) {
  var headlen = 10;
  var dx = tox - fromx;
  var dy = toy - fromy;
  var angle = Math.atan2(dy, dx);
  context.moveTo(fromx, fromy);
  context.lineTo(tox, toy);
  context.lineTo(tox - headlen * Math.cos(angle - Math.PI / 6), toy - headlen * Math.sin(angle - Math.PI / 6));
  context.moveTo(tox, toy);
  context.lineTo(tox - headlen * Math.cos(angle + Math.PI / 6), toy - headlen * Math.sin(angle + Math.PI / 6));
}

const level_tube_img = new Image();
level_tube_img.src = "/images/bookpics/level_canvas_tube.png";
const level_bubble_img = new Image();
level_bubble_img.src = "/images/bookpics/level_canvas_bubble.png";
const level_tube_img_r = new Image();
level_tube_img_r.src = "/images/bookpics/level_canvas_tube_r.png";
const level_bubble_img_r = new Image();
level_bubble_img_r.src = "/images/bookpics/level_canvas_bubble_r.png";
const v_to_path2D = document.getElementById('vectorGrid');
const ctx2D = v_to_path2D.getElementsByClassName('trajectory1D')[0].getContext('2d');
var xElement = document.getElementById("xvalue");
var yElement = document.getElementById("yvalue");
xElement.value = 2;
yElement.value = 2;
var xcurrent = 0;
var ycurrent = 0;
ctx2D.textAlign = 'center';
ctx2D.textBaseline = 'middle';

function canvas_axis(context, maxX, maxY) {
  var midX = maxX/2;
  var midY = maxY/2;
  var stepX = maxX/20;
  var stepY = maxY/20;
  context.strokeStyle='rgba(0,0,0,0.5)';
  context.lineWidth=1;
  context.moveTo(midX, 0);
  context.lineTo(midX,maxY);
  context.moveTo(0, midY);
  context.lineTo(maxX, midY);
  context.stroke();
  context.strokeStyle='rgba(0,0,0,0.1)';
  for (var i=-10; i<=10; i++) {
    context.moveTo(0,midY+i*stepY);
    context.lineTo(maxX,midY+i*stepY);
    context.moveTo(midX+i*stepX,0);
    context.lineTo(midX+i*stepX,maxY);
  }
  context.stroke();
  context.drawImage(level_tube_img,45,360, 310, 34);
  context.drawImage(level_tube_img_r,6,45, 34, 310);
}

function plot_all(){
    xcurrent = 0.8*xcurrent + 0.2*xElement.value;
    ycurrent = 0.8*ycurrent + 0.2*yElement.value;
    var x = xcurrent;
    var y = ycurrent;
    x_scale = x*20 + 200;
    y_scale = -y*20 + 200;
  
    ctx2D.clearRect(0,0,400,400);
    ctx2D.beginPath();
    canvas_axis(ctx2D, 400, 400);
    ctx2D.drawImage(level_bubble_img,x_scale-22,360, 44, 34);
    ctx2D.drawImage(level_bubble_img_r,6,y_scale-22, 34, 44);
    ctx2D.font = '14px sans';
    ctx2D.fillStyle = '#228e2c';
    ctx2D.strokeStyle = '#228e2c';
    ctx2D.beginPath();ctx2D.moveTo(x_scale,y_scale);ctx2D.lineTo(200,y_scale);ctx2D.stroke();
    ctx2D.fillText('X = '+xcurrent.toFixed(1),x*10+200,y_scale-10*Math.sign(y));
    ctx2D.fillStyle = '#2676b3';
    ctx2D.strokeStyle = '#2676b3';
    ctx2D.beginPath();ctx2D.moveTo(x_scale,y_scale);ctx2D.lineTo(x_scale,200);ctx2D.stroke();
    ctx2D.fillText('Y = '+ycurrent.toFixed(1),x_scale+40*Math.sign(x),-y*10+200);
    ctx2D.beginPath();
    ctx2D.strokeStyle='black';
    ctx2D.lineWidth=2;
    canvas_arrow(ctx2D,200,200,x_scale, y_scale);
    ctx2D.stroke();
    var magnitude = Math.sqrt(x*x  + y*y);
    var direction_angle = Math.atan2(y,x)/Math.PI*180;
    if (direction_angle < 0){
    	direction_angle = direction_angle + 360;
    }
    document.getElementById("xshow").innerHTML=xcurrent.toFixed(1);
    document.getElementById("yshow").innerHTML=ycurrent.toFixed(1);
    document.getElementById("magshow").innerHTML=magnitude.toFixed(1);
    //document.getElementById("angshow").innerHTML=direction_angle.toFixed(0);
}

setInterval(plot_all, 50);
</script>

<!-- TODO: Stefan will be modifying this to better link with the bubble sensors.
-->

::: further-reading
You can learn more about how to describe and work with quantities that have
a direction from our [lesson on vectors](/vectors).
:::

## Measuring Gravity with the SpinWheel

The SpinWheel has sensors that can measure gravity along 
<span class="footnote">three axes<span>Below the interactive SpinWheel animation, you can see how these three axes, x, y, and z, are defined.</span></span>.
In the visualization below you can see how different tilts will result in different measurement results:
e.g., tilting left/right changes the measurement along the <span style="color:#228e2c;">$x$</span> axis.
As you are playing with the sliders, pay close attention to the <span style="color:#228e2c;">$x$</span> and <span style="color:#2676b3;">$y$</span> components 
as they are the ones
corresponding to the displacement of the air bubbles seen
in the bubble levels above.
The upright grey vector is the acceleration due to gravity, which is fixed with respect to the surface of Earth.
That vector's <span style="color:#228e2c;">$x$</span> and <span style="color:#2676b3;">$y$</span> components (shown below) give the <span style="color:#228e2c;">$x$</span> and <span style="color:#2676b3;">$y$</span> measurements we will be using.

<!-- I think this needs more explanation.
-->

<!-- Are x, y, z labels possible to add to the interactive animation? So that people don't need to match the colors? 
-->

<!-- This animation is fun, but I do not understand what I am supposed to be doing with it? 
-->

<!-- TODO: add some pictures showing how if the SpinWheel is tilted, gravity is no longer perpendicular to the plane and that is how the measurements work
-->

<div id="threediv"><div id="threejsanim"></div><span id="xlenp">X component: <span id="xlen"></span></span><span id="ylenp">Y component: <span id="ylen"></span></span>Tilt back and forth:<input id="fbtilt" type="range" min="-100" max="+100" value="30">Tilt left and right:<input id="lrtilt" type="range" min="-100" max="+100">Rotate face:<input id="frotate" type="range" min="-100" max="+100"></div>

<style>
#threediv {
  text-align: center;
  width: 100%;
}
#threediv > * {
  display: block;
  margin: auto;
}
#threediv #xlenp {
  color: #228e2c;
}
#threediv #ylenp {
  color: #2676b3;
}
</style>

<script type="module">

import * as THREE from '/three/three.module.js';

import { OrbitControls } from '/three/OrbitControls.js';
 
function makeSpinWheel() {
  var outerbox = new THREE.Group();
  var box = new THREE.Group();
  var geometry = new THREE.CylinderGeometry(20,20,1,24);
  var material = new THREE.MeshPhongMaterial({color: 0x111111, transparent: true, opacity: 0.90});
  var disk = new THREE.Mesh( geometry, material );
  box.add(disk);
  var sgeometry = new THREE.CylinderGeometry(1.5,1.5,1,24);
  var sdisk = new THREE.Mesh( sgeometry, material );
  sdisk.position.set(21/1.414,0,21/1.414);
  box.add(sdisk);
  for (var i=0; i<4; i++) {
    var bgeometry = new THREE.BoxGeometry(5,1.5,5);
    var wmaterial = new THREE.MeshPhongMaterial({color: 0xbbbbbb});
    var square1 = new THREE.Mesh(bgeometry, wmaterial);
    var square2 = new THREE.Mesh(bgeometry, wmaterial);
    var x = (-1)**i;
    var z = (-1)**(i>>1);
    square1.position.set(x*10,1.25,z*10);
    square2.position.set(x*3,1.25,z*3);
    //square1.rotation.z += Math.PI/2;
    box.add(square1);
    box.add(square2);
  }
  box.rotation.y = Math.PI*3/4;
  outerbox.add(box);
  return outerbox;
}

function makeScene() {
  var scene = new THREE.Scene();
  scene.background = new THREE.Color( 0xffffff );

  var lights = [];
  lights[ 0 ] = new THREE.PointLight( 0xaaaaaa, 1, 0 );
  lights[ 1 ] = new THREE.PointLight( 0xaaaaaa, 1, 0 );
  lights[ 2 ] = new THREE.PointLight( 0xaaaaaa, 1, 0 );
  lights[ 0 ].position.set( 0, 200, 100 );
  lights[ 1 ].position.set( 0, 0, 100 );
  lights[ 2 ].position.set( 0, - 200, 100 );
  
  scene.add( lights[ 0 ] );
  scene.add( lights[ 1 ] );
  scene.add( lights[ 2 ] );

  var grid = new THREE.GridHelper( 1500, 70 );
  grid.position.set(0,-100,0);
  scene.add(grid);

  return scene;
}

var camera, scene, renderer;
var box;
var arrow;
var xarrow, yarrow, zarrow;
var sphere;
var lx_glob, ly_glob;
const size = 400;
const animdiv = document.getElementById('threejsanim');
const fgtilt = document.getElementById('fbtilt');
const lrtilt = document.getElementById('lrtilt');
const frotate = document.getElementById('frotate');
const xlen = document.getElementById('xlen');
const ylen = document.getElementById('ylen');
   
function init() {
  scene = makeScene();
  
  box = makeSpinWheel();
  scene.add(box);

  arrow = new THREE.ArrowHelper(
    new THREE.Vector3(0,1,0),
    new THREE.Vector3(0,0,0),
    //40, 0xf58559,
    40, 0xaaaaaa,
    10, 4
  );
  scene.add(arrow);

  xarrow = new THREE.ArrowHelper(
    new THREE.Vector3(1,0,0),
    new THREE.Vector3(0,2,0),
    40, 0x92bd80,
    10, 4
  );
  box.add(xarrow);

  yarrow = new THREE.ArrowHelper(
    new THREE.Vector3(0,0,-1),
    new THREE.Vector3(0,2,0),
    40, 0x8fb0d3,
    10, 4
  );
  box.add(yarrow);

  zarrow = new THREE.ArrowHelper(
    new THREE.Vector3(0,1,0),
    new THREE.Vector3(0,2,0),
    40, 0xf58559,
    10, 4
  );
  //box.add(zarrow);

  /*
  var sgeometry = new THREE.SphereGeometry( 3, 12, 12 );
  var smaterial = new THREE.MeshBasicMaterial( {color: 0xf58559} );
  sphere = new THREE.Mesh( sgeometry, smaterial );
  scene.add(sphere);
  */ 

  var fov = 60;
  var aspect = 2;
  var near = 0.10;
  var far = 500;
  camera = new THREE.PerspectiveCamera(fov, aspect, near, far);
  camera.position.z = 80;
  
  renderer = new THREE.WebGLRenderer( { antialias: true } );
  renderer.setSize( size, size/2 );
  animdiv.appendChild( renderer.domElement );

  var controls = new OrbitControls(camera, renderer.domElement);
}
 
function animate() {
  requestAnimationFrame( animate );
  const fb = fbtilt.value*Math.PI/2/100;
  const lr = lrtilt.value*Math.PI/2/100;
  const r = frotate.value*Math.PI/2/100;
  const euler = new THREE.Euler(fb,r,lr,'ZXY');
  box.setRotationFromEuler(euler);
  const g = new THREE.Vector3(0,1,0);
  const py0 = new THREE.Vector3(0,0,-1);
  const my0 = new THREE.Vector3(0,0,1);
  const y0 = new THREE.Vector3(0,0,-1).applyEuler(euler);
  const ly = y0.dot(g);
  const aly = Math.abs(ly)*40
  yarrow.setLength(aly, Math.min(10,aly), 4);
  var dy;
  if (ly > 0) {
    dy = py0;
  } else {
    dy = my0;
  }
  const px0 = new THREE.Vector3(1,0,0);
  const mx0 = new THREE.Vector3(-1,0,0);
  const x0 = new THREE.Vector3(1,0,0).applyEuler(euler);
  const lx = x0.dot(g);
  const alx = Math.abs(lx)*40
  xarrow.setLength(alx, Math.min(10,alx), 4);
  var dx;
  if (lx > 0) {
    dx = px0;
  } else {
    dx = mx0;
  }
  const pz0 = new THREE.Vector3(0,1,0);
  const mz0 = new THREE.Vector3(0,-1,0);
  const z0 = new THREE.Vector3(0,1,0).applyEuler(euler);
  const lz = z0.dot(g);
  const alz = Math.abs(lz)*40
  //zarrow.setLength(alz, Math.min(10,alz), 4);
  var dz;
  if (lz > 0) {
    dz = pz0;
  } else {
    dz = mz0;
  }
  xarrow.setDirection(dx);
  yarrow.setDirection(dy);
  //zarrow.setDirection(dz);
  /*
  const xy = x0.clone()
               .multiplyScalar(lx*40);
  xy.add(y0.clone()
           .multiplyScalar(ly*40));
  sphere.position.copy(xy);
  */
  renderer.render( scene, camera );
  lx_glob = lx;
  ly_glob = ly;
  xlen.innerHTML = Math.round(lx_glob*100)/100;
  ylen.innerHTML = Math.round(ly_glob*100)/100;
}
 
init();
animate();
 
</script>

![These are the three axes that the SpinWheel can detect acceleration and gravity along. In the interactive 3D diagram you can see how the vector of gravitational acceleration (in grey) is decomposed along these three axes. You can drag, ctrl+drag, or scroll on the 3D image to rotate, pan, or zoom the camera.<a class="imagecredit" href="https://monochra.com/">image credit Mariya Krastanova</a>](/images/bookpics/dance_axis.png)

## Programming your own Tilt Sensor

Now that we have experimented with how the SpinWheel measures gravity, 
let's start writing the code for the tilt sensor! 
To start, we'll have two of the SpinWheel's LEDs respond to
tilt along the $x$ axis.
The SpinWheel will read
the gravity and acceleration along the $x$ axis,
interpret that value as a description of the tilt along that axis,
and then light up a corresponding LED along the same axis as appropriate.

### From an Empty Sketch

We will build our tilt sensor program step by step, 
starting with this empty sketch.
A good first step is to write some simple test code that 
just prints a few messages, confirming that your device is still functioning. 
For instance, copy the following code into your file. This code, 
once running on the SpinWheel, will repeatedly send the message 
"I am working!" to the computer that your SpinWheel is attached to. 
As always, we will add comments to the code, 
so that the purpose of each line is explained. 
(A comment is a line of code that is not run by the computer, 
but meant to be interpreted by humans. 
In this code, comment lines start with `//`).

::: further-reading
You can consult our [SpinWheel basic commands page](/basics) to remind yourself how to read the computer code shown below. For more details about coding itself, check out the [Coding Building Blocks page](/progpatterns).
:::

```cpp
#include "SpinWearables.h"
using namespace SpinWearables;

void setup() {
  // Connect to the computer, so we can read status messages.
  Serial.begin(115200);
  // Ensure the special SpinWheel hardware is working.
  SpinWheel.begin();  
}

void loop() {
  // Send a confirmation message over and over.
  Serial.println("I am working!"); 
}
```

If you upload this sketch to the SpinWheel, you won't be able to see anything happen. 
It doesn't turn on the LEDs, instead the sketch simply set ups the SpinWheel and sends a confirmation message ("I am working!") repeatedly using `Serial.println()`. 
If you want to see this message, navigate to `Tools -> Serial Monitor` in the Arduino software. 

### Measuring Tilt

Now we can start working with
measurements of tilt (direction of gravity) on the SpinWheel.
We do this by calling the `SpinWheel.readIMU()` function
to measure the three components of the gravitational vector
(shown in grey in the visualization above).
IMU stands for Inertial Measurement Unit:
a fancy name for something that senses motion. 
This function will record 3 values, one for each direction of motion.
Refer back to the image above to see how the $x$, $y$, and $z$ axes are defined.
To begin with, we will only use the $x$ components of the measurement.

```c++
#include "SpinWearables.h"
using namespace SpinWearables; 

void setup() {
  // Ensure all of the SpinWheel hardware is on.
  SpinWheel.begin();
}

void loop() {
  // Read all sensor data.
  SpinWheel.readIMU();

  // Save the x-axis measurement in a variable.
  int x = SpinWheel.ax*255;
}
```

In the sketch above, the measurement of gravity and acceleration along the $x$ axis is 
contained in the `SpinWheel.ax` variable.
We aren't using this measurement to do anything yet, however. 
In the next section, we'll begin changing the LEDs based on this information.

### Responding to Tilt Along the X-axis

To make a useful level, we need the LEDs to change in response to how the 
SpinWheel is tilted. The code below lights up either large LED 5 or 7
depending on which LED is pointing down. Upload the below code onto your 
SpinWheel and experiment some to see how it works. 

```c++
#include "SpinWearables.h"
using namespace SpinWearables; 

void setup() {
  // Ensure all of the SpinWheel hardware is on.
  SpinWheel.begin();
}

void loop() {
  // Read all sensor data.
  SpinWheel.readIMU();

  // Save the x-axis measurement in a variable.
  int x = SpinWheel.ax*255;

  // Turn off all LEDs.
  SpinWheel.clearAllLEDs();

  // If the tilt is in a given direction,
  // turn on the corresponding LED.
  // We only want the SpinWheel to register
  // if the tilt is sufficiently large.
  if (x > 10) {
    SpinWheel.setLargeLED(5,-x, -x,-x);
  }
  else if (x < -10) {
    SpinWheel.setLargeLED(7, x, x, x);
  }

  SpinWheel.drawFrame();
}
```

Because the SpinWheel's motion sensors are very sensitive,
we only want the LEDs to light up if the SpinWheel tilts enough.
We have decided that if `SpinWheel.ax`, or `x` in the code above,
is <span class="footnote">bigger than 10<span>We picked 10 arbitrarily and you can set it to a different value.</span></span>, then we want the LED to light up. 
You could decide to make your tilt sensor more or less sensitive 
by adjusting the value in the lines: 
`if (x > 10)` and `else if (x < -10)`. 
You could instead have the LED on the side that is higher light up
by swapping which LED is called (replacing `5` with `7` in the first 
instance of `setLargeLED` and `7` with `5` in the second instance, 
so your code looks like the following:

```c++
  if (x > 10) {
    SpinWheel.setLargeLED(7,-x, -x,-x);
  }
  else if (x < -10) {
    SpinWheel.setLargeLED(5, x, x, x);
  }
```

You can experiment with the code in other ways as well. 
For instance, you could change the color that LED 5 and 7 light up
or have more LEDs also light up.

### Improving the Tilt Sensor

If you want your tilt sensor to behave more like the second level in the pictures above,
then you can upload a slightly more detailed
version of the above code that senses both along the $x$ and $y$ axes.
Go to the Examples menu in the Arduino software, and open the file here:
[`Examples → SpinWearables → Tilt_Sensor →  Simple`](/codedoc/examples/Tilt_Sensor/Simple/Simple.ino.html). 
After looking at this version, 
feel free to modify the code further,
creating more elaborate visualizations.
A version similar to the one shown below can be found in
[`Examples → SpinWearables → Tilt_Sensor →  Fancy`](/codedoc/examples/Tilt_Sensor/Fancy/Fancy.ino.html).

Both the
[`Simple`](/codedoc/examples/Tilt_Sensor/Simple/Simple.ino.html)
and the
[`Fancy`](/codedoc/examples/Tilt_Sensor/Fancy/Fancy.ino.html)
code examples can also be seen in your browser in literate programming renditions.



::: further-reading
We have [a list of visualization functions](/allcommands) that can be of use
when making more elaborate tilt visualizations.
You might also be interested in the [dancing with color](/dancing)
or [step counter](/stepcounter) adventures,
which explore different ways to depict motion with the SpinWheel.
:::
