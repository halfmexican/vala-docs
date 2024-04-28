Multidimensional Arrays
=========================

Multi-dimensional arrays are defined with `[,]` or `[,,]` etc.

.. code-block:: vala

    int[,] c = new int[3,4];
    int[,] d = {{2, 4, 6, 8},
                {3, 5, 7, 9},
                {1, 3, 5, 7}};
    d[2,3] = 42;

This sort of array is represented by a single contiguous memory block. 

To find the length of each dimension in a multi-dimensional array, the `length` member becomes an array, storing the length of each respective dimension.

.. code-block:: vala

    int[,] arr = new int[4,5];
    int r = arr.length[0];
    int c = arr.length[1];
    
.. note::
   Jagged multi-dimensional arrays (`[][]`, also known as "stacked arrays" or "arrays of arrays"), where each row may have a different length, are not yet supported.

.. warning::
   you can't get a mono-dimensional array from a multidimensional array, or even slice a multidimensional array!
