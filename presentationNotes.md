# Matching Dimensions

- think of svg like infinite graph paper and the game battleship
- `<svg width="115" height="190"...` this is called viewport
- `viewBox="0 0 115 190"...` callled viewbox
- click on codepen and add `border: 1px solid black`
- read it
- Q: how would svg look if we were to change these values around? For example: in viewBox, remove 50px for each
- it may be counter-intuitive at first
- click other codepen link (the one with square star etc. and play with values)

# Reduced viewBox

- A: it looks like this
- notice height/width is same as last slide
- read it / explain it using graph paper analogy

# Viewbox

- a very useful tool to learn about SVG viewbox
- if you move width to 200 and height to 300 it's counter-intuitive/gets bigger
- similarly, if you increase the width/height, then image gets smaller -- do you see why now?
- so this tool helps give you a mental model of what's happening under the hood of svg height/width
- preserveAspectRatio - you'll hardly ever use this
- click link [Understanding SVG Coordinate systems] - they wrote 3 articles on understanding svg better

# Expanding viewPort

- so let's see what happens if we change the values the other way
- compared to the 1st example, we're leaving the viewbox values as is
- but this time we're going to expand the view port (originally we had values that were less than this)
-

# Altering min values

# optimize SVGOMG

# Introducing morphSVG plugin

- this is one of those things where when I first saw it, it blew me away
- so I will let you experience what I experienced
- instead of me putting a codepen with code already there, I'll let you build it from scratch
- One of the more exciting features that Greensock has is something called morphSVG
- it mutates shapes beautifully which you saw in last week's Star Wars animation
- the syntax is like this, just put it as one of the properties
- 1st id is your first svg path, 2nd id is your svg path - it has to be a path

# GSAP plugins codepen

-
