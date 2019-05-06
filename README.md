# README

- [README](#readme)
  - [Data Units](#data-units)
  - [Algorithmic Thinking](#algorithmic-thinking)
    - [Big O Notation](#big-o-notation)
    - [NP-completeness](#np-completeness)
    - [Logarithms](#logarithms)
  - [Bit Manipulation](#bit-manipulation)
    - [Binary Numbers](#binary-numbers)
      - [Binary Numbers and Base-2](#binary-numbers-and-base-2)
      - [Negative Numbers and Two's Complement](#negative-numbers-and-twos-complement)
    - [Bitwise AND](#bitwise-and)
    - [Bitwise OR](#bitwise-or)
    - [Bitwise XOR (exclusive OR)](#bitwise-xor-exclusive-or)
    - [Bitwise NOT](#bitwise-not)
    - [Bit Shifting](#bit-shifting)
      - [Left Shifts](#left-shifts)
      - [Logical Right Shifts](#logical-right-shifts)
      - [Arithmetic Right Shifts](#arithmetic-right-shifts)
  - [Java](#java)
    - [Java Primitive Data Types](#java-primitive-data-types)
    - [Java Collection Performance](#java-collection-performance)
      - [Sets](#sets)
      - [Queues](#queues)
      - [Lists](#lists)
      - [Maps](#maps)
    - [Java Variance](#java-variance)
    - [Java Virtual Machine Stacks](#java-virtual-machine-stacks)
    - [Heap](#heap)
    - [Generational Garbage Collection](#generational-garbage-collection)
  - [Networking](#networking)
    - [Open Systems Interconnection (OSI) Reference Model](#open-systems-interconnection-osi-reference-model)
  - [Memory Hierarchy](#memory-hierarchy)
  - [ACID](#acid)
  - [REST](#rest)

## Data Units

name | symbol | size | bit rate
:---: | :---: | :---: | :---:
bit | ```b``` | 0 or 1 | ```bit/s```
byte | ```B``` | 8 bits | ```B/s```
kilobyte | ```KB``` | 1024 bytes | ```kb/s```
megabyte | ```MB``` | 1024 kilobytes | ```Mb/s```
gigabyte | ```GB``` | 1024 megabytes | ```Gb/s```
terabyte | ```TB``` | 1024 gigabytes | ```Tb/s```
petabyte | ```PB``` | 1024 terabytes
exabyte | ```EB``` | 1024 terabytes

See also:
- [Data Measurement Chart](http://www.wu.ece.ufl.edu/links/dataRate/DataMeasurementChart.html)
- [Data-rate units](https://en.wikipedia.org/wiki/Data-rate_units)
- [Some selected powers of two](https://en.wikipedia.org/wiki/Power_of_two#Some_selected_powers_of_two)

## Algorithmic Thinking

### Big O Notation

notation | name | complexity class
:---: | :---: | :---:
$O(1)$ | constant time
$O(log n)$ | logarithmic time
$O(n)$ | constant time
$O(n log n)$ | log-linear time
$O(n^2)$ | quadratic time
$O(n^c)$ | polynomial time | **P**
$O(c^n)$ | exponential time (with linear exponent) | **E**
$O(c^{poly(n)})$ | exponential time | **EXPTIME**
$O(n!)$ | factorial

- all pairs: $n^2$
- all triples: $n^3$
- all subsets of set $n$: $2^n$
- all $k$ combinations of set $n$ ($n$ choose $k$): ${n \choose k} = n!/(k!(n-k)!)$
- all permutations: $n!$

See also:
- [Big-O Cheat Sheet](http://bigocheatsheet.com/)
- [Orders of common functions](https://en.wikipedia.org/wiki/Big_O_notation#Orders_of_common_functions)
- [Table of common time complexities](https://en.wikipedia.org/wiki/Time_complexity#Table_of_common_time_complexities)

### NP-completeness

- The class **P** consists of problems that are solvable in polynomial time.
- The class **NP** consists of problems that are *verifiable* in polynomial time.
- Any problem in **P** is also in **NP**. And any problem in **NP** is also in **EXPTIME**. More formally:
  - $P \subseteq NP \subseteq PSPACE \subseteq EXPTIME \subseteq NEXPTIME \subseteq EXPSPACE$
  - $P \subsetneq EXPTIME$
  - $NP \subsetneq NEXPTIME$
- A problem is in class **NPC** (and is referred to as being **NP-complete**) if it is in **NP** and is as *hard* as any problem in **NP**.
- If any **NP-complete** problem can be solved in polynomial time, then every problem in **NP** can be solved in polynomial time.

See also:
- [EXPTIME](https://en.wikipedia.org/wiki/EXPTIME)

![](https://upload.wikimedia.org/wikipedia/commons/a/a0/P_np_np-complete_np-hard.svg)

### Logarithms

The logarithm for a base *b* and a number *x* is defined to be the inverse function of taking *b* to the power *x*. For any *x* and *b*:

$$
log_b(x) = y \iff b^y = x
$$

For example:

$$
log_2 64 = 6 \iff 2^6 = 64
$$

## Bit Manipulation

### Binary Numbers

#### Binary Numbers and Base-2

decimal | binary | interpretation | powers
:---: | :---: | :---: | :---:
0 | 0000 | 0 + 0 + 0 + 0
1 | 0001 | 0 + 0 + 0 + 1 | $2^0$
2 | 0010 | 0 + 0 + 2 + 0 | $2^1$
3 | 0011 | 0 + 0 + 2 + 1 | $2^1 + 2^0$
4 | 0100 | 0 + 4 + 0 + 0 | $2^2$
5 | 0101 | 0 + 4 + 0 + 1 | $2^2 + 2^0$
6 | 0110 | 0 + 4 + 2 + 0 | $2^2 + 2^1$
7 | 0111 | 0 + 4 + 2 + 1 | $2^2 + 2^1 + 2^0$
8 | 1000 | 8 + 0 + 0 + 0 | $2^3$
9 | 1001 | 8 + 0 + 0 + 1 | $2^3 + 2^0$
10 | 1010 | 8 + 0 + 2 + 0 | $2^3 + 2^1$

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

The ```AND``` operation takes two bits and returns ```1``` if *both* bits are ```1```. Otherwise, it returns ```0```.

```
(1 & 1) == 1
(1 & 0) == 0
(0 & 1) == 0
(0 & 0) == 0
```

When performing ```AND``` on two integers, the ```AND``` operation is calculated on each pair of bits (the two bits at the same index in each number).

```
(5 & 6) == 4

// at bit level:
//   0101 (5)
// & 0110 (6)
// = 0100 (4)
```

### Bitwise OR

The ```OR``` operation takes two bits and returns ```1``` if *either* of the bits are 1. Otherwise, it returns ```0```.

```
(1 | 1) == 1
(1 | 0) == 1
(0 | 1) == 1
(0 | 0) == 0
```

When performing ```OR``` on two integers, the ```OR``` operation is calculated on each pair of bits (the two bits at the same index in each number).

```
(5 | 6) == 7

// at bit level:
//   0101 (5)
// | 0110 (6)
// = 0111 (7)
```

### Bitwise XOR (exclusive OR)

The ```XOR``` operation (or ```exclusive or```) takes two bits and returns ```1``` if *exactly one* of the bits is ```1```. Otherwise, it returns ```0```.

```
(1 ^ 1) == 0
(1 ^ 0) == 1
(0 ^ 1) == 1
(0 ^ 0) == 0
```

When performing ```XOR``` on two integers, the ```XOR``` operation is calculated on each pair of bits (the two bits at the same index in each number).

```
(5 ^ 6) == 3

// at bit level:
//   0101 (5)
// | 0110 (6)
// = 0011 (3)
```

### Bitwise NOT

The ```NOT``` bitwise operation takes one set of bits, and for each bit returns ```0``` if the bit is ```1```, and ```1``` if the bit is ```0```.

When performing ```NOT``` on an integer, each bit of the integer is inverted.

```
~ 5 == -6

// at bit level:
// ~ 0101 (5)
// = 1010 (-6 in two's complement as interpreted by the compiler)
```

### Bit Shifting

#### Left Shifts

When shifting left, the most-significant bit is lost, and a ```0``` bit is inserted on the other end.

```
0010 << 1 -> 0100
0010 << 2 -> 1000
```

A single left shift multiplies a binary number by ```2```.

```
2 << 1 == 4

// at bit level:
// 0010 << 1 = 0100
```

#### Logical Right Shifts

When shifting right with a **logical right shift**, the least-significant bit is lost and a ```0``` is inserted on the other end.

```
1011 >>> 1 -> 0101
1011 >>> 3 -> 0001
```

For positive numbers, a single logical right shift divides a number by ```2```, throwing out any remainders.

```
5 >>> 1 == 2

// at bit level:
// 0101 >>> 1 = 0010
```

#### Arithmetic Right Shifts

When shifting right with an **arithmetic right shift**, the least-significant bit is lost and the most-significant bit is *copied*.

```
1011 >> 1 -> 1101
1011 >> 3 -> 1111

0011 >> 1 -> 0001
0011 >> 2 -> 0000
```

The first two numbers had a ```1``` as the most significant bit, so more ```1```'s were inserted during the shift. The last two numbers had a ```0``` as the most significant bit, so the shift inserted more ```0```'s.

If a number is encoded using [two's complement](#negative-numbers-and-twos-complement), then an arithmetic right shift preserves the number's sign, while a logical right shift makes the number positive.

```
-5 >> 1 == -3

// at bit level:
// 1011 >> 1 = 1101

-1 >>> 1 == 7

// at bit level:
// 1111 >>> 1 = 0111
```

## Java

### Java Primitive Data Types

category | type | size | signed range | signed exp
:---: | :---: | :---: | :---: | :---:
integral | byte | 8-bit | -128 to 127 | $−(2^7)$ to $2^7 − 1$
integral | short | 16-bit | -32,768 to 32,767 | $−(2^{15})$ to $2^{15} − 1$
integral | int | 32-bit | -2,147,483,648 to 2,147,483,647 | $−(2^{31})$ to $2^{31} − 1$
integral | long | 64-bit | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | $−(2^{63})$ to $2^{63} − 1$
integral | char | 16-bit | ```'\u0000'``` to ```'\uffff'```
floating-point | float | 32-bit | 32-bit IEEE 754 floating-point numbers
floating-point | double | 64-bit | 64-bit IEEE 754 floating-point numbers
other | boolean | N/A  | ```true``` and ```false```

See also:
- [Common integral data types](https://en.wikipedia.org/wiki/Integer_(computer_science)#Common_integral_data_types)
- [Orders of magnitude (data)](https://en.wikipedia.org/wiki/Orders_of_magnitude_(data))

### Java Collection Performance

#### [Sets](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html)

collection | add | contains | remove
:---: | :---: | :---: | :---:
HashSet | O(1) | O(1) | O(1)
LinkedHashSet | O(1) | O(1) | O(1)
TreeSet | O(log n) | O(log n) | O(log n)

#### [Queues](https://docs.oracle.com/javase/8/docs/api/java/util/Queue.html)

collection | add/offer | peek | contains | poll/remove
:---: | :---: | :---: | :---: | :---:
LinkedList | O(1) | O(1) | O(n) | O(1)
PriorityQueue | O(log n) | O(1) | O(n) | O(log n)

#### [Lists](https://docs.oracle.com/javase/8/docs/api/java/util/List.html)

collection | add | get | set | contains | remove
:---: | :---: | :---: | :---: | :---: | :---:
ArrayList | O(1) | O(1) | O(1) | O(n) | O(n)
LinkedList | O(1) | O(n) | O(n) | O(n) | O(1)

#### [Maps](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html)

collection | put | get | containsKey | remove
:---: | :---: | :---: | :---: | :---:
HashMap | O(1) | O(1) | O(1)
LinkedHashMap | O(1) | O(1) | O(1) | O(1)
TreeMap | O(log n) | O(log n) | O(log n) | O(log n)

See also:
- [Big-O Cheat Sheet](http://bigocheatsheet.com/)

### Java Variance

Given a generic class ```C<X>```:
- ```C<X>``` is said to be **covariant** with respect to ```X``` if ```S <: T``` implies ```C<S> <: C<T>``` (where ```<:``` denotes the subtyping relation)
- ```C<X>``` is said to be **contravariant** with respect to ```X``` if ```S <: T``` implies ```C<T> <: C<S>```
- ```C<X>``` is said to be **invariant** when ```C<S> <: C<T>``` is derived only if ```S = T```

A generic collection whose element type is abstracted as a type parameter is typically:
- read-only when **covariant**
    - reading is allowed because the upper bound restricts the element type to a specific type or a subtype of that type
    - writing is not allowed because the element type accepted by the collection is unknown
- write-only when **contravariant**
    - writing is allowed because the lower bound restricts the element type to a specific type or a supertype of that type
    - reading is not allowed because the element type returned by the collection is unknown

See also:
- [On Variance-Based Subtyping for Parametric Types](http://www.fos.kuis.kyoto-u.ac.jp/~igarashi/papers/variance.html)
- Using the OpenJDK to Investigate Covariance in Java
- [Variance in Java and Scala](https://medium.com/@sinisalouc/variance-in-java-and-scala-63af925d21dc)

### Java Virtual Machine Stacks

Each Java Virtual Machine thread has a private *Java Virtual Machine stack*, created at the same time as the thread. A Java Virtual Machine stack stores frames. A Java Virtual Machine stack is analogous to the stack of a conventional language such as C: it holds local variables and partial results, and plays a part in method invocation and return.

### Heap

The Java Virtual Machine has a *heap* that is shared among all Java Virtual Machine threads. The heap is the run-time data area from which memory for all class instances and arrays is allocated.

The heap is created on virtual machine start-up. Heap storage for objects is reclaimed by an automatic storage management system (known as a *garbage collector*); objects are never explicitly deallocated.

### Generational Garbage Collection

An object is considered garbage and its memory can be reused by the VM when it can no longer be reached from any reference of any other live object in the running program.

While naive garbage collection examines every live object in the heap every time, *generational collection* exploits several empirically observed properties of most applications to minimize the work required to reclaim unused (garbage) objects. The most important of these observed properties is the weak generational hypothesis, which states that most objects survive for only a short period of time.

To optimize for this scenario, memory is managed in *generations* (memory pools holding objects of different ages). Garbage collection occurs in each generation when the generation fills up.

The vast majority of objects are allocated in a pool dedicated to young objects (the *young generation*), and most objects die there. When the young generation fills up, it causes a *minor collection* in which only the young generation is collected; garbage in other generations isn't reclaimed. The costs of such collections are, to the first order, proportional to the number of live objects being collected; a young generation full of dead objects is collected very quickly. Typically, some fraction of the surviving objects from the young generation are moved to the *old generation* during each minor collection. Eventually, the old generation fills up and must be collected, resulting in a *major collection*, in which the entire heap is collected. Major collections usually last much longer than minor collections because a significantly larger number of objects are involved.

See also:
- [Go GC: Prioritizing low latency and simplicity](https://blog.golang.org/go15gc)

## Networking

### Open Systems Interconnection (OSI) Reference Model

layer \# | layer name | data unit | protocol examples | Internet layer
:---: | :---: | :---: | :---: | :---:
7 | application | data | FTP, HTTP | application
6 | presentation | data | ASCII, MPEG | application
5 | session | data | named pipes, sockets | application
4 | transport | TCP segment, datagram | TCP, UDP| transport
3 | network | packet | IP (IPv4, IPv6) | Internet
2 | data link | frame | IEEE 802.3 (Ethernet) | link
1 | physical | one or more bits

- A **network (layer 4) load balancer** functions at the fourth layer of the OSI reference model.
- An **application (layer 7) load balancer** functions at the seventh layer of the OSI reference model.

See also:
- [RFC 1122 - Requirements for Internet Hosts - Communication Layers](https://tools.ietf.org/html/rfc1122#section-2.2)
- [Using AWS Application Load Balancer and Network Load Balancer with EC2 Container Service](https://medium.com/containers-on-aws/using-aws-application-load-balancer-and-network-load-balancer-with-ec2-container-service-d0cb0b1d5ae5)

## Memory Hierarchy

![](https://upload.wikimedia.org/wikipedia/commons/0/0c/ComputerMemoryHierarchy.svg)

## ACID

ACID is an acronym for:
- **atomicity**: a transaction is an indivisible unit that is either performed in its entirety or is not performed at all
- **consistency**: a transaction must transform the database from one consistent state to another consistent state
- **isolation**: transactions execute independently of one another
- **durability**: the effects of a successfully completed (committed) transaction
are permanently recorded in the database and must not be lost because of a
subsequent failure

## REST

A basic HTTP request consists of:
- a verb (or method)
- a resource (or endpoint)

Each HTTP verb:
- has a meaning
- is idempotent or not: *a request method is considered "idempotent" if the intended effect on the server of multiple identical requests with that method is the same as the effect for a single such request* (see [RFC7231: Idempotent methods](https://tools.ietf.org/html/rfc7231#section-4.2.2)).
- is safe or not: *request methods are considered "safe" if their defined semantics are essentially read-only* (see [RFC7231: Safe methods](https://tools.ietf.org/html/rfc7231#section-4.2.1)).
- is cacheable or not

verb | meaning | idempotent | safe | cacheable
:---: | :---: | :---: | :---: | :---:
GET | reads a resource | yes | yes | yes
POST | creates a resource or triggers a data-handling process | no | no | only cacheable if response contains explicit freshness information
PUT | fully updates (replaces) an existing resource or creates a resource | yes | no | no
PATCH | partially updates a resource | no | no | only cacheable if response contains explicit freshness information
DELETE | deletes a resource | yes | no | no

[//]: # (TODO)

[//]: # (https://everythingisdata.wordpress.com/2009/10/17/numbers-everyone-should-know/)

[//]: # (https://en.wikipedia.org/wiki/External_sorting#External_merge_sort)

[//]: # (http://www.cs.umd.edu/~pugh/java/memoryModel/DoubleCheckedLocking.html)

[//]: # (https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)
[//]: # (https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)

[//]: # (http://static.googleusercontent.com/media/research.google.com/zh-CN/us/archive/mapreduce-osdi04.pdf)

[//]: # (https://github.com/donnemartin/system-design-primer#remote-procedure-call-rpc)
[//]: # (https://github.com/donnemartin/system-design-primer#consistency-patterns)
[//]: # (https://github.com/donnemartin/system-design-primer#availability-patterns)
[//]: # (https://github.com/donnemartin/system-design-primer#reverse-proxy-web-server)
[//]: # (https://gist.github.com/jboner/2841832)
[//]: # (https://gist.github.com/hellerbarde/2843375)

