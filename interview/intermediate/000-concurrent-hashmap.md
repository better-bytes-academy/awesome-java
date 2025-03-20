### **Internal Working of `ConcurrentHashMap`**
`ConcurrentHashMap` is a thread-safe, high-performance implementation of `Map` in Java, designed for concurrent access by multiple threads. Unlike `HashMap`, which is not synchronized, and `Hashtable`, which synchronizes all operations, `ConcurrentHashMap` provides a more granular locking mechanism to allow better concurrency.

---

### **How `ConcurrentHashMap` Achieves Thread Safety**
1. **Segmented Locking (Java 7 and earlier)**
   - The map was divided into segments (default: 16).
   - Each segment had its own lock, allowing multiple threads to operate on different segments concurrently.
   - This reduced contention and improved performance compared to `Hashtable`, which locks the entire map.

2. **Bucket-Level Locking (Java 8 and later)**
   - Instead of segments, Java 8 replaced them with a finer-grained **bucket-level locking mechanism**.
   - Uses an array of `Node<K, V>` (similar to `HashMap`).
   - Each bucket is protected via CAS (Compare-And-Swap) or synchronized blocks when necessary.
   - Reduces the need for exclusive locks, improving performance.

3. **Concurrent Insertions and Updates**
   - Uses **CAS operations** (`Unsafe.compareAndSwapInt()`) for updates to minimize locking.
   - If multiple threads try to update the same bucket, only one succeeds at a time, ensuring thread safety.

4. **Read Operations**
   - Reads are mostly **lock-free** unless the data is being modified.
   - For fast lookups, `ConcurrentHashMap` does not use locks unless necessary.

5. **Resize Mechanism**
   - Unlike `HashMap`, which resizes with a single-threaded approach, `ConcurrentHashMap` allows **multiple threads** to assist in resizing.
   - Uses a `ForwardingNode` to avoid unnecessary contention during resizing.

---

### **Performance Trade-offs**
| **Factor**           | **ConcurrentHashMap** | **HashMap**  | **Hashtable** |
|----------------------|----------------------|-------------|--------------|
| **Thread Safety**    | Yes, high concurrency | No, not thread-safe | Yes, but with a single lock |
| **Locking Mechanism** | Fine-grained (bucket-level) | No locking | Synchronized on entire map |
| **Read Performance**  | High, mostly lock-free | High | Low due to full synchronization |
| **Write Performance** | Moderate, uses CAS and locks | High (non-thread-safe) | Low (global lock) |
| **Resize Efficiency** | Multi-threaded resize | Single-threaded resize | Single-threaded resize |

### **Key Takeaways**
- `ConcurrentHashMap` achieves thread safety using **bucket-level synchronization and CAS operations**.
- It provides **better scalability** than `Hashtable` due to reduced contention.
- **Read operations are fast**, while write operations use minimal locking.
- **Resizing is more efficient** as multiple threads help in rehashing.
---

Here's a simple Java example demonstrating how `ConcurrentHashMap` works in a multi-threaded environment:

```java
import java.util.concurrent.ConcurrentHashMap;

public class ConcurrentHashMapExample {
    public static void main(String[] args) {
        // Create a ConcurrentHashMap
        ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();

        // Adding some initial values
        map.put("A", 1);
        map.put("B", 2);
        map.put("C", 3);

        // Creating multiple threads to update the map concurrently
        Thread thread1 = new Thread(() -> {
            for (int i = 0; i < 5; i++) {
                map.put("A", map.get("A") + 1);
                System.out.println("Thread 1 updated A to: " + map.get("A"));
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        });

        Thread thread2 = new Thread(() -> {
            for (int i = 0; i < 5; i++) {
                map.put("B", map.get("B") + 1);
                System.out.println("Thread 2 updated B to: " + map.get("B"));
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        });

        // Start both threads
        thread1.start();
        thread2.start();

        // Wait for threads to finish
        try {
            thread1.join();
            thread2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // Print final map content
        System.out.println("Final Map: " + map);
    }
}
```

### **Explanation of the Code**
1. We **create a `ConcurrentHashMap`** with some initial key-value pairs.
2. Two threads (`thread1` and `thread2`) update the values of `"A"` and `"B"` respectively **concurrently**.
3. Since `ConcurrentHashMap` ensures **thread safety**, no `ConcurrentModificationException` occurs.
4. After both threads finish execution, we print the **final state** of the map.

### **Expected Output (may vary)**
```
Thread 1 updated A to: 2
Thread 2 updated B to: 3
Thread 1 updated A to: 3
Thread 2 updated B to: 4
Thread 1 updated A to: 4
Thread 2 updated B to: 5
Thread 1 updated A to: 5
Thread 2 updated B to: 6
Thread 1 updated A to: 6
Thread 2 updated B to: 7
Final Map: {A=6, B=7, C=3}
```
---
Here’s a more advanced example showcasing `computeIfAbsent()`, `computeIfPresent()`, and `forEach()` in `ConcurrentHashMap`:  

