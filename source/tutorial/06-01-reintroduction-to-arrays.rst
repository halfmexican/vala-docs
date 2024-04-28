Re-introduction to Arrays
==========================

An array is a data structure that allows you to store multiple elements of the same type in a contiguous block of memory.
We used one previously in the :doc:`Parrot Program <04-02-cycle-through-names>` chapter.
 
Declaring and Initializing Arrays
---------------------------------

To declare an array in Vala, you specify the type of elements followed by square brackets ``[]``. Here's an example:

.. code-block:: vala

    int[] numbers = new int[5];

    
In this code snippet, we declare an array called ``numbers`` that can store integers. The ``new int[5]`` creates a new array with a length of 5, meaning it can hold up to 5 integer elements.

You can also initialize an array with specific values at the time of declaration:

.. code-block:: vala

    int[] numbers = { 1, 2, 3, 4, 5 };

Accessing Array Elements
------------------------

To access individual elements of an array, you use the index operator ``[]``. Array indices start from 0. Here's an example:

.. code-block:: vala

    int[] numbers = { 1, 2, 3, 4, 5 };
    int uno = numbers[0];  // Accesses the first element (1)
    int tres = numbers[2];  // Accesses the third element (3)

Array Slices
-------------

Vala allows you to create a slice of an array, which is a subset of the original array. You can create a slice by specifying the start and end indices:

.. code-block:: vala

    int[] numbers = { 1, 2, 3, 4, 5 };
    int[] slice = numbers[1:4]; // => { 2, 3, 4 }

In this example, `numbers[1:4]` creates a slice that starts from index 1 (inclusive) and ends at index 4 (exclusive)

Array Length
-------------

The length of an array can be obtained using the ``length`` member variable. For example:

.. code-block:: vala

    int[] a = new int[10];
    int count = a.length; // length is 10

.. note::
    if you write ``Object[] a = new Object[10]``, no objects will be created, just the array to store them in.


Resizing Arrays
----------------

You can resize an array by calling ``resize()`` on it. It will keep the original content (as much as fits). 

.. code-block:: vala

    int[] a = new int[5];
    a.resize(12);
   
.. tip::
   You can append array elements dynamically with the ``+=`` operator. However, this works only for locally defined or private arrays. The array is automatically reallocated if needed. Internally this reallocation happens with sizes growing in powers of 2 for run-time efficiency reasons. However, .length holds the actual number of elements, not the internal size

.. code-block:: 

   int[] e = {};
    e += 12;
    e += 5;
    e += 37;

Moving Elements
---------------

You can move elements within an array by calling move(src, dest, length) on it. The original positions will be filled with 0.

.. code-block:: vala

    uint8[] chars = "hello world".data;
    chars.move (6, 0, 5);
    print ((string) chars); // "world "

Fixed Size Arrays
------------------

.. code-block:: vala

    int f[10];  // no 'new ...

.. note::
   Vala does not do any bounds checking for array access at runtime. If you need more safety you should use a more sophisticated data structure like an ArrayList.

