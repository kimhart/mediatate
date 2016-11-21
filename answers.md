#KIM HART ANSWERS

###GITHUB PAGES
View working project [here](https://kimhart.github.io/mediatate/).

###PREFACE

I built this project into a Node/Express server and used Gulp, Sass and Babel for my build just to emulate my normal workflow. I built an npm Sass compiler so I could use Sass over basic CSS, used Babel to compile the ES6 syntax in my JS, and Gulp to compile and minify all my CSS/JS for faster load times. 

###PHASE II

1. What is the difference between these two images?
    * Image1 and Image2 both have identical sources by default, but they each (ideally) receive different version numbers. 

2. What are the implications for how these images load?
    * Running as-is: Both of the images load, but only Image1 assumes a version number. 
    * What happens: The function that assigns a version number to Image2 results in an Uncaught TypeError ("Cannot set property src of null"). 
    * Why it's happening: You're running the Image2 function way up top before the DOM renders, so the src doesn't exist when it runs. Splitting this into different scripts also increases the requests and overall load times.
    
3. What can be done to make these images load correctly with a version number?
    * At its simplest? Move the script to the bottom of the body, under the script for Image1. BUT...
    * I changed it up and made it faster (assuming we didn't want to use jQuery here.) Now this single script is reusable for everything with the class of "image", which I added to our images above.
    * The query string + version number is now dynamically assigned to each image.
    * Note: I concatenated the index rather than adding it to the milliseconds — so from a data collection perspective, you could still pull the accurate milliseconds (if that's important to you) as well as a clear version number at the end of the string, starting at 0.

###PHASE III

1. Using the inline CSS, make a slideshow out of the images.
    * Since we used Bootstrap, I went with their standard built-in carousel. It's not my favorite aesthetics-wise, but in the interest of time it made sense to use.

2. Does where you load the CSS matter?  Please explain.
    * Yes, you have to load Bootstrap first and your custom CSS after — otherwise Bootstrap might overwrite your custom styling.

3. Make it possible to allow a user to "Like" or "Thumbs-up" an image in the slideshow?  This does not require integrating with any third-party services like Facebook and does not need to be saved into a database.
    * When you hover over the slides, a heart icon appears in the center. If you click the icon, it turns red, imitating a "like". (Notes: does not log any real data and would have to be a different design for mobile (no hovering on touch screens).

###PHASE IV

1. On page load, randomly decide what test group a user will be assigned to -- Users should be assigned to a "Control" group or the "Variation" group.
    * This is explained a bit in my JS comments, but I went back to my email marketing days for this test. I used to do a lot of A/B testing with layouts and colors to gauge what got the most clicks and engagement. I did something similar here and assigned a green form submit button as the control group, and a red button as the variation. Figured I'd kill two birds with one stone and do the test on an existing element that measures engagement.

###PHASE V

1. Use Javascript to validate that a user types in an email address
    * I used a combo of HTML5 validation + Bootstrap validation for the error messages (but this only goes so far. You can type something like "no@no" and it will accept it.) I coupled this with a regex pattern to check for a more legit email sequence before it even sends the form data anywhere.

2. Use Javascript to prevent users from submitting their email address more than once
    * This is handled by using jQuery's inArray(). It checks for the object and returns the index number (-1 if it doesn't exist). The logic in the if-statement is pretty straightforward.

3. Use Javascript to display feedback to the user (ie: Thanks for signing up!). Once a user has signed up, consider hiding the form so that users don't sign up again.
    * The form displays either "That email is already in our system!" or "Thank you for signing up!" depending on the array contents. Personally, I think adding the functionality of hiding the form wouldn't matter, since we already prevented them from signing up the same address twice. I simply clear the form on submit so another email can be added. BUT... I added the hide functionality in the comments anyway just for giggles.


