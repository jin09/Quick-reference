# Scalable Apps in Python

## How to increase capacity of single application?

![Image](../master/assets/increase_capacity.png?raw=true)
Solution sounds simple. But is it really?  

## Have we really solved the problem of scalability or are we missing anything?

![Image](../master/assets/is_problem_solved.png?raw=true)
We have missed so many aspects to the problem of scalabilty  

## What should be done?  

Google App Engine takes care of all of it for us.  
When app is busy, it scales up  

![Image](../master/assets/scale_up.png?raw=true)  

When app is IDLE, it scales down automatically  

![Image](../master/assets/scale_down.png?raw=true)  

Google Cloud Platform also manages other shortfalls that we missed for us..  

## Support different devices

![Image](../master/assets/cloud_endpoints.png?raw=true)  

## Datastore Modelling

![Image](../master/assets/datastore_modelling.png?raw=true)  

## Datastore Analogy

![Image](../master/assets/datastore_analogy.png?raw=true)  

## Datastore queries

```python
import db from google.ext.datastore

class Users(db.Model):
  name = StringProperty()
  user_id = IntegerProperty()
  
# Makes a query object of a kind
query_obj = Users.query()

# filter the contents
query_obj.filter(Users.name == 'sam')

# Order the result
query_obj.order(Users.name)

query_obj.get() # Gets 1 st result
query_obj.fetch() # Gets all results
query_obj.fetch(5) # Gets first 5 results

for result in query_obj:
  # iterate the cursor

```

## Indexing and datastore
By default google datastore indexes all the properties  
It makes it able to query on that property fast.  
But creating index on all the entities is expensive during write operation  
We must create index on only those that are needed  

We can specify which property not to index  

```python
import db from google.ext.datastore

class Users(db.Model):
  name = StringProperty(indexed=False)
  user_id = IntegerProperty(indexed=False)
```

## Composite Indexes

Sometimes when we filter on multiple kinds all together or order them  
then we have to create composite index.  
We need to update the `index.yaml` in that case.  
We can either do it manually or when we first run the app locally  
the google app engine autogenerates the `index.yaml` entry for us.  
Next all we have to do on terminal is :  
```
gcloud app deploy
gcloud app deploy index.yaml
```
Later line is to update indexes on google's cloud

## Datastore commit process

![Image](../master/assets/datastore_commit.png?raw=true)  

## Datastore Transactions

![Image](../master/assets/transactions.png?raw=true)  

Sample code taken from the completed version of conference central
```python

@ndb.transactional(xg=True) # xg stands for cross group, check what it means and where it is used
def _conferenceRegistration(self, request, reg=True):
    """Register or unregister user for selected conference."""
    retval = None
    prof = self._getProfileFromUser() # get user Profile

    # check if conf exists given websafeConfKey
    # get conference; check that it exists
    wsck = request.websafeConferenceKey
    conf = ndb.Key(urlsafe=wsck).get()
    if not conf:
        raise endpoints.NotFoundException(
            'No conference found with key: %s' % wsck)

    # register
    if reg:
        # check if user already registered otherwise add
        if wsck in prof.conferenceKeysToAttend:
            raise ConflictException(
                "You have already registered for this conference")

        # check if seats avail
        if conf.seatsAvailable <= 0:
            raise ConflictException(
                "There are no seats available.")

        # register user, take away one seat
        prof.conferenceKeysToAttend.append(wsck)
        conf.seatsAvailable -= 1
        retval = True

    # unregister
    else:
        # check if user already registered
        if wsck in prof.conferenceKeysToAttend:

            # unregister user, add back one seat
            prof.conferenceKeysToAttend.remove(wsck)
            conf.seatsAvailable += 1
            retval = True
        else:
            retval = False

    # write things back to the datastore & return
    prof.put()
    conf.put()
    return BooleanMessage(data=retval)
```

## Memcache

![Image](../master/assets/memcache.png?raw=true)  

## Task Queues
A response must complete within 60 seconds.  
But let's say that we receive a request which takes hours to complete,  
we can;t keep our user waiting that long right?  
For for very long tasks, we have the concept of task queues
![Image](../master/assets/task_queues.png?raw=true)  

**Where can we use task queues?**  
![Image](../master/assets/task_queues_usage.png?raw=true)  

### Http Request vs Task Queues

![Image](../master/assets/http_vs_task_queue.png?raw=true)  

### 1. Push Queues
App Engine has threads that scan these queues and pick up tasks  
![Image](../master/assets/push_queues.png?raw=true)  

These threads execute each task one by one and call the URL specified  
![Image](../master/assets/push_queues_1.png?raw=true)  

**Execution time for each task is 10 minutes, so bigger tasks should be broken down  
into sub tasks**

### How to create a Push Queue Task?

![Image](../master/assets/task_queues_2.png?raw=true)  
![Image](../master/assets/task_queues_2.png?raw=true)  

```python
from google.appengine.api import taskqueue

# Look for TODO 2
# create Conference, send email to organizer confirming
# creation of Conference & return (modified) ConferenceForm
Conference(**data).put()
taskqueue.add(params={'email': user.email(),
    'conferenceInfo': repr(request)},
    url='/tasks/send_confirmation_email'
)
```

### 1. Pull Queues
App Engine doesn't executes these tasks, they are instead pulled by workers  
using the REST API. If task not completed in time then task is put back  
in the queue. If the external worker doesn't delete the task then also the  
task is put back in the queue.
![Image](../master/assets/pull_queues.png?raw=true)  
