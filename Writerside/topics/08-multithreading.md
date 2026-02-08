# Multithreading
<show-structure depth="2"/>

Running multiple programs on a single computer is known as **multiprogramming**.

- Forms of Multiprogramming:
  1. **Multi User:** Multiple users are using the same computer for running different programs.
  2. **Multi Tasking:** Single user, but runs multiple tasks simultaneously in one computer.

Multithreading is part of Multi-tasking.

Java provides `Thread` class and `Runnable` interface to achieve multithreading.

`Thread` class contains the actual mechanism for multithreading.

## Thread Class

Extending the `Thread` class:

```Java
class MyThread extends Thread {
    @Override
    public void run() {
        int i = 0;
        while (true) {
            i++;
            System.out.println(i + ". Hello");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread thd = new MyThread();
        thd.start();

        int i = 0;
        while (true) {
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

Making `Main` class extend the `Thread` class:

```Java
public class Main extends Thread {
    @Override
    public void run() {
        int i = 0;
        while (true) {
            i++;
            System.out.println(i + ". Hello");
        }
    }

    public static void main(String[] args) {
        Main m = new Main();
        m.start();

        int i = 0;
        while (true) {
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

## Runnable Interface

Implementing the `Runnable` interface:

```Java
class MyRunnable implements Runnable {
    @Override
    public void run() {
        int i = 0;
        while (true) {
            i++;
            System.out.println(i + ". Hello");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        MyRunnable r = new MyRunnable();
        Thread t = new Thread(r);
        t.start();

        int i = 0;
        while (true) {
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

Making `Main` class implement the `Runnable` interface:

```Java
public class Main implements Runnable {
    @Override
    public void run() {
        int i = 0;
        while (true) {
            i++;
            System.out.println(i + ". Hello");
        }
    }

    public static void main(String[] args) {
        Main m = new Main();
        Thread t = new Thread(m);
        t.start();

        int i = 0;
        while (true) {
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

## States of Thread

    new -> ready -> running -> terminated

The First state of the thread is **new**, it stores the object of the thread.

When `start()` method is called then thread enters into the **ready** state, 
where it is ready to run.

- During **Running** state, it can go into one of the following states:
  1. **wait**: Waiting to acquire some resource or Made to wait by some other thread.
  2. **timed wait**: Make the thread to delay for some time using the sleep method, 
                     it is also known as **sleep state**.
  3. **blocked**: It is similar to waiting state.

## Thread Priorities

JAVA supports thread priorities from `1`-`10`.

The priority of default thread is always `5`.

The thread with **higher priority** gets the **more CPU time**.

Higher priority is given to threads which **gets the input or the data**.

Multithreading features are provided by the operating systems...
but in java, **JVM have its own scheduler**.

## Methods of Thread Class

```Java
// Constructors
Thread()
Thread(Runnable r)
Thread(String name) // Gives name to the thread
Thread(Runnable r, String name)
Thread(ThreadGroup g, String name)

// Getter and Setter methods
long getId();
String getName();
int getPriority();
ThreadState getState();
THreadGroup getThreadGroup(); // to	know the group to which the thread belongs

void setName(String name);
void setPriority(int p);
void setDaemon(Boolean d);  // Daemon thread is a background thread with least priority and no user interaction
                            // e.g. Garbage Collector in Java

// Enquiry
boolean isAlive();
boolean isDaemon();
boolean isInterrupted();

// Instance methods
void interrupt();   // It will stop doing the currently doing work, e.g. stop waiting/sleeping
void join();        // If a thread has finished its job, then instead of terminating, it can wait for other threads to finish
                    // e.g. main() can wait until all the threads have finished
void join(long millseconds);
void run();
void start();

// Static Methods
int activeCount();
Thread currentThread(); // returns reference to current running thread
void yield();           // It can stop higher priority thread from starvating lower priority threads (And continue after the lower priority thread is finished)
void dumpstack();       // To know the contents in the stack or to know the depth of the stack.
```

## Example

```Java
class MyThread extends Thread {
    public MyThread(String name) {
        // calling super class constructor i.e. Thread(String name)
        super(name);

        // Priority can be set in the main() also, using the Thread object
        setPriority(Thread.MIN_PRIORITY);
    }

    public void run() {
        int counter = 1;
        while (true) {
            System.out.println(counter);
            counter++;
            try {
                Thread.sleep(1000);
            } catch (Exception e) {
                System.out.println(e);
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t = new MyThread("Thread 1");
        System.out.println("Thread Id: " + t.getId());
        System.out.println("Thread name: " + t.getName());
        System.out.println("Thread Priority: " + t.getPriority());
        System.out.println("Thread State: " + t.getState());
        t.start();
        System.out.println("Now, Thread State: " + t.getState());
        t.interrupt();
    }
}
```

Output:

```shell
Thread Id: 15
Thread name: Thread 1
Thread Priority: 1
Thread State: NEW
Now, Thread State: RUNNABLE
1
java.lang.InterruptedException: sleep interrupted
2
3
4
5
6
```

## Synchronization

```Java
class MyData {
    // We can synchronize a block or a complete function
    public void display(String str) {
        synchronized (this) {
            for (int i = 0; i < str.length(); i++) {
                System.out.print(str.charAt(i));
            }
        }
    }

    // synchronized public void display(String str) {
    //      for (int i = 0; i < str.length(); i++) {
    //          System.out.print(str.charAt(i));
    //      }
    // }
}

class MyThread1 extends Thread {
    MyData d = new MyData();

    public MyThread1(MyData d) {
        this.d = d;
    }

    public void run() {
        d.display("Hello World");
    }
}

class MyThread2 extends Thread {
    MyData d = new MyData();

    public MyThread2(MyData d) {
        this.d = d;
    }

    public void run() {
        d.display("Welcome");
    }
}

public class Main {
    public static void main(String[] args) {
        MyData data = new MyData();

        MyThread1 thd1 = new MyThread1(data);
        MyThread2 thd2 = new MyThread2(data);

        thd2.start();
        thd1.start();
    }
}
```

The classes `MyThread1` and `MyThread2` access the data from the display class 
which is the shared object.

### Example using ATM Machine

```Java
class ATM {
    synchronized public void checkBalance(String name) {
        System.out.print(name);
        try {
            Thread.sleep(1000);
        } catch (Exception e) {
        }
        System.out.println(" is checking balance");
    }

    synchronized public void withdraw(String name, int amount) {
        System.out.print(name);
        try {
            Thread.sleep(1000);
        } catch (Exception e) {
        }
        System.out.println(" is withdrawing " + amount);
    }
}

class Customer extends Thread {
    private String name;
    private int amount;
    private ATM atm;

    public Customer(String name, int amount, ATM atm) {
        this.name = name;
        this.amount = amount;
        this.atm = atm;
    }

    public void useATM() {
        atm.checkBalance(name);
        atm.withdraw(name, amount);
    }

    public void run() {
        useATM();
    }
}

public class Main {
    public static void main(String[] args) {
        ATM atm = new ATM();

        Customer c1 = new Customer("Jack", 2000, atm);
        Customer c2 = new Customer("John", 2000, atm);

        c1.start();
        c2.start();
    }
}
```

ATM Object is a shared resource, so we need to synchronize it.

## Inter Thread Communication

**Inter-Process Communication (IPC)** → between processes

**Inter-Thread Communication** → between threads inside the same process

Inter-thread communication is a way for threads to coordinate their work 
so they don’t step on each other’s toes.

- Typical scenario:
  - One thread produces data (producer)
  - Another thread consumes data (consumer)
  - They share the same object

<br>

- The problem:
  - Consumer should wait if there’s nothing to consume
  - Producer should wait if the buffer is full

<br>

- Threads communicate using the methods:
  - `wait()`
  - `notify()`
  - `notifyAll()`

These methods must be called inside synchronized blocks or methods.

When a thread cannot proceed because a required condition is not met, 
it calls `wait()` and releases the lock. 

When another thread changes the condition, 
it calls `notify()` or `notifyAll()` to wake waiting threads.

### Race Condition

- A race condition happens when:
  - Multiple threads access shared data
  - The result depends on who runs first
  - The outcome becomes unpredictable

- To avoid race conditions:
  - Shared data must be accessed in synchronized code
  - Conditions must be checked using a `while` loop
  - `notifyAll()` is preferred when multiple threads are waiting

### notify vs notifyAll

- `notify()`
  - Wakes one arbitrary waiting thread
  - Risky when multiple consumers exist

- `notifyAll()`
  - Wakes all waiting threads
  - Each re-checks the condition
  - Safer for complex cases

That’s why conditions must always be checked in a `while` loop, not `if`.
