# Website Performance Optimization
This is Project 4 of Udacity's [https://www.udacity.com/course/front-end-web-developer-nanodegree--nd001](Front-End Web Developer Nanodegree). The task was to optimize a given site in such a way that it achieves

1. a [https://developers.google.com/speed/pagespeed/insights/](PageSpeed Insights) score of 90 or higher
2. a consistent framerate of 60 FPS when scrolling
3. a resize time of 5 ms or less when using the resize slider

## Viewing the Project
You can view the site on [https://github.com/](GitHub) or locally on your own machine. 

### On GitHub
Point your browser at [gnuffer.github.io/frontend-nanodegree-mobile-portfolio](gnuffer.github.io/frontend-nanodegree-mobile-portfolio).

### Locally
1. Download [https://git-scm.com/](Git).  Instructions can be found [https://git-scm.com/downloads](here).
2. Clone the repo:
``` bash
$ git clone https://github.com/gnuffer/frontend-nanodegree-mobile-portfolio
```
3. Open index.html in your browser.

### Serving the site
Once you have installed the project locally, you can make it accessible remotely by serving it.

1. Install [https://www.python.org/downloads/](Python) 

2. Install [https://ngrok.com/](ngrok) to the top level of the project directory. 

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
The project can now be accessed remotely at one of the URL's ngrok provides.

### Directory Structure
The project's root directory contains two subdirectories, src and dist, which contain the development files and the production files, respectively. The production index.html file is in the root directory, the developer version is called "srcindex.html" and is in the src directory. The package.json file in the root directory contains the npm scripts used as build tool. 

### Build Instructions
To build the site on your own machine, 

1. Download [https://www.npmjs.com/get-npm](Node.js and npm)

2. navigate to the project directory
```
$ cd /path/to/project-directory
```
3. install package dependencies
```
$ npm install
```
4. return production files to their pre-build state 
``` 
$ npm run reset:all
```
5. build
```
$ npm run build:all
```

### Optimizations to ensure a minimum [https://developers.google.com/speed/pagespeed/insights/](PageSpeed Insights) score of 90 for index.html 
#### Manual changes to index.html
 - added `media="print"` attribute to link tag to external print styles sheet
 - added `async` attribute to script tags
 - moved scripts to end of body
 - replaced unsafe Google Analytics URL with safe URL (`https`)
 - inserted Google Web Font Loader script at the end of body
#### Automated changes with npm scripts
 - minified html, css, and js files
 - inlined css
 - resized and optimized images
### Optimizations to ensure a consistent frame rate of 60 FPS when scrolling
#### Manual changes to views/js/main.js
 - refactored the `updatePositions` and `DOMCONTENTLOADED` callback functions
 - got rid of unnecessary variables `col` and `s`
 - used `requestAnimationFrame` to update positions on scroll
 - applied `transformX` to sliding pizzas in `updatePositions` function
 - moved variables that require DOM-access out of for-loops, thereby reducing the number of times the DOM needs to be accessed
 - dynamically recalculated the number of elements of the mover-class, thereby greatly reducing render and paint work
### Optimizations to ensure a maximum resize time of 5 ms when using the pizza size slider
 - refactored `changePizzaSizes` function
 - optimized for-loops
### Resources on npm scripts as build tool
 - [https://docs.npmjs.com/misc/scripts](npm scripts)
 - [https://gist.github.com/PurpleBooth/109311bb0361f32d87a2](a template to make a good README)
 - [https://github.com/damonbauer/npm-build-boilerplate/blob/master/package.json](NPM Build Boilerplate)
 - [https://www.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/](Keith Cirkel, How to Use npm as a Build Tool) 
 - [https://css-tricks.com/why-npm-scripts/](Damon Bauer, Why npm Scripts?)
 - [https://code.tutsplus.com/courses/npm-scripts-for-build-tooling](Andrew Burgess, npm Scripts for Build Tooling)
 - [https://medium.com/@dabit3/introduction-to-using-npm-as-a-build-tool-b41076f488b0#.3bf2erm9l](Nader Dabit, Introduction to Using NPM as a Build Tool)
 - [https://www.sitepoint.com/guide-to-npm-as-a-build-tool/](Peter Dierx, Give Grunt the Boot! A Guide to Using npm as a Build Tool)
 - [https://hackernoon.com/simple-build-tools-npm-scripts-vs-makefile-vs-runjs-31e578278162#.wnexeou8d](Pawel Galazka, Simple Build Tools: npm Scripts vs Makefile vs runjs)
 - [http://clickherelabs.com/2016/03/npm-as-a-build-tool/](Muriel Gonzalez, NPM as a Build Tool)
 - [https://medium.freecodecamp.com/why-i-left-gulp-and-grunt-for-npm-scripts-3d6853dd22b8#.7dzhn7wjj](Cory House, Why I left Gulp and Grunt for npm Scripts)
