# LAXX

Light weight vanilla javascript plugin to do awesome things when you scroll!!

## Demos


## Getting started

1) Add laxx.js to your html page

```
<script src="js/laxx.js" >
```


2) Initialize the plugin 

```
window.onload = function() {
	laxx.setup({ /* opts */ }) // init
	  
	document.addEventListener('scroll', function(e) {
	  laxx.update(window.scrollY) // update every scroll
	}, false)

	laxx.update(window.scrollY) // set initial positions
}
```


3) Add attributes to HTML tags you want to animate, either by using presets:
```
<p laxx-preset="spin fadeInOut">Look at me goooooo!</p>
```
or creating your own animations:
```
<p laxx-translate-y="200 100, 0 -100">Look at me goooooo!</p>
```

4) Scroll and enjoy!

## Presets

The easiest way to get started is to use the built in presets. E.g.
```
<p laxx-preset="spin fadeInOut">Look at me goooooo!</p>
```
The available presets are:
```
linger, lazy, eager, slalom, crazy, spin, spinIn, spinOut, 
blurInOut, blurIn, blurOut, fadeInOut, fadeIn, fadeOut, driftLeft, 
driftRight, slideLeft, slideRight, zoomInOut, zoomIn, zoomOut
```

## Custom Animations

You can easily create your own effects. Just add a the correct attr to your tag (see table below) and set an array of values. These arrays take the format of `[scrollPos val, ...]` e.g:
```
<p laxx-opacity="0 1, 100 1, 200 0">I start to fade out after the window scrolls 100px and then I'm gone by 200px!</p>
```


By default the scrollPos is `window.scrollY` but you can set an anchor element which will adjust the scrollPos by the elements offsetTop. You can either pass in a selector `laxx-anchor="#bio"` or set it to use itself `laxx-anchor="self"` e.g.
```
<p laxx-opacity="-200 1, -100 1, 0 0" laxx-anchor="self">I start to fade out after I'm 100px away from the top of the window and then I'm gone by the time I reach the top!</p>
```

There are some shortcuts for useful values: 

| Key     	| Value           |
| ------------- | ------------- |
| vw       	| window.innerWidth  |
| vh     	| window.innerHeight |
| elw     	| targetElement.clientHeight |
| elh     	| targetElement.clientWidth |

You can use these instead of integer values for the scrollPos  e.g.
```
<p laxx-opacity="0 1, vh 0">I fade out as the page scrolls down and I'm gone when the page has scrolled the view port height!</p>
```

You can also do calculations using `( )` e.g.
```
<p laxx-opacity="0 1, (vh*0.5) 0">I fade out as the page scrolls down and I'm gone when the page has scrolled half the view port height!</p>
```

### Supported Animation Keys

Transforms

| Transform     | Key           |
| ------------- | ------------- |
| opacity       | laxx-opacity  |
| translate     | laxx-translate |
| translateX     | laxx-translate-x |
| translateY     | laxx-translate-y |
| scale     | laxx-scale |
| scaleX     | laxx-scale-x |
| scaleY     | laxx-scale-y |
| skew     | laxx-skew |
| skewX     | laxx-skew-x |
| skewY     | laxx-skew-y |
| rotate     | laxx-rotate |

Filters (note - these may be unperformant on low powered machines)

| Filter     | Key           |
| ------------- | ------------- |
| brightness       | laxx-brightness  |
| contrast     | laxx-contrast |
| hue-rotate     | laxx-hue-rotate |
| blur     | laxx-blur |
| invert     | laxx-invert |
| saturate     | laxx-saturate |
| grayscale     | laxx-grayscale |

## Scroll Wheels
Scroll wheels only icrement the scroll position in steps which can cause the animations to look janky. You can use the SmoothScroll (http://www.smoothscroll.net/) plugin to smooth this out, however there maybe performance implications that need investigating.

## To Do
* Add "momentum" as option for anchor & presets
* Optimise elements that go off screen
* Better error reporting

