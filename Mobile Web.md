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

### Input Client Side Validations

We can use the pattern property in input tags to specify regular expression to match  
![Image](../master/assets/input_patterns.png?raw=true)

### Input `required` and `placeholder`

If `required` is present, then you cannot submit the form until that filed is filled.  
`placeholder` property is used to give hints to the input fields.  

![Image](../master/assets/Required_placeholder.png?raw=true)

### Always wrap inputs in `label`

They increase the area of the input that can be touched.  

![Image](../master/assets/label.png?raw=true)

### Tel Hrefs

We can dial numbers using this link `<a href="tel:+919988776644">DIAL</a>`

![Image](../master/assets/tel_href.png?raw=true)

## 9. Sensors

### Video and Audio

**Get camera and audio access on web**  

![Image](../master/assets/camera_and_audio.png?raw=true)

**What is the problem with this approach?**  

![Image](../master/assets/capture_issues.png?raw=true)

**We can directly get media stream without leaving current application**  

![Image](../master/assets/right_media.png?raw=true)

If I want to capture a snapshot I use the following:  

![Image](../master/assets/take_snapshot.png?raw=true)

**We can choose what camera to capture content from - front facing or primary**  

![Image](../master/assets/camera_sources.png?raw=true)

### Geolocation

![Image](../master/assets/geolocation.png?raw=true)

### Accelerometer

![Image](../master/assets/accelorometer.png?raw=true)

**What to use when?**  

![Image](../master/assets/orientation_vs_motion.png?raw=true)

![Image](../master/assets/device_motion_code.png?raw=true)

### Vibration On Web

![Image](../master/assets/vibration.png?raw=true)

## 10. Offline and Storage

### Always code offline first app

![Image](../master/assets/offline_first.png?raw=true)

### Storage: HTML5 Application Cache (aka Appcache)

We start by specifying the manifest file in the main `<html>` tag  
```html
<html manifest="manifest.appcache">
   <head>
   </head>
</html>
```

This file `manifest.appcache` may look something like this:  

```appcache
CACHE MANIFEST
#version 1.0

CACHE:
bower_components/requirejs/require.js
favicon.ico
styles/aab0066e.main.css
scripts/1396e6bc.main.js
scripts/vendor/f7f27360.modernizr.js
images/icon.png
images/favorite_icon.png
images/schedule_bg.png
images/locate_icon.png
images/filter_icon.png
images/Roboto-light.woff
images/Roboto-medium.woff
images/Roboto-bold.woff
images/maptiles/floor0-v2.svg
images/maptiles/floor1-v2.svg
images/maptiles/floor2-v2.svg
images/mapmarkers/food.svg
images/mapmarkers/info.svg
images/mapmarkers/power.svg
images/mapmarkers/room.svg
images/mapmarkers/toilet.svg
images/profiles/chris_wilson.jpg
images/profiles/colt_mcanlis.jpg
images/profiles/eric_bidelman.jpg
images/profiles/matt_gaunt.jpg
images/profiles/paul_kinlan.jpg
images/profiles/peter_lubbers.jpg
images/profiles/sam_dutton.jpg
images/profiles/sandro_paganotti.jpg
json/sessions/session01.json
json/sessions/session02.json
json/sessions/session03.json
json/sessions/session04.json
json/sessions/session05.json
json/sessions/session06.json
json/sessions/session07.json
json/sessions/session08.json
json/sessions/session09.json
json/speakers/chris_wilson.json
json/speakers/colt_mcanlis.json
json/speakers/eric_bidelman.json
json/speakers/matt_gaunt.json
json/speakers/paul_kinlan.json
json/speakers/peter_lubbers.json
json/speakers/sam_dutton.json
json/speakers/sandro_paganotti.json
json/maps.json
json/schedule.json
json/speakers.json

# / is wildcard for all pages  
# so, for all pages, offline.html will be displayed if the user is offline
# NB path is relative to this file
#FALLBACK:
#/ offline.html

# Resources that require the user to be online
NETWORK:
http://www.google-analytics.com/ga.js
http://maps.googleapis.com/
http://maps.gstatic.com/
http://mt0.googleapis.com/
http://mt1.googleapis.com/
http://csi.gstatic.com/
http://fonts.googleapis.com/
http://themes.googleusercontent.com/


#*
```
**Note:** When the user loads the page for the first time, it will hit the server and  
download relevant resources and create a local cache in browser. The next time request  
is made to that page, the resources under the `CACHE` section of `manifest.appcache`  
gets loaded locally and no server request is made.

**Problem:** When I make a change in the future, the app still loads from cache and the change  
doesn't take effect.  

**How to fix this problem?**  
Whenever we make a change, we should also change the version of the `manifest.appcache` file  
by chaging the `2nd line` of `manifest.appcache`.  
This way the resources would first be loaded from server and then the cache will be updated.  

**Problem with using the Appcache `manifest file`**

![Image](../master/assets/manifest_challenge.png?raw=true)

**Concept:** When the manifest file changes on the server, the manifest on my  
local machine is updated asynchronously when the page is fetched.  
Since our app is offline first, the page may already be done loading from the old cache  
In order to get the latest one, we need to refresh again.  
Luckily we can capture the event of cache getting updated and then reload page from javascript  

```javascript
// Check if a new cache is available on page load.
window.addEventListener('load', function(e) {

  window.applicationCache.addEventListener('updateready', function(e) {
    if (window.applicationCache.status == window.applicationCache.UPDATEREADY) {
      // Browser downloaded a new app cache.
      if (confirm('A new version of this site is available. Load it?')) {
        window.location.reload();
      }
    } else {
      // Manifest didn't changed. Nothing new to server.
    }
  }, false);

}, false);
```

### Local Data Storage

![Image](../master/assets/local_storage_types.png?raw=true)

**1. JS LocalStorage**  

![Image](../master/assets/local_storage.png?raw=true)

In order to store binalry files or sturctured data, we have WEBSQL API and Indexed DB

**2. WebSQL**  
It is no longer supported by the developer, it is dead end.  
Use at your own risk. It is present in Chrome, Safari, Firefox  

**3. Indexed DB**  
Right choice for storing complex data  

![Image](../master/assets/indexed_db.png?raw=true)
