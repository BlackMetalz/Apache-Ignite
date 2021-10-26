# 1. In-Memory Data Grid

# 2. Off-heap Memory
- evicted / expire object can be be figured to push down into DBMS
- off-heap memory, this mean it doesn't affected by heap of JVM, store objects outside of the heap to avoid garbage collection cycles
- there is a configuration that allow push data from on heap into off heap after a certain threshold or we can decide. It is really is a simple configuration
