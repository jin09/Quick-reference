# C++ Quick Reference For Myself

### Max Heap STL

```c++
priority_queue <int> pq;
    pq.push(5);
    pq.push(1);
    pq.push(10);
    pq.push(30);
    pq.push(20);
    
    // One by one extract items from max heap
    while (pq.empty() == false)
    {
        cout << pq.top() << " ";
        pq.pop();
    }
    ```
