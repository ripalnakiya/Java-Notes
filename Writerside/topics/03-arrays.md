# Arrays
<show-structure depth="2"/>

Array Declaration Syntax:

```Java
dataType arrayName[] = new dataType[size];
```

For example,

```Java
int marks[] = new marks[10];

int []marks = new int[10];

// Here, int[] becomes a data type
int[] marks = new int[10];

// So, we can create multiple arrays
int[] marks, values;
marks = new int[10];
values = new int[10];


int marks[] = {10, 20 ,30};

String fruits[] = {"Banana", "Mango", "Apple"};
```

## Array Length

```Java
System.out.println(marks.length);
```

## For each loop

We can also use **For each** loop to access the elements of the array

```Java
int A[] = {2, 4, 6, 8, 10};

for(int x : A) {
    System.out.println(x);
}
```

It will access each element of the array.

For each loop will only access the array elements, it will not modify the acutal array.

## 2D Array

```Java
int A[][] = new int[3][4];

int [][]A = new int[3][4];

int []A[] = new int[3][4];

// Here, int[] becomes a data type
int[] A[] = new int[3][4];

int[] B[], C[];
B = new int[3][4];
C = new int[3][4];

// Here, int[][] becomes a data type
int[][] A = new int[3][4];

int[][] B, C;
B = new int[3][4];
C = new int[3][4];

int A[][] = {{1,2,3,4}, {2,4,6,8}, {3,6,9,12}};

```

---

Consider this tricky array declaration:

```Java
int[] A, B[];

A = new int[10];
B = new int[3][4];
```

Here, `A` is 1D array and `B` is 2D array.

### Accessing Array Elements

```Java
for(int x[] : A) {
    for(int y : x) {
        System.out.print(y);
    }
    System.out.print("\n");
}
```
