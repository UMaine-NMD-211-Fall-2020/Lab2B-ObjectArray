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
14.
```processing
```
```processing
```
15.
```processing
```
```processing
```
## Submit below
[FirstName LastName - 2C](example.com)
