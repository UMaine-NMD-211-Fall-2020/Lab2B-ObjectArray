# Lab2B-ObjectArray
Make an array of 5+ objects. 
Move objects. 
Change enough so that you understand what is happening, and that this becomes your own.

## Lab Instructions
### Lab Set Up
Update your `README.md` file for lab 2 with what you are gong to do with lab 2B.
1. Open a new Processing file. Inside of your lab 2 folder, save your file within the lab 2 folder as as `Lab2B-*YOUR FIRST NAME*-*YOUR LAST NAME*`.
2. Add your header comments.
```processing
/*  Lab 2B - NMD 211
    FirstName LastName
    September 16, 2020
    
    
    Object arrays
    - create basic object
    - make 5+ objects with an array
    - motion
*/
```
3. Set up your processing drawing. Set the output size, if you want strokes, and ellipseMode. 
```processing
void setup(){                                                  // --- SETUP ---
  size(500,500);                                               // drawing surface size
    
  noStroke();                                                  // no outlines 
  ellipseMode( CENTER );                                       // ellipses drawn (x,y,w,h)
}
```
4. Start the draw section below your setup section. Add your background. 
```processing
void draw(){                                                                          // --- DRAW ---
  background(255, 255, 225);                                                          // background color is off white
}
```
### Create ColorCircle Class
5. Below draw, create a generic class named ColorCirlce with an empty constructor. 
```processing
class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  
  ColorCircle(  ){                                                                    // - CLASS'S CONSTRUCTOR
  }
}
```
6. At the very top of the page, above setup and below initial comments, declare that there will be an array of ColorCircle objects. Also make a global variable saying how long the array will be.
Then, instanatiate the ColorCircle object array inside of setup
```processing
ColorCircle[] circlesArray;                                                           // declare global array

// - global variables & other constants
int numberCircles = 5;                                                                // number of circles

void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
 }
```
7. Place a token ColorCircle array inside of each of the array slots with a [for](https://processing.org/reference/for.html) loop. 
```processing
ColorCircle[] circlesArray;                                                           // declare global array

// - global variables & other constants
int numberCircles = 5;                                                                // number of circles

void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
  // - place each circle in the array
  for ( int circle = 0 ; circle < numberCircles ; circle ++){                         // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ] = new ColorCircle();                                       // circleArray value circle is a ColorCircle object
  } // END FOR
 }
```
#### Code Up Until Now
Your entire code should looks something like the following as of now. 
If you run it, you should have an empty background.
```processing
/*  Lab 2B - NMD 211
    FirstName LastName
    September 16, 2020
    
    
    Object arrays
    - create basic object
    - make 5+ objects with an array
    - motion
*/
ColorCircle[] circlesArray;                                                           // declare global array

// - global variables & other constants
int numberCircles = 5;                                                                // number of circles

void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
  // - place each circle in the array
  for ( int circle = 0 ; circle < numberCircles ; circle ++){                         // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ] = new ColorCircle();                                       // circleArray value circle is a ColorCircle object
  } // END FOR
 }
 
void draw(){                                                                          // --- DRAW ---
  background(255, 255, 225);                                                          // background color is off white
}

class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  
  ColorCircle(  ){                                                                    // - CLASS'S CONSTRUCTOR
  }
}
```

### Display ColorCircle Object
8. Define an empty display function inside of your ColorCircle class.
```processing
class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  
  ColorCircle(){                                                                      // - CLASS'S CONSTRUCTOR
  }
  
  void display(){                                                                     // - DISPLAY CLASS OBJECT
  }
  
}
```
9. Add a call to display each colorcircle class in your array during the draw function below setting the background color. 
Remember that there's nothing new to see yet. 
```processing
void draw(){                                                                          // --- DRAW ---
  background(255, 255, 225);                                                          // background color is off white
  
  for ( int circle = 0; circle < numberCircles ; circle ++){                          // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ].display();                                                 //  - display the circle
  } // END FOR
}
```
10. Draw hardcoded ellipses using the class. 
Do this by adding to the display function/method in ColorCircle.
The values used are temporary, to be changed soon. 
Save & Run, to see that your display function is working properly. 
```processing
void display(){                                                                     // - DISPLAY CLASS OBJECT
    fill(0);                                                                          // temporary black fill
    ellipse( 0,0,80,80);                                                            // ellipse with temporary x, y, r, r valuse
  }
```
11. Add an input x, so you can spread the ellipses out and see that you have 5. 
If you change the x values the way I do, you will space the ellipses out equally across the drawing area.
To add an input, we need to add a local variable to the class, add to the class constructor, add to the class display, and add to our initialization call for loop. 

**class local variable & class constructor & display**
```processing
class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  float x;                                                                            // local variable storing circle's center x
  
  ColorCircle( float xIn ){                                                           // - CLASS'S CONSTRUCTOR
    x = xIn;                                                                          // input x value as center x
  }
  
  void display(){                                                                     // - DISPLAY CLASS OBJECT
    fill(0);                                                                          // temporary black fill
    ellipse( x,0,80,80);                                                            // ellipse with temporary x, y, r, r valuse 
  }
}
```

**initialization call for loop in setup**
```processing
void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
  // - place each circle in the array
  for ( int circle = 0 ; circle < numberCircles ; circle ++){                         // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ] = new ColorCircle(((1+circle)*width)/(numberCircles+1))  ; // - circleArray value circle is a ColorCircle 
  } // END FOR
 }
```
### Motion: Simple Top to Bottom
The circles are currently stationary. 
To move them from the top of the page to the bottom, we need to change the y values of each circle.
12. Add a changeable y value to the class ColorCirce.

**Add y to the local variables, the constructor, and display.**
```processing
class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  float x;                                                                            // local variable storing circle's center x
  float y;                                                                            // local variable storing circle's center y
 
  ColorCircle( float xIn, float yIn){                                                 // - CLASS'S CONSTRUCTOR
    x = xIn;                                                                          // input x value as center x
    y = yIn;                                                                          // input y value as center y
  }
  
  void display(){                                                                     // - DISPLAY CLASS OBJECT
    fill(0);                                                  // Set color
    ellipse( x , y, 80, 80);                                                            // Draw Shape 
  }
}
```
**Add y to the instance generator in setup.**
```processing
void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
  // - place each circle in the array
  for ( int circle = 0 ; circle < numberCircles ; circle ++){                         // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ] = new ColorCircle(                                         // - circleArray value circle is a ColorCircle 
                                                ((1+circle)*width)/(numberCircles+1), // x value
                                                 0)  ;                                // y value
  } // END FOR
 }
```
13. Add a function/method fall to the class. 
This will change the y values of the objects. 
To activate, call it after the object is displayed.
The motion used is super basic, all the same speed. 

**add y value to class**
```processing
class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  float x;                                                                            // local variable storing circle's center x
  float y;                                                                            // local variable storing circle's center y
 
  ColorCircle( float xIn, float yIn){                                                 // - CLASS'S CONSTRUCTOR
    x = xIn;                                                                          // input x value as center x
    y = yIn;                                                                          // input y value as center y
  }
  
  void display(){                                                                     // - DISPLAY CLASS OBJECT
    fill(0);                                                                          // Set color
    ellipse( x , y, 80, 80);                                                          // Draw Shape 
  }
  
  void fall(){                                                                        // - CLASS OBJECT MOTION
    y += 1;
  }
}
```
**y value in initialization**
```processing
void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
  // - place each circle in the array
  for ( int circle = 0 ; circle < numberCircles ; circle ++){                         // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ] = new ColorCircle(                                         // - circleArray value circle is a ColorCircle 
                                              ((1+circle)*width)/(numberCircles+1),   // x value
                                              0)  ;                                   // y value
  } // END FOR
 }
```
**change the y value**
```processing
void draw(){                                                                          // --- DRAW ---
  background(255, 255, 225);                                                          // background color is off white
  
  for ( int circle = 0; circle < numberCircles ; circle ++){                          // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ].display();        //  - display the circle
  
      // - change values before next run
    circlesArray[ circle ].fall();                                                    //  - move the circle down by 1 pixels 
  
} // END FOR
```

#### Code Check In
The code currently looks like:
```processing
/*  Lab 2B - NMD 211
    FirstName LastName
    September 16, 2020
    
    
    Object arrays
    - create basic object
    - make 5+ objects with an array
    - motion
*/
ColorCircle[] circlesArray;                                                           // declare global array

// - global variables & other constants
int numberCircles = 5;                                                                // number of circles

void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
  // - place each circle in the array
  for ( int circle = 0 ; circle < numberCircles ; circle ++){                         // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ] = new ColorCircle(                                         // - circleArray value circle is a ColorCircle 
                                              ((1+circle)*width)/(numberCircles+1),   // x value
                                              0)  ;                                   // y value
  } // END FOR
 }
 
void draw(){                                                                          // --- DRAW ---
  background(255, 255, 225);                                                          // background color is off white
  
  for ( int circle = 0; circle < numberCircles ; circle ++){                          // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ].display();        //  - display the circle
  
      // - change values before next run
    circlesArray[ circle ].fall();                                                    //  - move the circle down by 1 pixels 
  
} // END FOR
  
}

class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  float x;                                                                            // local variable storing circle's center x
  float y;                                                                            // local variable storing circle's center y
 
  ColorCircle( float xIn, float yIn){                                                 // - CLASS'S CONSTRUCTOR
    x = xIn;                                                                          // input x value as center x
    y = yIn;                                                                          // input y value as center y
  }
  
  void display(){                                                                     // - DISPLAY CLASS OBJECT
    fill(0);                                                                          // Set color
    ellipse( x , y, 80, 80);                                                          // Draw Shape 
  }
  
  void fall(){                                                                        // - CLASS OBJECT MOTION
    y += 1;
  }
}
```
### Fall at Different Speeds
14. Each circle needs its own travelling speed. 
Make a global array of speeds, above our definition of the method\funtion setup.
```processing
// - global variables & other constants
int numberCircles = 5;                                                                // number of circles
float[] circleSpeeds = {1, 2, 0.5, 0.1, 10};                                          // list of all circle travel speeds
```
15. Add the circle travel speeds into the ColorCircle class constructor, local variables, and local method/function fall, then add the value into the initialization call. 

**Add speed to ColorCircle class**
```processing
class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  float x;                                                                            // local variable storing circle's center x
  float y;                                                                            // local variable storing circle's center y
  float s;                                                                            // local variable storing circle's speed

 
  ColorCircle( float xIn, float yIn, float speed ){                                                 // - CLASS'S CONSTRUCTOR
    x = xIn;                                                                          // input x value as center x
    y = yIn;                                                                          // input y value as center y
    s = speed;                                                                        // input y value as s, the circle's falling speed

  }
  
  void display(){                                                                     // - DISPLAY CLASS OBJECT
    fill(0);                                                                          // Set color
    ellipse( x , y, 80, 80);                                                          // Draw Shape 
  }
  
  void fall(){                                                                        // - CLASS OBJECT MOTION
    y += s;
  }
}
```
**ColorCircle Class initialization with speed**
```processing
void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
  // - place each circle in the array
  for ( int circle = 0 ; circle < numberCircles ; circle ++){                         // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ] = new ColorCircle(                                         // - circleArray value circle is a ColorCircle 
                                              ((1+circle)*width)/(numberCircles+1),   // x value
                                              0,                                      // y value
                                              circleSpeeds[circle]);                   // - speed = speed from our list

  } // END FOR
 }
```
#### Code Check In
The code currently looks like:
```processing
/*  Lab 2B - NMD 211
    FirstName LastName
    September 16, 2020
    
    
    Object arrays
    - create basic object
    - make 5+ objects with an array
    - motion
*/
ColorCircle[] circlesArray;                                                           // declare global array

// - global variables & other constants
int numberCircles = 5;                                                                // number of circles
float[] circleSpeeds = {1, 2, 0.5, 0.1, 10};                                          // list of all circle travel speeds


void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
  // - place each circle in the array
  for ( int circle = 0 ; circle < numberCircles ; circle ++){                         // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ] = new ColorCircle(                                         // - circleArray value circle is a ColorCircle 
                                              ((1+circle)*width)/(numberCircles+1),   // x value
                                              0,                                      // y value
                                              circleSpeeds[circle]);                   // - speed = speed from our list

  } // END FOR
 }
 
void draw(){                                                                          // --- DRAW ---
  background(255, 255, 225);                                                          // background color is off white
  
  for ( int circle = 0; circle < numberCircles ; circle ++){                          // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ].display();        //  - display the circle
  
      // - change values before next run
    circlesArray[ circle ].fall();                                                    //  - move the circle down by 1 pixels 
  
} // END FOR
  
}

class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  float x;                                                                            // local variable storing circle's center x
  float y;                                                                            // local variable storing circle's center y
  float s;                                                                            // local variable storing circle's speed

 
  ColorCircle( float xIn, float yIn, float speed ){                                                 // - CLASS'S CONSTRUCTOR
    x = xIn;                                                                          // input x value as center x
    y = yIn;                                                                          // input y value as center y
    s = speed;                                                                        // input y value as s, the circle's falling speed

  }
  
  void display(){                                                                     // - DISPLAY CLASS OBJECT
    fill(0);                                                                          // Set color
    ellipse( x , y, 80, 80);                                                          // Draw Shape 
  }
  
  void fall(){                                                                        // - CLASS OBJECT MOTION
    y += s;
  }
}
```
### (OPTIONAL) Ideas for even more fun code
- Use an if statement in fall to get circles to return to the top once they've reacehd the bottom of the page
- Let each circle have its own fixed radius
- Let each circle have its own fixed color
#### Example of the optional ideas
```processing
/*  Lab 2B - NMD 211
    FirstName LastName
    September 16, 2020
    
    
    Object arrays
    - create basic object
    - make 5+ objects with an array
    - motion
*/

ColorCircle[] circlesArray;                                                           // declare global array

// - global variables & other constants
int numberCircles = 5;                                                                // number of circles
int circleRed = 0;                                                                    // starting red value

int[] circleRadiuses = {2, 47, 17, 100, 60};                                          // list of all circle radiuses
float[] circleSpeeds = {1, 2, 0.5, 0.1, 10};                                          // list of all circle travel speeds

void setup(){                                                                         // --- SETUP ---
  size(500,500);                                                                      // drawing surface size
    
  noStroke();                                                                         // no outlines 
  ellipseMode( CENTER );                                                              // ellipses drawn (x,y,w,h)
  
  // - set aside space for the array of colored cirlces
  circlesArray = new ColorCircle[ numberCircles ];
  // - place each circle in the array
  for ( int circle = 0 ; circle < numberCircles ; circle ++){                         // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ] = new ColorCircle(((1+circle)*width)/(numberCircles+1),    // - circleArray value circle is a ColorCircle 
                                                                                      //   object with x (1+circle)*width)/(numberCircles+1)
                                             0,                                       // - y = 0 
                                             circleRadiuses[circle],                  // - radius = radius from our list
                                             circleSpeeds[circle]);                   // - speed = speed from our list
  } // END FOR
}

void draw(){                                                                          // --- DRAW ---
  background(255, 255, 225);                                                          // background color is off white
  
  for ( int circle = 0; circle < numberCircles ; circle ++){                          // for each circle in circles 0, 1, 2, 3, 4
    circlesArray[ circle ].display();                                                 //  - display the circle
    
    // - change values before next run
    circlesArray[ circle ].fall();                                                    //  - move the circle down by speed pixels  
    circleRed += 50;                                                                  //  - increase red value by 50
  } // END FOR
  
  // - Have cycled through all circles in list
  circleRed = 0;                                                                      // reset red value to 0
}

class ColorCircle{                                                                    // --- CLASS COLORCIRCLE ---
  float x;                                                                            // local variable storing circle's center x
  float y;                                                                            // local variable storing circle's center y
  int r;                                                                              // local variable storing circle's radius
  float s;                                                                            // local variable storing circle's speed
  
  ColorCircle( float xIn, float yIn, int rad , float speed ){                         // - CLASS'S CONSTRUCTOR
    x = xIn;                                                                          // input x value as center x
    y = yIn;                                                                          // input y value as center y
    r = rad;                                                                          // input rad value as r, the circle's radius
    s = speed;                                                                        // input y value as s, the circle's falling speed
  }
  
  void display(){                                                                     // - DISPLAY CLASS OBJECT
    fill( circleRed , 50, 255, 200);                                                  // Set color
    ellipse( x , y, r, r);                                                            // Draw Shape 
  }
  
  void fall(){                                                                        // - CLASS OBJECT MOTION
    if ( y < height + (height/5)){                                                    // if the object is above a certain y value (hasn't reached so far down the bottom of the screen yet)
      y += s;                                                                         // move forward by s pixels
    }
    else {                                                                            // the object has reached the lower edge
      y = - height/5 ;                                                                // return to above top
    }
    
  }
}
```
## Submit below
[FirstName LastName - 2C](example.com)
