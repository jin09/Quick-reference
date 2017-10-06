# C++ Quick Reference For Myself

### Max Heap STL

```c++
priority_queue <int> pq;
    
pq.push(5)
pq.push(1)
   
pq.empty()
        
pq.top()
       
pq.pop()
```
### Min Heap STL

Generic Template

```c++
priority_queue <Type, vector<Type>, ComparisonType > min_heap;
```

Example

```c++
priority_queue <int, vector<int>, greater<int> > pq;

pq.push(5);
pq.push(1);

pq.empty();

pq.top();

pq.pop();
```
