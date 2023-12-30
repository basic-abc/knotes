### ELI5
- Least Recently Used (LRU) cache, it holds the head, tail of a bidirectional linked list (self-defined list nodes) alongside a HasMap for fast access

#### Variants
- [716. Max Stack](https://leetcode.com/problems/max-stack/description/?envType=study-plan-v2&envId=premium-algo-100) can be implemented with a TreeMap to track min / max values

### Pitfalls
- Consider helper functions addNode, removeFromPos & updateCache (which calls removeFromPos & addNode to remove & reinsert the element to head)