```java
import java.util.concurrent.ConcurrentHashMap;

public class AdvancedConcurrentHashMapExample {
    public static void main(String[] args) {
        // Create a ConcurrentHashMap
        ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();

        // Using computeIfAbsent: Adds key only if it's absent
        map.computeIfAbsent("X", key -> 10);
        map.computeIfAbsent("Y", key -> 20);
        System.out.println("After computeIfAbsent: " + map);

        // Using computeIfPresent: Updates value only if key exists
        map.computeIfPresent("X", (key, value) -> value + 5);
        map.computeIfPresent("Y", (key, value) -> value * 2);
        System.out.println("After computeIfPresent: " + map);

        // Using forEach to iterate over entries
        System.out.println("Final Map Entries:");
        map.forEach((key, value) -> System.out.println(key + " -> " + value));
    }
}
```

### **Explanation of Features Used**
1. **`computeIfAbsent(key, function)`**  
   - If the key is **absent**, it computes a value using the provided function and inserts it.
   - If the key is **already present**, it does nothing.

2. **`computeIfPresent(key, function)`**  
   - If the key **exists**, it updates the value using the provided function.
   - If the key **is absent**, it does nothing.

3. **`forEach(biConsumer)`**  
   - Iterates over the map and applies a function to each key-value pair.

### **Expected Output**
```
After computeIfAbsent: {X=10, Y=20}
After computeIfPresent: {X=15, Y=40}
Final Map Entries:
X -> 15
Y -> 40
```

---

### **Why Use These Methods?**
- **Avoid explicit `if-else` checks** while modifying values.  
- **Atomic updates** ensure thread safety.  
- **Better performance** than `synchronized` blocks.  

---
Here's an advanced example that demonstrates using `ConcurrentHashMap` with **parallel streams** and **custom concurrency scenarios**.  

---

### **Example: Using `ConcurrentHashMap` with Parallel Streams**
```java
import java.util.concurrent.ConcurrentHashMap;
import java.util.stream.IntStream;

public class ParallelProcessingExample {
    public static void main(String[] args) {
        // Create a ConcurrentHashMap
        ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();

        // Populate the map with initial values
        IntStream.rangeClosed(1, 5).forEach(i -> map.put("Key" + i, i));

        System.out.println("Initial Map: " + map);

        // Using parallelStream to update values concurrently
        map.keySet().parallelStream().forEach(key -> {
            map.computeIfPresent(key, (k, v) -> v * 2); // Double each value
            System.out.println(Thread.currentThread().getName() + " updated " + key);
        });

        System.out.println("Updated Map: " + map);
    }
}
```

### **How This Works**
1. **Populates `ConcurrentHashMap`** with five key-value pairs.
2. Uses **parallel stream** (`parallelStream()`) to process keys **in parallel**, ensuring **better performance** on multi-core processors.
3. The `computeIfPresent()` method updates values in a thread-safe manner.

### **Expected Output (Order May Vary Due to Concurrency)**
```
Initial Map: {Key1=1, Key2=2, Key3=3, Key4=4, Key5=5}
Thread-1 updated Key2
Thread-2 updated Key4
Thread-3 updated Key3
Thread-4 updated Key1
Thread-5 updated Key5
Updated Map: {Key1=2, Key2=4, Key3=6, Key4=8, Key5=10}
```

---

### **Example: Custom Concurrency Scenario with Multiple Threads**
```java
import java.util.concurrent.*;

public class CustomConcurrencyExample {
    public static void main(String[] args) {
        // Create a ConcurrentHashMap
        ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();

        // Executor Service with 3 threads
        ExecutorService executor = Executors.newFixedThreadPool(3);

        Runnable writerTask = () -> {
            for (int i = 1; i <= 5; i++) {
                map.put("Task" + i, i * 10);
                System.out.println(Thread.currentThread().getName() + " added Task" + i);
                try {
                    Thread.sleep(50); // Simulate work
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        };

        Runnable readerTask = () -> {
            map.forEach((key, value) -> 
                System.out.println(Thread.currentThread().getName() + " read " + key + " -> " + value));
        };

        // Execute tasks
        executor.execute(writerTask);
        executor.execute(readerTask);
        executor.execute(readerTask);

        // Shutdown executor
        executor.shutdown();
        try {
            executor.awaitTermination(1, TimeUnit.SECONDS);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Final Map: " + map);
    }
}
```

### **How This Works**
1. Creates a **thread pool with 3 threads** (`FixedThreadPool`).
2. One thread **writes** key-value pairs (`writerTask`).
3. Two threads **read** the map concurrently (`readerTask`).
4. **Thread safety is maintained** because `ConcurrentHashMap` supports multiple readers and writers.

### **Expected Output (Order May Vary)**
```
Thread-1 added Task1
Thread-1 added Task2
Thread-1 added Task3
Thread-2 read Task1 -> 10
Thread-3 read Task1 -> 10
Thread-2 read Task2 -> 20
Thread-3 read Task2 -> 20
Thread-1 added Task4
Thread-1 added Task5
Final Map: {Task1=10, Task2=20, Task3=30, Task4=40, Task5=50}
```

---

### **Key Takeaways**
- **Parallel streams** efficiently process map elements using multiple threads.
- **Fixed thread pool** allows controlled concurrent access to `ConcurrentHashMap`.
- **Thread safety is ensured** without external synchronization.
