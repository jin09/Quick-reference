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
