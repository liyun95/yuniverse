# Concepts

`String`

:   A string is a collection of characters, mostly treated as a single unit. A string is used to store text values like a name, address, message, etc.

`Slice`

:   A slice is a subset of characters from a string. We use the syntax `[ i : f ]` to specify the initial and final index of the string to access a slice. There are several ways to access a slice of a string:

        - Use both values, as in [ i : f ], to access the slice from index i to index f-1.
        - Use only the intial value, as in [ i : ], to access the slice from index i to the end of the string.
        - Use only the final value, as in [ : f ], to access the slice from the start of the string to index f-1.

`Nested list`

:   A nested list is a list that contains other lists as its values or members. The container list is termed an outer list, and the member list is termed an inner list. Example: `alist = ['aa', ['b', 'c'], 'dd']`.