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

### We can specify the scope of service worker as well

We can make the service worker work for specific urls also if not all  

```javascript
navigator.serviceWorker.register('sw.js', {
  scope: '/my-app/' 
});
```
![Image](../master/assets/scope.png?raw=true)

### We can have multiple service workers with different scopes

Useful for sites like github-pages

### Default scopes in service workers

default scope is decided by the location of the service-worker file  

![Image](../master/assets/default_scope.png?raw=true)

### What hapeens within a service worker?

We llisten to event and do things that we do generally in js.  

![Image](../master/assets/within.png?raw=true)

### Fetch in service workers

It fetches all the requests that are made by that particular scope  
So all the requests made by that scope goes through the service worker  

```javascript
self.addEventListener('fetch', function(event) {
  console.log(event.request);
});
```

![Image](../master/assets/fetch.png?raw=true)

**2 Major Notes:**  
1. When we register service worker for the first time, it took 2 refreshes for the service worker to work  
2. When we modify the service worker, those changes didn't reflect at all in the console  

### Lifecycle of service workers:  

1. When we load page without service workers then requests goes normally.  

![Image](../master/assets/normal.png?raw=true)

2. When we reload with service worker, then new window replaces the old one,  
and all the content is downloaded again with our new service worker, so only registration takes  
place when you reload, although service worker is now active but is not controlling the page yet.  
So service worker code doesn't work yet.  

![Image](../master/assets/just_loaded.png?raw=true)

So any request made would by pass the service worker because the service worker  
isn't controlling the as of this moment.  

3. Now we reload the page, and now the service worker took control of the page  
and now we see the requests log or whatever we do in the service worker.  

![Image](../master/assets/control.png?raw=true)

4. But when we change the service worker, the changes didn't reflect even on reload, why?  

When we reload, a new version of service worker is downlaoded but it doesn't replace the currently running  
version of sevice worker. As long as there are pages that are using the current version of service worker,  
the new version doesn't replace the curent version. So we either close browser and revisit that webpage, or  
we go to some other page and then come back to this URL. When we return the new version of service worker would have  
replaced the old version and will be controlling the pages.  

![Image](../master/assets/control.png?raw=true)

**Workaround for navigating to someother page and then coming back**  
`SHIFT + F5`  

**There's another way!**  
In chrome dev tools, go to Application, check the option `replace new service worker on refresh`  
this makes development friendly but not user friendly :p  

### Respond to requests yourself  

```javascript
self.addEventListener('fetch', function(event) {
  event.responWith(
    new Response('Hello World!!')
  );
});
```

### We can even set header for the responses we send  

```javascript
self.addEventListener('fetch', function(event) {
  event.responWith(
    new Response('Hello World!!', {
      headers: {'foo': 'bar'}
    })
  );
});
```

### Make requests through fetch 

fetch returns a promise and so we can well use that in our service worker response  
lets first see a sample fetch  

```javascript
fetch('./api/some.json')
  .then(
    function(response) {
      if (response.status !== 200) {
        console.log('Looks like there was a problem. Status Code: ' +
          response.status);
        return;
      }

      // Examine the text in the response
      response.json().then(function(data) {
        console.log(data);
      });
    }
  )
  .catch(function(err) {
    console.log('Fetch Error :-S', err);
  });
```
### Respond with help of `fetch` 

```javascript
self.addEventListener('fetch', function(event) {
  fetch('img/my-photo.jpg')
});
```
**`fetch` may get content from cache first and then the network**  

### Hijackin requests

service worker can do all sorts of stuff, it can make a network call,  
modify the results accordingly.  
Lets see with example  

```javascript
self.addEventListener('fetch', function(event) {
  event.responWith(
    fetch(event.request).then(function(response){
      if(response.status == 404){
        return new Response("Page not Found!!")
      }
    }).catch(function(){
      return new Response('Request failed through the network but im there for you offline :)')
    })
  );
});
```
