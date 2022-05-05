# Music Visualiser Project

Name:YuJiao Kan

Student Number: D20125727


# Description of the assignment
Planet rotation simulated the heavenly body in outer space.
An audio visual, to draw particle collisions visually.

# Instructions

The most important function is noise(), which is wavy, undulating textures. 
The noise function is more rhythmic than the standard random function and generates continuous random numbers between 0.0 and 1.0.
Use a Sphere() function to draw spheres in 3D.


# How it works
•	Use keyPressed() class 
•	I have 2 modes

```Java
  public void keyPressed()
  {
     if (key >= '0' && key <= '1') {
        mode = key - '0';
      }
   
      if (keyCode == ' ') {
              if (player.isPlaying()) {
                  player.pause();
              } else {
                  player.rewind();
                  player.play();
              }
          }
        
    }
```
- pushMatrix();
- popMatrix();
- translate();
- rotateX();
- rotateY()
- radians()
- cos()
- sin()
- noise()
- ambientLight ();
- pointLight();
- random()



# What I am most proud of in the assignment

Mode 0
The rays of light have bounced around so much that objects are evenly lit from all sides.
-	ambientLight (30, 20, 50);
The rays of light from a point. x-coordinate is -300, y-coordinate is 0 , z-coordinate 300
-	pointLight(0, 255, 255, -300, 0, 300);
-	pointLight (255, 0, 0, -300.0f, 0.0f, -300.0f);

Rotate a shape around the x-axis and millis() returns the number of milliseconds which gives the function an effect that varies over time. 
-	rotateX((millis() / 2000.0f));
-	rotateY(millis() / 2000.0f);

Mode 1

Fill color is black and diaphaneity is 10
-	fill(0,10); 
-	rect(0, 0, width, height);
-	
use noise() function, random sequence generate float number between  0.0 and 1.0
Draw a lot of ellipses which rotate 1 degree in everytime.
-	while (degree <= 360)//circle =360
-	      {      
-	       for (int i=0; i < player.bufferSize(); i++) {
-	        degree += incr;
-	        angle = radians(degree);
-	        x1 = cos(i) * (radian1 + ((distance1)* noise(y1/100, yIn)));
-	        y1 = sin(i) * (radian1 + ((distance1+player.mix.level()*50) *noise(x1/380, yIn)));
-	        ellipse(x1*1, y1*1, 1.5f, 1.5f);
-	   
-	        x2 = sin(angle) * (radian2 + (distance2 * noise(y2/200, yIn)));
-	        y2 = cos(angle) * (radian2 + (distance2 * noise(y2/20, yIn)));
-	        ellipse(x2, y2, 1, 1);  
-	      }    
-	      }





# Markdown Tutorial

This is *emphasis*

This is a bulleted list

- Item
- Item

This is a numbered list

1. Item
1. Item

This is a [hyperlink](http://bryanduggan.org)

# Headings
## Headings
#### Headings
##### Headings

This is code:

```Java
package D20125727;


import ddf.minim.*;
import processing.core.PApplet;


public class ParticleCollisions extends PApplet{

    Minim minim;
    AudioPlayer player;
    int num;
    float [] x1;
    float[] y1;
    float[] z1;
    int mode=0;
  

    // noise(), sin(), rotate(),
    float x, y,x3, x2, y2, radian1, radian2, distance1, distance2,thetaX,thetaY;
    float degree, incr, yIn, rotateBy, angle;
    

    public void settings()
    {
      
       size(2040, 1280,P3D);
        //
       // fullScreen(P3D);
        minim = new Minim(this);
        
      
        player = minim.loadFile("TOMO - 化作青烟(さくらひらり).mp3", 1024);
      
       
    }


    public void setup() {
      smooth();
      colorMode(RGB);
      
      num=35;
      
      x1=new float[num];
      y1=new float[num];
      z1=new float[num];
        
      incr = 1; // numVertex = 360/incr
      radian1= -30 ;
      radian2 = -200 ;
      distance1 = 550;
      distance2 = 550;

      //sphere coordinate in 3D
      for (int i = 0; i < num; i++) 
      {
        x1[i] = random(-1000.0, 1000.0);
        y1[i] = random(-1100, 900);
        z1[i] = random(-1200, 800);
      } 
      
    
      
      
      
    }
   
    private float random(double d, double e) {
      return 0;
    }


    public void keyPressed() {
      if (key >= '0' && key <= '1') {
        mode = key - '0';
      }
   
      if (keyCode == ' ') {
              if (player.isPlaying()) {
                  player.pause();
              } else {
                  player.rewind();
                  player.play();
              }
          }
        
    }
  

    public void draw() {
      //player.play();
      
    switch (mode) {



      case 0:
      {
      
        colorMode(RGB);
      background(0);


      translate(width/2, height/2);

      ambientLight (30, 20, 50);
      pointLight(0, 255, 255, -300, 0, 300);
      pointLight (255, 0, 0, -300.0f, 0.0f, -300.0f);

      rotateX((millis() / 3000.0f));
      rotateY(millis() / 3000.0f);

      for (int i = 0; i < num; i++) {
        pushMatrix();
        translate(x1[i], y1[i], z1[i]);
        
        rotateX(i * 0.2f + millis() * 0.004f);
        rotateY(i * 0.3f + millis() * 0.004f);
        noStroke();
        sphere(20);
        popMatrix();

      }



        
        break;
      }   

      case 1:
      
      
      noStroke();
      fill(0,10);
      rect(0, 0, width, height);
      fill(random(0, 5), 255, 255);
     
      rotateBy += player.mix.level()*0.03;
      pushMatrix();
      translate(width/2, height/2);
      rotate(rotateBy);
      degree = 0;
      while (degree <= 360)
      {
        
        
      for (int i=0; i < player.bufferSize(); i++) {
        degree += incr;
        angle = radians(degree);
        x = cos(i) * (radian1 + ((distance1)* noise(y/100, yIn)));
        y = sin(i) * (radian1 + ((distance1+player.mix.level()*50) * noise(x/380, yIn)));
        ellipse(x*1, y*1, 1.5f, 1.5f);
   
        x2 = sin(angle) * (radian2 + (distance2 * noise(y2/200, yIn)));
        y2 = cos(angle) * (radian2 + (distance2 * noise(y2/20, yIn)));
        ellipse(x2, y2, 1, 1);
       
      }

      
      }
      

        for(int i=0; i<player.bufferSize()-1;i++){

        
        noFill();
        strokeWeight(2);
        stroke(5,255,255,10);
        rotateX(frameCount*3);
        rotateY(frameCount*3);
        ellipse(90,90,player.mix.get(i), player.mix.get(i));
        
        
      

      }
      
      yIn += .003;
      popMatrix();

      break;

     

    }

  }
}

```

This is a youtube video:

[![YouTube](http://img.youtube.com/vi/C4OJTFsQW44/0.jpg)](https://youtu.be/C4OJTFsQW44)



