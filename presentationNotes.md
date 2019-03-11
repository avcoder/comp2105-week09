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

# Altering min values

- before we had 0 0 for the viewBox but now it's 50 30
- so the viewbox starts from a different position other than 0 0
- analogy: viewbox is like a window of a house
- analogy: sprite image - which part to focus on?

# preserveAspectRatio

- 9/10 you'll hardly ever need to change the default `xMidYMid meet`
- experiment different values with https://codepen.io/avcoder/pen/Lajvmo
- for `preserveAspectRatio: none` click on last image to get to https://webanimationworkshops.com (Inspect triangle)

# optimize SVGOMG

- according to Sarah Drasner, she always uses SVGOMG tool to optimize her SVGs - best workflow
- Adobe Illustrator save it as an SVG
- before I click on SVGOMG, click link [Sitepoint] where it gives 3 ways to optimize SVG
- here's sitepoint's instance where you have generated code where you have a lot of junk
- but in reality all you really need is the bare minimum
- similar to if you were to save a Word document as an html page
- try opening up cat.svg (from undraw.co/illustrations) and then toggle "Show original" to see % optimized
- toggle prettify markup
- so your in-class exercise today, I've asked you to use this optimizer
- the other 2 tools for optimization are a little older (3rd one is text based and uses node)

# Introducing morphSVG plugin

- this is one of those things where when I first saw it, it blew me away
- so I will let you experience what I experienced
- so instead of me putting a codepen with code already there, I'll let you build it from scratch - it'll be better as a learning perspective
- One of the more exciting features that Greensock has is something called morphSVG
- it mutates shapes beautifully which you saw in last week's Star Wars animation when it changed all those faces
- the syntax is like this, just put it as one of the properties
- 1st id is your first svg path, 2nd id is your svg path - it has to be a path
- read it

# GSAP plugins codepen

- What's cool about morphSVG is that Greensock has a partnership with codepen in that you can tryout their usually paid plugins, for FREE on codepen only
- not only morphSVG but all their other paid plugins, so you can play with this as much as you like
- so let's copy morphSVG library and create a codepen
- read it

# Intro to { morphSVG: "#" }

- okay so here are the different steps 1 thru 8
- I'm asking you to create a new codepen from scratch and play with morphSVG

1. so go into your codepen, include TweenMax and morphSVG plugin

   - let's click on gear icon, search for TweenMax, codepen adds it
   - unforunately if you search for morphSVG it won't find it and that's the purpose of the previous slide
   - copy morphSVG path and paste it into codepen's JS - so now your codepen has both libraries

2. grab 2 svg icons (after we try this out you can experiment with your own SVGs later)

   - so here's the amazon icon where someone has created some svg icons for the different brands
   - click Raw copy/paste it into codepen
   - so that's the 1st svg
   - let's grab the apple icon now and do the same
   - so that's the 2nd svg

3. make an id name for each path

   - Q: why paths only and not rect etc.?
   - A: because morphSVG only works on paths
   - Q: what if I don't have paths but only rect star etc
   - A: use morphSVGPlugin.convertToPath() https://greensock.com/morphSVG

4. Add `TweenMax.to("#amazon", 1, { morphSVG: "#apple"})`

   - cool eh?

5. add a 1.5 delay

   - `{..., delay: 1.5}`

6. hide 2nd logo

   - `#applelogo { display: none; }`

7. Change colour

- Have to target rect to change colour
  ```js
  TweenMax.to("#amazon", 1, { morphSVG: "#apple", delay: 1.5 });
  TweenMax.to("#amazonlogo rect", 1, { attr: { fill: "#555" }, delay: 1.5 });
  ```

# GSAP Review

- so last week you learned the .to, .from, .set
- so here we have a timeline
- Q: What do you expect would happen if I click this Run button?
- the essential code is here; the green refers to green box etc.
- since we're using a .to, everything listed here is the end destination
- 0% is where it's at; 100% is where it's going
- use sliders: because we're using a timeline, the 2nd statement will occur after 1st statement
- it should move green box 1s to the right
- followed by that, blue square, then orange square

# Introducing the position parameter

- so in addition to your target, duration, props, you now also have the allowance to put a position parameter
- and this is the secret to make beautiful sequences with precise timing - use of position parameter
- read top/bottom

# Use of position to allow for gaps +=1

- there are a handful of ways you can use position paramter; last week I showed you how to add/use a label
- here i'm using a position parameter of +=1
- it'll insert 1 second between 1st and 2nd one
- before I click run, the green square will run 1s
- normally this blue square would run after it, but since it has +=1, it'll wait 1s
- so in reality (use slider) blue square starts here instead
- similar to the last square
- so I would expect when I click run that it would run like this
- [click run]

# Use position to allow for overlaps -=1

- Q: what do you expect will happen here?
- the green square will run 1s
- the blue square will normally go here, but because it has -=.5, before the first square's animation ends, this one starts

# Use position as an absolute value

- read it
- here I specified 2 and 2.5
- so the first one has no position parameter
- The 2nd one would normally occur here
- now remember it starts at 0
- 2.5 occurs here
- so that's the animation I would expect
- [click run]

# Use position to set a label, OR specify where a tween should be placed
