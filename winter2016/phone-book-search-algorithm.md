

#### String Management - processing strings and extracting information

We'll be writing an algorithm tonight that describes the 'phone book' search method, a way of quickly searching a list of items for a specific item.

This is an 'algorithm' which is a long word for 'way of doing things'.

Other things that are algorithms: tying your shoes, addition, making an omelet.



1. ##### Today's deep dive: functions and scope

    ```python
    """ Lets learn a bit about functions and 'scope'
    """
    
    # you can use lowercase, but globals as all caps can help differentiate.
    THIS_IS_A_GLOBAL_VARIABLE = "is this available in the function?"

    def add_a_number(source_number, number_to_add):
        """ This function allows us to add whatever we pass it
        """
        result = source_number + number_to_add
        
        print "Viewing: {}".format(THIS_IS_A_GLOBAL_VARIABLE)

        return result

    first_number = 100
    second_number = 10
    returned_from_the_function = add_a_number(first_number, second_number)
    print "Result of {} + {}: {}".format(first_number, second_number, returned_from_the_function)
        
        
    ```



2. ##### String Encoding! ascii or utf-8?
    1. First off, what are they?
        1. ascii - this is a 1:1 encoding of bytes to characters, it can only represent the english letters and some additional stuff.
        2. unicode - this is a huge set of characters representing many languages. Not all fonts support all sections of unicode. Unicode costs between 1-4 bytes per character.
    2. So what does Python use in the Python interpreter?
        1. Python 2 uses ascii for strings, but has unicode strings available if you choose to use them.
        2. Python 3 uses unicode by default, so you never have to think about it.
        3. You can identify a unicode string because it will look like this: u'hello world'.
        4. How do you know if you are using Python 2 or 3? When you type the python command, you have to type `python3` to use Python 3 on most systems.
    3. What about your source code file, does that have to be ascii or unicode? [Lets check PEP 263](https://www.python.org/dev/peps/pep-0263/)
        1. The Python 2 interpreter defaults to decoding a source code file (a script) as ascii.
        2. In order to use a different encoding you need to specify it:
            1. emacs-friendly: `# -*- coding: utf-8 -*-`
            2. vim-friendly:`# vim: set fileencoding=utf-8 :`
            3. Precise definition from PEP 263: encoding must match the regular expression `"coding[:=]\s*([-\w.]+)"`
            4. you could use human friendly: `# this file uses the encoding: utf-8`
        3. What about Python 3?
            1. Python 3 uses utf-8 [as the default file coding](https://docs.python.org/3.3/howto/unicode.html#the-string-type)
            2. PEP 263 still applies to Python 3.
    4. Lets use Python 2 - Three types of string declarations:
        1. ascii = 'this is a string'
        2. unicode = u'this is a unicode string'
        3. raw = r'this needs no escapes'
    5. String escapes - a string will often need escapes.
        1.  Let's play with [escape sequences!](https://docs.python.org/2/reference/lexical_analysis.html#string-literals)
        ```python
        >>> 'hello world'
        >>> 'hello humans\' world'
        >>> '\\'
        >>> r'\\'
        >>> '\\\\'
        ```

3. ##### Lets play with some strings.

    1. First lets look inside a string
        1. Lets use the dir built-in method.
        ```python
        >>> mystring = "this is my string"
        >>> help(dir)
        >>> dir(mystring)
        ```
        2. These things are string methods. [Lets look at some](https://docs.python.org/2/library/stdtypes.html#string-methods)
            1. lower(), capitalize(), title()
    

    2. Now lets slice a string.
        1. [Reference documentation](https://docs.python.org/2/reference/expressions.html#slicings)
        2. [Slice Tutorial](https://docs.python.org/2/tutorial/introduction.html#strings)

    3. Substring Search - find a string that fits inside another string.
        1. How many instances of 'is' are in 'this is my string'?
        2. Lets work with some more string methods.
            1. find(), rfind(), 
            2. count()
            3. partition(), rpartition()
            4. split()

    4. Iterating over a list of strings:
        1. Again, we use the for... in pattern:

    5. Regular Expressions - Know they exist; try them out sometime.
        1. Regular expressions are strings that can match a SET of regular strings.
            1. There's a lot to say about these
            2. Check out the Python `re` library, it is already on your computer.