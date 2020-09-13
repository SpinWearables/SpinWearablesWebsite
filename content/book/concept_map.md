---
title: The SpinWheel Field Guide
keywords: spinwheel, STEM, science, science and art, physics, computer science, middle school, high school, textbook
header-video: /images/banners/linewheel_crossfade.mp4
nocomments: nocomments
---


<script src="/jquery.min.js"></script>
<script src="/springy/springy.js"></script>
<script src="/springy/springyui.js"></script>

<script>

jQuery(function(){
  var graph = new Springy.Graph();

  var intro = graph.newNode({label: "Getting Started with the SpinWheel", color: "red"});
  var quick = graph.newNode({label: "Initial Setup", color: "red"});
  var basic = graph.newNode({label: "Basic Structure of a Program"});
  var arduino = graph.newNode({label: "Arduino 101", color: "grey"});
  var sight = graph.newNode({label: "Biology of Sight"});
  var strobe = graph.newNode({label: "Stroboscope"});
  var ani = graph.newNode({label: "Intro to Animations"});
  var ani2 = graph.newNode({label: "Animations and Patterns"});
  var step = graph.newNode({label: "Step Counter"});
  var dance = graph.newNode({label: "Dancing Companion"});
  var compass = graph.newNode({label: "Compass"});
  var progpatterns = graph.newNode({label: "Building Blocks of Coding", color: "grey"});
  var light = graph.newNode({label: "Light and Color", color: "grey"});
  var colortheory = graph.newNode({label: "Color Theory", color: "grey"});
  var inertia = graph.newNode({label: "Inertial Reference Frames", color: "grey"});
  var rotation = graph.newNode({label: "Rotation", color: "grey"});
  var magnet = graph.newNode({label: "Magnetism", color: "grey"});
  var vector = graph.newNode({label: "Vectors and Motion", color: "grey"});
  
  graph.newEdge(intro, quick);
  graph.newEdge(quick, sight); 
  graph.newEdge(quick, strobe);
  graph.newEdge(sight, ani); 
  graph.newEdge(ani, basic);
  graph.newEdge(basic, arduino);  
  graph.newEdge(sight, light); 
  graph.newEdge(light, colortheory); 
  graph.newEdge(ani, ani2); 
  graph.newEdge(arduino, progpatterns); 
  graph.newEdge(ani2, progpatterns); 
  graph.newEdge(ani2, step); 
  graph.newEdge(ani2, dance);
  graph.newEdge(dance, compass); 
  graph.newEdge(compass, magnet);
  graph.newEdge(step, compass);
  graph.newEdge(dance, vector); 
  graph.newEdge(vector, rotation); 
  graph.newEdge(dance, inertia);
  graph.newEdge(step, inertia);

  var springy = jQuery('#springymap').springy({
    graph: graph,
    stiffnes: 200,
    repulsion: 2000,
    damping: 0.5
  });
});

</script>

<canvas id="springymap" width="800" height="600">
</canvas>

There is a lot going on in the map above, so below we have our recommended order for completing the lessons and adventures. However, this is just a recommendation! Depending on which activities you are excited by and your comfort with programming, then you may jump around.

<style>
@font-face {
  font-family: 'xkcd';
  src: url('/xkcd-script.ttf')  format('truetype');
}

:root {
  /* Change this to change the appearance of the hexaons */
  --hex-width: 150px; 
  --hex-inner-border: 15px;
  
  /* Other hexagon dimentions */
  --hex-side: calc(var(--hex-width)/2);
  --hex-height: calc(var(--hex-side)*1.7320508075688772);
  --hex-tiptotip: calc(var(--hex-side)*3 - var(--hex-inner-border)*0.75);
  --hex-transition: all .2s ease;
}

/* Hexagons */
.hexagon-container {
  display: grid;
  grid-template-columns: var(--hex-tiptotip) var(--hex-tiptotip) var(--hex-tiptotip) var(--hex-tiptotip);
  grid-auto-rows: calc(var(--hex-height)/2 - var(--hex-inner-border)*1.7320508075688772/8);
  grid-gap: 0 0;
  font-family: xkcd;
}
.hexagon {
  align-items: center;
  cursor: pointer;
  display: flex;
  height: var(--hex-height);
  justify-content: center;
  position: relative;
  transition: var(--hex-transition);
  width: var(--hex-width);
}

