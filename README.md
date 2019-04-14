# README

- [README](#readme)
  - [Java Virtual Machine Stacks](#java-virtual-machine-stacks)
  - [Heap](#heap)
  - [Generational Garbage Collection](#generational-garbage-collection)
  - [Big O Notation](#big-o-notation)
  - [Bit manipulation](#bit-manipulation)
    - [Binary Numbers](#binary-numbers)
      - [Binary Numbers and Base-2](#binary-numbers-and-base-2)
      - [Negative Numbers and Two's Complement](#negative-numbers-and-twos-complement)
    - [Bitwise AND](#bitwise-and)
    - [Bitwise OR](#bitwise-or)
    - [Bitwise XOR (exclusive OR)](#bitwise-xor-exclusive-or)
    - [Bitwise NOT](#bitwise-not)
  - [Memory Hierarchy](#memory-hierarchy)

## Java Virtual Machine Stacks

Each Java Virtual Machine thread has a private *Java Virtual Machine stack*, created at the same time as the thread. A Java Virtual Machine stack stores frames. A Java Virtual Machine stack is analogous to the stack of a conventional language such as C: it holds local variables and partial results, and plays a part in method invocation and return.

## Heap

The Java Virtual Machine has a *heap* that is shared among all Java Virtual Machine threads. The heap is the run-time data area from which memory for all class instances and arrays is allocated.

The heap is created on virtual machine start-up. Heap storage for objects is reclaimed by an automatic storage management system (known as a *garbage collector*); objects are never explicitly deallocated.

## Generational Garbage Collection

An object is considered garbage and its memory can be reused by the VM when it can no longer be reached from any reference of any other live object in the running program.

While naive garbage collection examines every live object in the heap every time, *generational collection* exploits several empirically observed properties of most applications to minimize the work required to reclaim unused (garbage) objects. The most important of these observed properties is the weak generational hypothesis, which states that most objects survive for only a short period of time.

To optimize for this scenario, memory is managed in *generations* (memory pools holding objects of different ages). Garbage collection occurs in each generation when the generation fills up.

The vast majority of objects are allocated in a pool dedicated to young objects (the *young generation*), and most objects die there. When the young generation fills up, it causes a *minor collection* in which only the young generation is collected; garbage in other generations isn't reclaimed. The costs of such collections are, to the first order, proportional to the number of live objects being collected; a young generation full of dead objects is collected very quickly. Typically, some fraction of the surviving objects from the young generation are moved to the *old generation* during each minor collection. Eventually, the old generation fills up and must be collected, resulting in a *major collection*, in which the entire heap is collected. Major collections usually last much longer than minor collections because a significantly larger number of objects are involved.

## Big O Notation

notation | name
:---: | :---:
O(1) | constant
O(log n) | logarithmic
O(n) | constant
O(n log n) | linearithmic/loglinear
O(n^2) | quadratic
O(n^c) | polynomial
O(c^n) | polynomial
O(n!) | factorial

- [Big-O Cheat Sheet](http://bigocheatsheet.com/)
- [orders of common functions](https://en.wikipedia.org/wiki/Big_O_notation#Orders_of_common_functions)
- [table of common time complexities](https://en.wikipedia.org/wiki/Time_complexity#Table_of_common_time_complexities)
- [NP-completeness](https://en.wikipedia.org/wiki/NP-completeness)

![](https://upload.wikimedia.org/wikipedia/commons/a/a0/P_np_np-complete_np-hard.svg)

## Bit manipulation

### Binary Numbers

#### Binary Numbers and Base-2

decimal | binary
:---: | :---:
0 | 0000
1 | 0001
2 | 0010
3 | 0011
4 | 0100
5 | 0101
6 | 0110
7 | 0111
8 | 1000
9 | 1001
10 | 1010

#### Negative Numbers and Two's Complement

decimal | binary | interpretation
:---: | :---: | :---:
−5 | 1011 | -8 + 2 + 1
−4 | 1100 | -8 + 4
−3 | 1101 | -8 + 4 + 1
−2 | 1110 | -8 + 4 + 2
−1 | 1111 | -8 + 4 + 2 + 1
0 | 0000 | 0
1 | 0001 | 1
2 | 0010 | 2
3 | 0011 | 2 + 1
4 | 0100 | 4
5 | 0101 | 4 + 1

### Bitwise AND

The ```AND``` operation takes two bits and returns 1 if *both* bits are 1. Otherwise, it returns 0.

```
(1 & 1) == 1
(1 & 0) == 0
(0 & 1) == 0
(0 & 0) == 0
```

When performing ```AND``` on two integers, the ```AND``` operation is calculated on each pair of bits (the two bits at the same index in each number).

```
(5 & 6) == 4

// at the bit level:
//   0101 (5)
// & 0110 (6)
// = 0100 (4)
```

### Bitwise OR

The ```OR``` operation takes two bits and returns 1 if *either* of the bits are 1. Otherwise, it returns 0.

```
(1 | 1) == 1
(1 | 0) == 1
(0 | 1) == 1
(0 | 0) == 0
```

When performing ```OR``` on two integers, the ```OR``` operation is calculated on each pair of bits (the two bits at the same index in each number).

```
(5 | 6) == 7

// at the bit level:
//   0101 (5)
// | 0110 (6)
// = 0111 (7)
```

### Bitwise XOR (exclusive OR)

The ```XOR``` operation (or ```exclusive or```) takes two bits and returns 1 if *exactly one* of the bits is 1. Otherwise, it returns 0.

```
(1 ^ 1) == 0
(1 ^ 0) == 1
(0 ^ 1) == 1
(0 ^ 0) == 0
```

When performing ```XOR``` on two integers, the ```XOR``` operation is calculated on each pair of bits (the two bits at the same index in each number).

```
(5 ^ 6) == 3

// at the bit level:
//   0101 (5)
// | 0110 (6)
// = 0011 (3)
```

### Bitwise NOT

The ```NOT``` bitwise operation takes one set of bits, and for each bit returns 0 if the bit is 1, and 1 if the bit is 0.

When performing ```NOT``` on an integer, each bit of the integer is inverted.

```
~ 5 == -6

// at the bit level:
// ~ 0101 (5)
// = 1010 (-6 in two's complement as interpreted by the compiler)
```

## Memory Hierarchy

![](https://upload.wikimedia.org/wikipedia/commons/0/0c/ComputerMemoryHierarchy.svg)

[//]: # (TODO)
[//]: # (https://medium.com/@sinisalouc/variance-in-java-and-scala-63af925d21dc)
[//]: # (http://www.cs.umd.edu/~pugh/java/memoryModel/DoubleCheckedLocking.html)
[//]: # (https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

