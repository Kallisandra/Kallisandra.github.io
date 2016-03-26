Kallisandra.github.io
#Udacity P5 - This readme details what changed in Dist Folder to optimize the project

Dist folder contains all the modified files
Src folder contains the original source files unmodified

1) Critical Rending Path for index.html
  *Optimize Pagespeed score to 90+ for index.html
  a) Add async tag to google analytics script tag on line 31
  b) Resize and optimize photos: profilepic.jpg and pizzeria.jpg with online webtools such as tinyjpg 
  c) Inline CSS internally to index.html for font.css and print.css and move to footer
  d) Inline style.css by embedding in script tag 

2) Frame rate for pizza.html
   * Increase to 60fps
   * The file that contains all the necessary changes is src/views/js/main.js
   a) function changePizzaSizes(size) has a loop where the variables keep getting called, move them outside of the for             loop, calculate loop with pizzaElementsLength outside loop, assign dx and width with first element of     
      pizzaContainersElement, use getElementsByClassName() Web API call is faster than querySelectorAll
   b) Move var pizzasDiv = document.getElementById("randomPizzas"); outside of the for loop to be declared only once
   c) Replace all the querySelectorAlls with getElementsByClassName in main.js

3) Computation efficienty for pizza.html
  * Resize pizza to less then 5ms 
  * The file that contains all the changes is src/views/js/main.js and src/views/css/style.css
  1) In style.css file change the .mover width to 100px to optimize the width of the mover
  2) main.js function changePizzaSizes
    a) Remove variables pizzaContainers and pizzaContainerslength because they are no longer necessary 
    b) declare a new variable pizzaContainersElements, change dx and newWidth to use only the first instance of     
       randompizzaContainers
    c) for the for loop on line 480, we will reverse the loop to improve performance, this is cited in many websites and I          tested it and this helped my performance 
  3) main.js function updatePositions
    a) Reverse the for loop again to improve performance
    b) this includes changing the logic for the entire loop
    c) function changeSliderLabel, replace getQuerySelector with getElementById, remove # and replace return with break for         faster webAPI
    d) function updatePositions(), move var phase outside of loop, change phase and item logic when reversing loop to mimic  
       correct pizza phasing, change elem.basicLeft to elem.styleLeft to match the logic in the function
    e) declare a new variable numRows to calculate screen.height divided by number of cols to determine number of pizzas used       to fill screen during scroll

4)Comments are included in all the necessary files
5)This is the readme file that includes all the optimizations

