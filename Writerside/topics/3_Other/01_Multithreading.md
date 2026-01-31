# Multithreading

Running multiple programs on a single machine or a computer is known as **multi-programming**.

Forms of Multiprogramming:

1. Multi User : Multiple users are using the same computer for running different programs.

2. Multi Tasking : Single user, but runs multiple tasks simultaneously in one computer.

Multithreading is part of Multi-tasking.

Java provides `Thread` class and `runnable` interface to achieve multithreading.

`Thread` class contains the actual mechanism for multithreading.

## Thread Class

```Java
class MyThread extends Thread{
    @Override
    public void run(){
        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". Hello");
        }
    }
}

public class Main{
    public static void main(String[] args){
        Thread thd = new Thread();
        thd.start();

        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

```Java
public class Main extends Thread{
    @Override
    public void run(){
        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". Hello");
        }
    }

    public static void main(String[] args){
        Main dr = new Main();
        dr.start();

        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

---

## Runnable Interface

```Java
class MyRunnable implements Runnable{
    @Override
    public void run(){
        int i = 0;
        while (true)
        {
            i++;
            System.out.println(i + ". Hello");
        }
    }
}

public class Main{
    public static void main(String[] args){
        MyRunnable rnb = new MyRunnable();
        Thread thd = new Thread(rnb);
        thd.start();

        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

```Java
public class Main implements Runnable{
    @Override
    public void run(){
        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". Hello");
        }
    }

    public static void main(String[] args){
        Main dr = new Main();
        Thread thd = new Thread(dr);
        thd.start();

        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

## States of Thread

new -> ready -> running -> terminated

During Running state, it can go into one of the following states:

1. wait : Waiting to acquire some resource or Made to wait by some other thread.

2. timed wait : To make the thread to delay for some time using the sleep method, it is also known as sleep state.

3. blocked : It is similar to waiting state.

The First state of the thread is `new`, it stores the object of the thread.

When `start()` method is called then thread enters into the ready state, where it is ready to run.

## Thread Priorities

JAVA supports thread priorities from 1-10.

The priority of default thread is always 5.

The higher priority is given to the thread which gets the input or the data.

The thread with higher priority gets the more CPU time.

Multithreading features are provided by the operating systems but in java, JVM have its own scheduler.

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
void join();    // If a thread has finished its job, then instead of terminating, it can wait for other threads to finish
                // e.g. main() can wait until all the threads have finished
void join(long millseconds);
void run();
void start();

// Static Methods
int activeCount();
Thread currentThread();     // returns reference to current running thread
void yield();               // It can stop higher priority thread from starvating lower priority threads (Continue after the lower priority thread is finished)
void dumpstack();           // to know the contents in the stack or to know the depth of the stack.
```

```Java
class MyThread extends Thread {
    public MyThread(String name) {
        // calling super class constructor i.e. Thread(String name)
        super(name);

        // Priority can be set in the main() also, using the Thread object
        setPriority(MIN_PRIORITY);

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
        // t.setPriority(MIN_PRIORITY);
        System.out.println("Thread Priority: " + t.getPriority());
        System.out.println("Thread State: " + t.getState());
        t.start();
        System.out.println("Now, Thread State: " + t.getState());
        t.interrupt();
    }
}
```

Output:

```SH
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

The classes Mythread1 and Mythread2 access the data from the display class which is the shared object.

---

Example using ATM Machine:

```Java
public class ATM {
    synchronized public void checkBalance(String name) {
        System.out.print(name);
        try {Thread.sleep(1000);} catch (Exception e) {}
        System.out.println(" is checking balance");
    }

    synchronized public void withdraw(String name, int amount) {
        System.out.print(name);
        try {Thread.sleep(1000);} catch (Exception e) {}
        System.out.println(" is withdrawing " + amount);
    }
}

public class Customer extends Thread {
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

## Inter Process Communication

It is a communication between the synchronized threads.

It is the communication between a single producer thread and a consumer thread.

The inter thread communication refers to the synchronization between the producer thread and the consumer thread to access the write and read method simultaneously.

To achieve the communication the flag = true and flag = false are used.

### Race Condition

When there is a single producer thread and multiple consumer threads.

All consumers do not execute at once, they do in a round robin fashion.

- When the count is zero then it is the producers turn.

- When the count is not zero then it is the consumers turn.

Since there are more than one consumers, any one of the consumer can access it.

The `notify()` method can open any thread as they may not be in an order.

    Assume one thread is accessing the shared resource and all other threads are blocked,
    when that thread has finished working it will inform other threads
    and any of the threads may access the object just like in a race.

So, in the above the count method is used to control the race.

The race condition can be avoided by the inter-thread condition.

> Notify() : This methods informs the blocked threads that they can now access the shared resource
