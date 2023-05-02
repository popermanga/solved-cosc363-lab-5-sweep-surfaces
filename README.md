Download Link: https://assignmentchef.com/product/solved-cosc363-lab-5-sweep-surfaces
<br>
This lab is a continuation of Lab04 on object modelling. In this lab, we will consider another example of  sweep surface obtained by successive transformations of a polygonal shape.

<ol>

 <li><u> Tower.cpp:</u></li>

</ol>

The “Turning Torso” (Fig. a), a twisted tower in Malmo, Sweden is an excellent architectural example of a sweep surface/structure (For more information on the tower, see: <a href="https://en.wikipedia.org/wiki/Turning_Torso">http://en.wikipedia.org/wiki/Turning_Torso</a> ). We can generate a model of the tower using the shape shown in Fig (b) as the base polygon. The program Tower.cpp contains a representation of the polygonal shape using vertex coordinates stored in arrays vx[], vy[], vz[] inside the display() function.  The polygon has 18 vertices as shown in Fig. (c).  Since this is a closed polygon, the first vertex is appended to the end of the list again, to get a closed quad strip.  The vertex list therefore contains 19 vertices.

<table width="520">

 <tbody>

  <tr>

   <td rowspan="2" width="262">                        Fig. (a)</td>

   <td width="259"> Fig. (b)</td>

  </tr>

  <tr>

   <td width="259">16 Fig. (c)</td>

  </tr>

 </tbody>

</table>







The tower consists of 9 “blocks”, each block having a height of approx. 20 meters, and turned <em>clockwise</em> about the vertical axis by 10 degrees relative to the lower block.




<ol>

 <li>The program displays only the base polygon (Fig. c) at the bottom part of the screen. The camera can be moved around the scene using the left and right arrow keys.</li>

 <li>Delete the code segment that draws the base polygon inside the display() function and implement the following algorithm:</li>

</ol>




<ul>

 <li>Generate a new set of transformed coordinates wx[i], wy[i], wz[i], i = 0.. <em>N</em>1 (already declared in the program)  by rotating the points (vx[i], vy[i], vz[i]) by -10 degs (clockwise) about the <em>y</em>-axis and translating along <em>y</em>axis by 20 units. Since we require the transformed points, we cannot use the OpenGL function glRotatef() to perform the rotation. Instead, we use the following equations:</li>

</ul>

<em>w<sub>x</sub></em> = <em>v<sub>x</sub></em> cos + <em>v<sub>z</sub></em> sin,           = −10 Degs (Convert to radians!) <em>w<sub>y</sub></em> = <em>v<sub>y</sub></em> <strong>+ 20</strong> <em>w<sub>z</sub></em> = <em> v<sub>x</sub></em> sin + <em>v<sub>z</sub></em> cos

<ul>

 <li>Join the points <em>V<sub>i</sub></em> = (vx[i], vy[i], vz[i]) and the transformed points <em>W<sub>i</sub></em> = (wx[i], wy[i], wz[i]) using a quad strip to generate the surface of the extruded shape.   Refer to the code given on Slide [5]-12.</li>

 <li>After drawing the quad-strip, replace the values in (vx[], vy[], vz[]) with the transformed values in (wx[], wy[], wz[]).</li>

</ul>

The above three steps generate the surface of one “block” of the tower.  Repeat the steps 8 more times.




The light and camera positions have already been defined in the program.  Change the value of the global variable viewAngle to -160 degs. The program should generate an output similar to the one given in Fig. (d).

Fig. (d)

<ol start="3">

 <li>The program includes the necessary functions for loading a bitmap texture “TowerTexture.bmp”. Please uncomment the three lines inside the initialise() function to enable texture mapping.  The texture has 5 parts corresponding to 5 sides of the tower (Fig (e)).</li>

</ol>

<em>t </em>




Fig. (e)

<ol start="4">

 <li>We need to assign texture coordinates to vertices of the quad strip. If a vertex <em>V<sub>i</sub></em>  has texture coordinates (<em>s<sub>i</sub></em>, 0),  then the corresponding vertex <em>W<sub>i</sub></em> will have texture coordinates (<em>s<sub>i</sub></em>, 1).  The values <em>s<sub>i</sub></em> must be carefully chosen so that the image sections in the texture are properly mapped to the 5 sides of the polygon (see Fig. (c)).   Fig(e) shows how this mapping must be done.  The table below gives the texture <em>s</em>-coordinates for some of the vertices. Compute the remaining coordinates, assuming that the points are uniformly distributed within each of the 3 middle sections.  Your program should then produce an output similar to the one given in Fig. (f).</li>

</ol>




<table width="521">

 <tbody>

  <tr>

   <td width="92">Vertex index  <em>i</em> 012:6:12:161718</td>

   <td width="95">Tex Coord<em>s<sub>i</sub></em> 00.15 0.2:0.4:0.6:0.80.851</td>

   <td width="334"> Fig. (f). Textured tower</td>

  </tr>

 </tbody>

</table>








