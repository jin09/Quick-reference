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
