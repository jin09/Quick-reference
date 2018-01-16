# Mobile Web Dev

## 1. Setup the Environment

1. Connect the mobile in USB Debugging mode  
2. Open `chrome://inspect` on development machine(Desktop)  
3. Forward port `9000` to `localhost:8080` so that ew can access the  
   local server of machine on port 9000 inside mobile browser

## 2. Viewport and UX

Lets say I have a website that is viewed on a desktop of width 980px width  
I want to view this website on mobile, but mobile width is 320 px  
So the browser fakes the width to be 980px on the mobile and so the all the data looks small  

**How can we avoid this?**  
We can use the html `meta viewport` tag to specify the dimensions of device  

```html
<head>
   <meta name="viewport" content="width=320">
</head>
```
**Note:** Whenever you are testing your app and making changes to the `meta viewport` tag,  
then always close that tab and reopen instead of refreshing the page.  
Refreshing the page doesn't have any efeect on the `viewport` to take effect.  
So always make sure to reopen that tab.  

**Problem**  
Our website doesn't need to be opened on a devie of width 320, it has to be more versatile than that.  
So how do we cater to the problem of dynamic viewport width?  

```html
<head>
   <meta name="viewport" content="width=device-width">
</head>
```

### Set Initial Zoom Level

```html
<head>
   <meta name="viewport" content="width=device-width, intial-scale=1.0">
</head>
```
We can also set maximum-scale and minimum-scale in the cotent property of `viewport metatag`  
which basically tells the zoom range  

### Lock zoom  

```html
<head>
   <meta name="viewport" content="width=device-width, intial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
</head>
```
## 3. Fluid Layout

Stop fixing height and width in terms of pixcels or points, instead move towards  
**Percentages and EM**  
![Image](../master/assets/fluid_layout.png?raw=true)

### Two rules for fluid layout  
![Image](../master/assets/2_rules.png?raw=true)

### New CSS property that takes care of fluid layout

![Image](../master/assets/flex.png?raw=true)

## 4. Media Queries

So should we use fluid design for all devices? This way the website would open the  
same way on all the devices - mobile, desktop, tablet.  
We don;t really want to do such a thing. We want to load website differently on  
all the different types of devices.  

![Image](../master/assets/media_1.png?raw=true)  

![Image](../master/assets/media_2.png?raw=true)

### Available Expressions on Media Query 

![Image](../master/assets/media_3.png?raw=true)

## 5. Responsive Images

Client should request the right copy of image based on the device information  
Mobile devices should be sent different copy of that image(maybe cropped)  
On desktop the client should receive a full version of the image  

## 6. Performance 

Performance depends on 3 things -  
**1. Network  
2. Render  
3. Compute**  

![Image](../master/assets/3_pillars.png?raw=true)

Become a chrome dev tools ninja if you want to be able to analyse the performance.  

### Network  
Check the number of requests  
check the size of each request  
**Fun Fact:** Average size of a webpage on internet is 1.1 MB,  
if yours crosees that, then it is already exceeding the limit  

### Render

Go to chrome dev tools and record activity under the  
`Timeline` tab. It will show the time taken by each event in realtime.  
We can also view the memory allocation and garbage collection as we work inside the app.  

![Image](../master/assets/activity_chrome.png?raw=true)

### Compute

In order to analyze the compute time of javascript program,  
we can use the `Profile` tab of chrome dev tools.  

![Image](../master/assets/profile_chrome.png?raw=true)

These coloured pillars are the computation frames, zooming it shows  
us the time taken to execute each function in javascript. These pillars  
are spaced by program time, which is when chrome takes control to do its thing  
and give CPU to the program again. (Just like pre-emption)  

**Follow the memory**  
If we want to improve perfomance, check the memory allocations during the run of app.  
Use the `Record Heap Allocations` under the `Profile tab` of chrome dev tools to do so.  

**Must Remeber Trick**  
`Take Snapshot` under `Profile Tab` gives us the info of all the memory allocated till that  
point including the system level allocations.  
Take another snapshot and filter objects that were created between these 2 snapshots.  
This is a beautiful way to find **delta**  

### Minimize Network Latency

![Image](../master/assets/min_net_lat.png?raw=true)

### Memory constraint  

![Image](../master/assets/mem_constraint.png?raw=true)

**Quick Tip:** Use lighter libraries that are small and fast.  
Like for example using `zepto` instead of `jQuery`.  

### Render Optimisation

We want all the animations to be smooth and consistent.  
We should have an animation frame rate of 60 FPS to call our app smooth.  

![Image](../master/assets/render_opt.png?raw=true)

## 7. Touch UX

![Image](../master/assets/touch.png?raw=true)

### Touch events

![Image](../master/assets/touch_events.png?raw=true)

### Polymer's Polyfill for touch and pointer events

Polyfill library helps us work with pen events, touch and pointer events  
simultaneously.  
We should use it for handling all the touch events.  

## 8. Inputs
We sometime note that, taking input for a number also pops a regular keyboard.  
to avoid this we can make good use of the `type` property of input fields.  

![Image](../master/assets/input_types.png?raw=true)
