# Music Visualiser Project

Name:YuJiao Kan

Student Number: D20125727

## Instructions
- Fork this repository and use it a starter project for your assignment
- Create a new package named your student number and put all your code in this package.
- You should start by creating a subclass of ie.tudublin.Visual
- There is an example visualiser called MyVisual in the example package
- Check out the WaveForm and AudioBandsVisual for examples of how to call the Processing functions from other classes that are not subclasses of PApplet

# Description of the assignment
Planet rotation simulated the heavenly body in outer space.
An audio visual, to draw particle collisions visually.

# Instructions

The main function is noise(), which is wavy, undulating textures. 
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
• translate();
• rotateX();
• rotateY()
• radians()
• cos()
• sin()
• noise()
• ambientLight ();
• pointLight();
• random()



# What I am most proud of in the assignment

Mode 0
The rays of light have bounced around so much that objects are evenly lit from all sides.
•	ambientLight (30, 20, 50);
The rays of light from a point. x-coordinate is -300, y-coordinate is 0 , z-coordinate 300
•	pointLight(0, 255, 255, -300, 0, 300);
•	pointLight (255, 0, 0, -300.0f, 0.0f, -300.0f);

Rotate a shape around the x-axis and millis() returns the number of milliseconds that control speed is slow.
•	rotateX((millis() / 2000.0f));
•	rotateY(millis() / 2000.0f);

Mode 1

Fill color is black and diaphaneity is 10
•	fill(0,10); 
•	 rect(0, 0, width, height);
use noise() function, random sequence generate float number between  0.0 and 1.0
Draw a lot of ellipses following music to dance
•	while (degree <= 360)//circle =360
•	      {
•	        
•	        
•	      for (int i=0; i < player.bufferSize(); i++) {
•	        degree += incr;
•	        angle = radians(degree);
•	        x1 = cos(i) * (radian1 + ((distance1)* noise(y1/100, yIn)));
•	y1 = sin(i) * (radian1 + ((distance1+player.mix.level()*50) *noise(x1/380, yIn)));
•	        ellipse(x1*1, y1*1, 1.5f, 1.5f);
•	   
•	        x2 = sin(angle) * (radian2 + (distance2 * noise(y2/200, yIn)));
•	        y2 = cos(angle) * (radian2 + (distance2 * noise(y2/20, yIn)));
•	        ellipse(x2, y2, 1, 1);
•	       
•	      }
•	
•	      
•	      }
•	




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
public void render()
{
	ui.noFill();
	ui.stroke(255);
	ui.rect(x, y, width, height);
	ui.textAlign(PApplet.CENTER, PApplet.CENTER);
	ui.text(text, x + width * 0.5f, y + height * 0.5f);
}
```

So is this without specifying the language:

```
public void render()
{
	ui.noFill();
	ui.stroke(255);
	ui.rect(x, y, width, height);
	ui.textAlign(PApplet.CENTER, PApplet.CENTER);
	ui.text(text, x + width * 0.5f, y + height * 0.5f);
}
```

This is an image using a relative URL:

![An image](images/p8.png)

This is an image using an absolute URL:

![A different image](https://bryanduggandotorg.files.wordpress.com/2019/02/infinite-forms-00045.png?w=595&h=&zoom=2)

This is a youtube video:

[![YouTube](http://img.youtube.com/vi/J2kHSSFA4NU/0.jpg)](https://www.youtube.com/watch?v=J2kHSSFA4NU)

This is a table:

| Heading 1 | Heading 2 |
|-----------|-----------|
|Some stuff | Some more stuff in this column |
|Some stuff | Some more stuff in this column |
|Some stuff | Some more stuff in this column |
|Some stuff | Some more stuff in this column |