.hexagon:nth-child(8n + 5),
.hexagon:nth-child(8n + 6),
.hexagon:nth-child(8n + 7),
.hexagon:nth-child(8n + 8) {
  margin-left: calc(var(--hex-side) * 1.5 - var(--hex-inner-border)*0.375);
}

.hexagon {
  clip-path: polygon(75% 0, 100% 50%, 75% 100%, 25% 100%, 0 50%, 25% 0);
}

.hexagon * {
  display: block;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: var(--hex-transition);
  clip-path: polygon(75% 0, 100% 50%, 75% 100%, 25% 100%, 0 50%, 25% 0);
  background-color: white;
}

.hexagon a {
  text-align: center;
  line-height: 18px;
  font-size: 16px;
  text-decoration: none;
}

.hexagon *:hover {
  background-color: white !important;
  font-size: 18px !important;
}

.hexagon > * {
  width: calc(var(--hex-width) - var(--hex-inner-border));
  height: calc(var(--hex-height) - var(--hex-inner-border)*1.7320508075688772/2);
}

.hexagon > div > div {
  width: calc(var(--hex-width) - 1.8*var(--hex-inner-border));
  height: calc(var(--hex-height) - 1.8*var(--hex-inner-border)*1.7320508075688772/2);
}

.hexagon > div > div > a {
  width: calc(var(--hex-width) - 2.1*var(--hex-inner-border));
  height: calc(var(--hex-height) - 2.1*var(--hex-inner-border)*1.7320508075688772/2);
}
</style>

<ul id="hexmap" class="hexagon-container">
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
  <li class="hexagon"></li>
</ul>

<script>
const tiles = [
{x:1, y:2, bgcolor:"#ffffff", textcolor:"#bf1e2e", bordercolor:"#bf1e2e", inner: true, text:"Getting<br>Started<br>with the<br>SpinWheel", href:"intro"},
{x:2, y:3, bgcolor:"#f2d2d5", textcolor:"#bf1e2e", bordercolor:"#bf1e2e", inner: true, text:"SpinWheel<br>Initial<br>Setup", href:"quickstart"},
//light
{x:2, y:5, bgcolor:"#d0eeec", textcolor:"#13a89e", bordercolor:"#13a89e", inner: true, text:"Mixing<br>Color with<br>Light", href:"#"},
{x:1, y:6, bgcolor:"#ffffff", textcolor:"#13a89e", bordercolor:"#13a89e", inner: true, text:"Biology of<br>Sight", href:"sight"},
{x:1, y:7, bgcolor:"#ffffff", textcolor:"#13a89e", bordercolor:"#13a89e", inner: false, text:"Color<br>Theory", href:"colortheory"},
{x:1, y:5, bgcolor:"#ffffff", textcolor:"#13a89e", bordercolor:"#13a89e", inner: false, text:"Light and<br>Color", href:"lightandcolor"},
//basic prog
{x:2, y:4, bgcolor:"#d3eef9", textcolor:"#25aae1", bordercolor:"#25aae1", inner: true, text:"Customizing<br>the SpinWheel&#39;s<br>Display", href:"#"},
{x:2, y:6, bgcolor:"#d3eef9", textcolor:"#25aae1", bordercolor:"#25aae1", inner: true, text:"Arduino<br>101", href:"#"},
{x:3, y:5, bgcolor:"#ffffff", textcolor:"#25aae1", bordercolor:"#25aae1", inner: false, text:"Basic<br>Structure<br>of a<br>Program", href:"#"},
];
const hexmap = document.getElementById("hexmap");
const allhexes = hexmap.getElementsByClassName("hexagon");
for (const tile of tiles) {
  const hex = allhexes[(tile.x-1)+4*(tile.y-1)];

  hex.style["background-color"] = tile.bordercolor;
  var innerHTML = `<a href="${tile.href}" style="color:${tile.textcolor};background-color:${tile.bgcolor}">${tile.text}</a>`;
  if (tile.inner==true) {
    innerHTML = `<div style="background-color:${tile.bgcolor}"><div style="background-color:${tile.bordercolor}">${innerHTML}</div></div>`;
  }
  hex.innerHTML = innerHTML;
}
</script>