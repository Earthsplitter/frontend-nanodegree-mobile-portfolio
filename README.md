#What I did

###For index.html
You can check this page by URL: https://earthsplitter.github.io/frontend-nanodegree-mobile-portfolio/<br>
Get 92 on mobile devices and 95 on desktop devices.

####1. images
Download all images and store them locally(**see 2048.jpg, courses.jpg and mobile-develop.jpg in img folder**), so I can do some compress.<br>
Then I compress all of them(**see $-minify.jpg**).

####2. css files
Separate media query for smartPhone in styles.css<br>
Store fonts locally, compress all *.css files(**use WebStorm file watcher automatically do this**), and then make all of them directly in HTML file head by <script\> tag.

####3. javascript files

Move analytics.js to the end of the file, just before <\/body>

###For views/pizza.html
Also see comments in main.js
####1. low fps when scroll down
1. **The most important** In updatePosition function, take `document.body.scrollTop` out of the loop and replace `items[i].basciLeft` with its value `(i % cols) * s`<br>
2. (<em>only did the first optimization cannot reach 60fps</em>)Decrease the number of pizzas, since it's positioned fixed, I think 24(4rows*6cols) is enough on 2K screen.<br>
3. LICM(loop invariant code motion), I did this compiler-level optimization, but I don't know if it works in browser.^_^<br>
####2. quick responsive when using slider
1. source code<br> `var newwidth = (document.querySelectorAll(".randomPizzaContainer")[i].offsetWidth + dx) + 'px';
                 document.querySelectorAll(".randomPizzaContainer")[i].style.width = newwidth;`<br>since we can calculate current width(`[i].offsetWidth`), replace it with a fixed number
                 ratio*windowWidth. Just simple simplification.