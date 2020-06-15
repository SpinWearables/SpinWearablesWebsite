---
title: Color Theory
keywords: color, light, electromagnetism, color theory, pigments, art
---

::: intro-box
In this lesson, we'll introduce the concept of colors. We will also describe how the properties of light make the colors that we see.
:::

::: warning :
This lesson is still under-development. Check back soon for more links and the full lesson!
:::

::: further-reading
todo: refer to the science of vision page, but focus on electromagnetism
:::


## Colors
Whether you're walking through a lush forest or art museum, our world is full of colors. Colors make a painting beautiful and make our homes and schools much more fun. Colors also have practical uses such as the colors on a stoplight or color-coding your class notes. Let's explore how colors are made, mixed, and emerge from light!

<!--TODO: Colorful picture goes here -->

### Mixing Colors with Pigments

If you've ever painted before, you’ve probably mixed colors on a pallet. When we are painting, we are using the pigments in our paint to create color. The idea of using pigments to create color is used in our clothes, painting our houses and even coloring our food. 

::: further-reading
Pigments work by absorbing certain wavelengths of light and reflecting others. To read more about how light is a wave, check out our [light and color lesson](/lightandcolor).
:::

When painting in elementary school, you likely were given red, yellow, and blue to use to mix the rest of the colors you wanted. With these colors you can create more colors such as green, orange, and purple. Your teacher may have taught you the difference between primary and secondary colors. Primary colors are those that can't be mixed from other colors while secondary colors can be created by mixing other colors.  


<!--TODO: maybe insert image of typical "primary blue, red, yellow" paint bottles -->

Using these three paints, you may have struggled to get a true purple or the exact green that you imagined. The reason for this is that the red and blue that you were given are not true primary colors. The true primary colors can be seen in a typical printer that uses yellow, cyan (a fancy word for the specific blue that is a primary color), and magenta (the specific color word for the red that is a primary color). 

<!--TODO: add an animation/widget/image showing where red and magenta are on the color wheel -->

In elementary school you weren't taught these names for the colors because they are seen as "too hard." The important thing from this lesson isn't remembering these words, but the idea of mixing colors. 

<!--TODO: add a picture of a painting pallet or easel? -->

If you have ever mixed colors using yellow, cyan, and magenta, you may have noticed how many more colors you can mix using them instead of what we think of as "primary red, yellow, and blue." Experiment a bit with mixing colors using the widget below.

<style>
#scolortests {
  font-size: 2rem;
}
#scolortests .explain {
  font-size: 1rem;
  width: 80%;
  margin: 0 auto;
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
<div class="explain">
Imagine a white sheet of paper (reflecting all colors of white light) on which we add pigments that absorb some colors. That would be cyan (absorbing red and reflecting green and blue), magenta (absorbing green), and yellow (absorbing blue). Adding up these pigments leads to absorbing all colors and reflecting none, making the page black.
</div>
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
 	  
Experimenting with this widget, you may have been able to make green from mixing together cyan and yellow or orange from yellow and magenta. You may have noticed that you could also make the color red that is often introduced in elementary school as a primary color by mixing together magenta and yellow.


::: further-reading
Did you notice how if you wanted to get a darker green, you could add magenta? Adding magenta makes a darker green because red is green's complementary color. Adding a color's "complement" is actually a more effective way to make a darker color then adding black. Complementary colors are opposite each other on the color wheel. This website talks more about [complementary colors](https://www.thesprucecrafts.com/definition-of-complementary-colors-2577513). 
:::

### Mixing Colors With Light 

When we make colors with light sources, color mixing works differently. Your computer or tv screen works by creating colors using an LED display using only three colors of light. When we mix paint, our primary colors are magenta (red), cyan (blue), and yellow. When we create color with an LED display instead, we vary the amount of green, red, and blue, which we can think of as the three digital primary colors.

The widget below shows the three digital primary colors, which we can combine in amounts from 0 to 255. Looking at the widget below, notice how with all three slide bars at 255, the box at the right is white. By adjusting the relative amount of green, red, and blue using the slide bars, you can change the color displayed.

<style>
#acolortests {
  font-size: 2rem;
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
<div class="explain">
Imagine a white sheet of paper (i.e. paper that does not absorb any of the colors of light falling on it) in a dark room. We shine three lights on it, with different intensity: a red, a green, and a blue light. If we shine them all together, we reflect all visible color components of the sheet of paper and see a white color.
</div>
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

Take a moment to play around with these and see if you can make your favorite color!

Did you notice how if you put the amount of blue at 0, but leave the red and green at 255 that you make yellow? This is different than mixing colors with paint! While yellow is a primary color for mixing paint, it isn't a primary color when mixing with light sources (green is instead!).

::: further-reading
The reason that there are three primary colors for mixing with light sources and pigments has to do with how our eyes detect light and how our brains turn that into the image of the world that we see. To explore this more, go through the [Biology of Sight Adventure](/sight).
:::


