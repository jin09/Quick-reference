# Offline Web Apps

## Tradition online first experience

![Image](../master/assets/traditional_web.png?raw=true)

## New web reborn

![Image](../master/assets/new_web.png?raw=true)

## Service Workers

### Registering a service worker

```javascript
navigator.serviceWorker.register('sw.js').then(function(reg){
  console.log('Yay!');
}).catch(function(){
  console.log('Boo!');
});
```
**Note:** If I try to re register a service worker then it won't actually re register it  
but would return the corresponding promise.  
