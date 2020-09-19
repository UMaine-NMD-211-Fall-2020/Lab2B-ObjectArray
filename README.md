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
  background(255, 255, 225);                                                          // background color is white
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
6. At the very top of the page, above setup and below initial comments, declare that there will be an array of ColorCircle objects. 
Then, instanatiate the ColorCircle object array inside of setup
```processing
ColorCircle[] circlesArray;                                                           // declare global array
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
### Display ColorCircle Object
8. At the very top of the page, below comments, declare that there will be an array of ColorCircle objects. 
```processing

```

## Submit below
[FirstName LastName - 2C](example.com)
