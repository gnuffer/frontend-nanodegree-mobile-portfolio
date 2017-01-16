# Website Performance Optimization
This is Project 4 of Udacity's [Front-End Web Developer Nanodegree](https://www.udacity.com/course/front-end-web-developer-nanodegree--nd001). The task was to optimize a given site in such a way that it achieves a

1.  [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) score of 90 or higher
2.  consistent framerate of 60 FPS when scrolling
3.  resize time of 5 ms or less when using the resize slider

## Viewing the Project
You can view the site on [GitHub](https://github.com/) or locally on your own machine. 

### On GitHub
Point your browser at [gnuffer.github.io/frontend-nanodegree-mobile-portfolio](gnuffer.github.io/frontend-nanodegree-mobile-portfolio).

### Locally
1. Download [Git](https://git-scm.com/).  Instructions can be found [here](https://git-scm.com/downloads).
2. Clone the repo:

    ```
    $ git clone https://github.com/gnuffer/frontend-nanodegree-mobile-portfolio
    ```

3. Open index.html in your browser.

## Serving the Site
Once you have installed the project locally, you can make it accessible remotely by serving it.

1. Install [Python](https://www.python.org/downloads/)

2. Install [ngrok](https://ngrok.com/) to the top level of the project directory. 

3. Set up a local server

    ```
    $ python -m SimpleHTTPServer 8080
    ```

4. Open your browser and visit `localhost:8080`. 

5. Go to the project directory

    ```
    $ cd /path/to/project-directory
    ```

6. Establish a secure tunnel

    ```
    $ ngrok http 8080
    ```

7. Access the project remotely at one of the URL's ngrok provides.

## Directory Structure
The project's root directory contains two subdirectories, src and dist, which contain the development files and the production files, respectively. The production index.html file is in the root directory, the developer version is called "srcindex.html" and is in the src directory. The package.json file in the root directory contains the npm scripts used as build tool. 

## Build Instructions
To build the site on your own machine, 

1. Download [Node.js and npm](https://www.npmjs.com/get-npm)

2. Navigate to the project directory

    ```
    $ cd /path/to/project-directory
    ```

3. Install package dependencies

    ```
    $ npm install
    ```

4. Return production files to their pre-build state 

    ```
    $ npm run reset:all
    ```

5. Build

    ```
    $ npm run build:all
    ```

## Optimizations to Ensure a Minimum [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) Score of 90 for index.html 
### Manual changes to index.html
 - added `media="print"` attribute to link tag to external print styles sheet
 - added `async` attribute to script tags
 - moved scripts to end of body
 - replaced unsafe Google Analytics URL with safe URL (`https`)
 - inserted Google Web Font Loader script at the end of body

### Automated changes with npm scripts
 - minified html, css, and js files
 - inlined css
 - resized and optimized images

## Optimizations to Ensure a Consistent Frame Rate of 60 FPS when Scrolling

### Manual changes to views/js/main.js
 - refactored the `updatePositions` and `DOMCONTENTLOADED` callback functions
 - got rid of unnecessary variables `col` and `s`
 - used `requestAnimationFrame` to update positions on scroll
 - applied `transformX` to sliding pizzas in `updatePositions` function
 - moved variables that require DOM-access out of for-loops, thereby reducing the number of times the DOM needs to be accessed
 - dynamically recalculated the number of elements of the mover-class, thereby greatly reducing render and paint work

## Optimizations to Ensure a Maximum Resize Time of 5 ms when Using the Pizza Size Slider
 - refactored `changePizzaSizes` function
 - optimized for-loops

## Resources on npm Scripts as Build Tool
 - [npm scripts](https://docs.npmjs.com/misc/scripts)
 - [Damon Bauer, Why npm Scripts?](https://css-tricks.com/why-npm-scripts/)
 - [Damon Bauer, NPM Build Boilerplate](https://github.com/damonbauer/npm-build-boilerplate/blob/master/package.json)
 - [Keith Cirkel, How to use npm as a build tool](https://www.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/)
 - [Andrew Burgess, npm Scripts for Build Tooling](https://code.tutsplus.com/courses/npm-scripts-for-build-tooling)
 - [Nader Dabit, Introduction to Using NPM as a Build Tool](https://medium.com/@dabit3/introduction-to-using-npm-as-a-build-tool-b41076f488b0#.3bf2erm9l)
 - [Peter Dierx, Give Grunt the Boot! A Guide to Using npm as a Build Tool](https://www.sitepoint.com/guide-to-npm-as-a-build-tool/)
 - [Pawel Galazka, Simple Build Tools: npm Scripts vs Makefile vs runjs](https://hackernoon.com/simple-build-tools-npm-scripts-vs-makefile-vs-runjs-31e578278162#.wnexeou8d)
 - [Muriel Gonzalez, NPM as a Build Tool](http://clickherelabs.com/2016/03/npm-as-a-build-tool/)
 - [Cory House, Why I left Gulp and Grunt for npm Scripts](https://medium.freecodecamp.com/why-i-left-gulp-and-grunt-for-npm-scripts-3d6853dd22b8#.7dzhn7wjj)
