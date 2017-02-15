
**Introduction to Python**
==========================

When I need to build a web app, I reach for Python. When I need to
automate some small task on my system, I reach for Python. When I want
to find the most common colors in an image, I reach for Python. When
I…OK, I think you get the picture. Basically, when I need to code
something and the language doesn’t matter, I use Python. So what is
Python?

Python is a general purpose programming language created in the late
1980s, and named after Monty Python, that’s used by thousands of people
to do things from testing microchips at Intel, to powering Instagram, to
building video games with the PyGame library. It’s small, very closely
resembles the English language, and has hundreds of existing third-party
libraries.

So what are the major reasons why I, personally, choose Python and
recommend it to as many people as possible? It comes down to three
reasons.

1. Readability
2. Libraries
3. Community

So lets get our hands dirty and write some Code!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: ipython2

    print "Not Hello world this time!"
    # comment


.. parsed-literal::

    Not Hello world this time!


The arithmetic operators +, -, \*, /, %, \*\*, //

\*\* Exponential calculation

// Floor Division

.. code:: ipython2

    print "5 + 2 =", 5+2
    print "5 - 2 =", 5-2
    print "5 * 2 =", 5*2
    print "5 / 2 =", 5/2
    print"5 % 2 =", 5%2
    print"5 ** 2 =", 5**2
    print"5 // 2 =", 5//2
     
    # Order of Operation states * and / is performed before + and -
     
    print"1 + 2 - 3 * 2 =", 1 + 2 - 3 * 2
    print"(1 + 2 - 3) * 2 =", (1 + 2 - 3) * 2


.. parsed-literal::

    5 + 2 = 7
    5 - 2 = 3
    5 * 2 = 10
    5 / 2 = 2
    5 % 2 = 1
    5 ** 2 = 25
    5 // 2 = 2
    1 + 2 - 3 * 2 = -3
    (1 + 2 - 3) * 2 = 0


.. code:: ipython2

    a = 5
    print a
    a = "string"
    print a


.. parsed-literal::

    5
    string


.. code:: ipython2

    # A string is a string of characters surrounded by " or '
    # If you must use a " or ' between the same quote escape it with \
    quote = "\"Always remember your unique,"
     
    # A multi-line quote
    multi_line_quote = ''' just 
    like everyone
    else '''
    print quote + multi_line_quote


.. parsed-literal::

    "Always remember your unique, just 
    like everyone
    else 


.. code:: ipython2

    # To embed a string in output use %s
    print"%s %s %s" % ('I like the quote', quote, multi_line_quote)
     
    # To keep from printing newlines use end=""
    print"I don't like ",
    print"newlines"
     
    # You can print a string multiple times with *
    print'hello\n' * 5


.. parsed-literal::

    I like the quote "Always remember your unique,  just 
    like everyone
    else 
    I don't like  newlines
    hello
    hello
    hello
    hello
    hello
    


.. code:: ipython2

    # LISTS -------------
    # A list allows you to create a list of values and manipulate them
    # Each value has an index with the first one starting at 0
     
    my_list = [1,'string',3, 4.05]
    print my_list
    print my_list[0]
     


.. parsed-literal::

    [1, 'string', 3, 4.05]
    1


Since Pythons philosophy is to keep it simple, you can have any type of
variable in list

.. code:: ipython2

    m_list = [my_list, 1]
    print m_list


.. parsed-literal::

    [[1, 'string', 3, 4.05], 1]


Slicing
-------

You can get a subset of the list with [min:up to but not including max]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: ipython2

     print my_list[1:3]
     print my_list


.. parsed-literal::

    ['string', 3]
    [1, 'string', 3, 4.05]


.. code:: ipython2

    my_list = [1,2,3,4,5,6,7]
    a_list = my_list[0:6:2]
    print a_list
    a_list = my_list[0:6:2]
    print a_list
    a_list = my_list[-1::-2]
    print a_list
    a_list = my_list[::-1]
    print a_list


.. parsed-literal::

    [1, 3, 5]
    [1, 3, 5]
    [7, 5, 3, 1]
    [7, 6, 5, 4, 3, 2, 1]


Other List functions implemented below
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: ipython2

    grocery_list = ['Juice', 'Tomatoes', 'Potatoes', 'Bananas']
     
    # You can change the value stored in a list box
    grocery_list[0] = "Green Juice"
    print grocery_list
     
    # You can get a subset of the list with [min:up to but not including max]
     
    print grocery_list[1:3]
     
    # You can put any data type in a a list including a list
    other_events = ['Wash Car', 'Pick up Kids', 'Cash Check']
    to_do_list = [other_events, grocery_list]
     
    print to_do_list
     
    # Get the second item in the second list (Boxes inside of boxes)
    print to_do_list[1][1]
     
    # You add values using append
    grocery_list.append('onions')
    print to_do_list
     
    # Insert item at given index
    grocery_list.insert(1, "Pickle")
     
    # Remove item from list
    grocery_list.remove("Pickle")
     
    # Sorts items in list
    grocery_list.sort()
     
    # Reverse sort items in list
    grocery_list.reverse()
     
    # del deletes an item at specified index
    del grocery_list[4]
    print to_do_list
     
    # We can combine lists with a +
    to_do_list = other_events + grocery_list
    print(to_do_list)
     
    # Get length of list
    print(len(to_do_list))
     
    # Get the max item in list
    print(max(to_do_list))
     
    # Get the minimum item in list
    print(min(to_do_list))


.. parsed-literal::

    ['Green Juice', 'Tomatoes', 'Potatoes', 'Bananas']
    ['Tomatoes', 'Potatoes']
    [['Wash Car', 'Pick up Kids', 'Cash Check'], ['Green Juice', 'Tomatoes', 'Potatoes', 'Bananas']]
    Tomatoes
    [['Wash Car', 'Pick up Kids', 'Cash Check'], ['Green Juice', 'Tomatoes', 'Potatoes', 'Bananas', 'onions']]
    [['Wash Car', 'Pick up Kids', 'Cash Check'], ['onions', 'Tomatoes', 'Potatoes', 'Green Juice']]
    ['Wash Car', 'Pick up Kids', 'Cash Check', 'onions', 'Tomatoes', 'Potatoes', 'Green Juice']
    7
    onions
    Cash Check


.. code:: ipython2

    dir(my_list)




.. parsed-literal::

    ['__add__',
     '__class__',
     '__contains__',
     '__delattr__',
     '__delitem__',
     '__delslice__',
     '__doc__',
     '__eq__',
     '__format__',
     '__ge__',
     '__getattribute__',
     '__getitem__',
     '__getslice__',
     '__gt__',
     '__hash__',
     '__iadd__',
     '__imul__',
     '__init__',
     '__iter__',
     '__le__',
     '__len__',
     '__lt__',
     '__mul__',
     '__ne__',
     '__new__',
     '__reduce__',
     '__reduce_ex__',
     '__repr__',
     '__reversed__',
     '__rmul__',
     '__setattr__',
     '__setitem__',
     '__setslice__',
     '__sizeof__',
     '__str__',
     '__subclasshook__',
     'append',
     'count',
     'extend',
     'index',
     'insert',
     'pop',
     'remove',
     'reverse',
     'sort']



.. code:: ipython2

    help(my_list.append)


.. parsed-literal::

    Help on built-in function append:
    
    append(...)
        L.append(object) -- append object to end
    


.. code:: ipython2

    # TUPLES -------------
    # Values in a tuple can't change like lists
     
    pi_tuple = (3, 1, 4, 1, 5, 9)
    # Convert tuple into a list
    
    new_tuple = list(pi_tuple)
    print new_tuple
    # Convert a list into a tuple
    new_list = tuple(grocery_list)
    print new_list
    # tuples also have len(tuple), min(tuple) and max(tuple)
     
     


.. parsed-literal::

    [3, 1, 4, 1, 5, 9]
    ('onions', 'Tomatoes', 'Potatoes', 'Green Juice')


Dictionary
----------

.. code:: ipython2

    # DICTIONARY or MAP -------------
    # Made up of values with a unique key for each value
    # Similar to lists, but you can't join dicts with a +
     
    super_villains = {'Fiddler' : 'Isaac Bowin',
                      'Fiddler' : 'Isaac B',
                      'Captain Cold' : 'Leonard Snart',
                      'Captain Cold' : 'Leonarart',
                      'Weather Wizard' : 'Mark Mardon',
                      'Mirror Master' : 'Sam Scudder',
                      'Pied Piper' : 'Thomas Peterson'}
     
    print(super_villains['Captain Cold'])
     
    # Delete an entry
    del super_villains['Fiddler']
    print(super_villains)
     
    # Replace a value
    super_villains['Pied Piper'] = 'Hartley Rathaway'
     
    # Print the number of items in the dictionary
    print(len(super_villains))
     
    # Get the value for the passed key
    print(super_villains.get("Pied Piper"))
     
    # Get a list of dictionary keys
    print(super_villains.keys())
     
    # Get a list of dictionary values
    print(super_villains.values())


.. parsed-literal::

    Leonarart
    {'Mirror Master': 'Sam Scudder', 'Pied Piper': 'Thomas Peterson', 'Captain Cold': 'Leonarart', 'Weather Wizard': 'Mark Mardon'}
    4
    Hartley Rathaway
    ['Mirror Master', 'Pied Piper', 'Captain Cold', 'Weather Wizard']
    ['Sam Scudder', 'Hartley Rathaway', 'Leonarart', 'Mark Mardon']


.. code:: ipython2

    # STRINGS -------------
    # A string is a series of characters surrounded by ' or "
    long_string = "I'll catch you if you fall - The Floor"
     
    # Retrieve the first 4 characters
    print(long_string[0:4])
     
    # Get the last 5 characters
    print(long_string[-5:])
     
    # Everything up to the last 5 characters
    print(long_string[:-5])
     
    # Concatenate part of a string to another
    print(long_string[:4] + " be there")
     
    # String formatting
    print("%c is my %s letter and my number %d number is %.5f" % ('X', 'favorite', 1, .14))
     
    # Capitalizes the first letter
    print(long_string.capitalize())
     
    # Returns the index of the start of the string
    # case sensitive
    print(long_string.find("Floor"))
     
    # Returns true if all characters are letters ' isn't a letter
    print(long_string.isalpha())
     
    # Returns true if all characters are numbers
    print(long_string.isalnum())
     
    # Returns the string length
    print(len(long_string))
     
    # Replace the first word with the second (Add a number to replace more)
    print(long_string.replace("Floor", "Ground"))
     
    # Remove white space from front and end
    print(long_string.strip())
     
    # Split a string into a list based on the delimiter you provide
    quote_list = long_string.split(" ")
    print(quote_list)
     


.. parsed-literal::

    I'll
    Floor
    I'll catch you if you fall - The 
    I'll be there
    X is my favorite letter and my number 1 number is 0.14000
    I'll catch you if you fall - the floor
    33
    False
    False
    38
    I'll catch you if you fall - The Ground
    I'll catch you if you fall - The Floor
    ["I'll", 'catch', 'you', 'if', 'you', 'fall', '-', 'The', 'Floor']


CONDITIONALS
^^^^^^^^^^^^

The if, else and elif statements are used to perform different actions
based off of conditions

Comparison Operators : \*\* ==, !=, >, <, >=, <= \*\*

The if statement will execute code if a condition is met

White space is used to group blocks of code in Python

Use the same number of proceeding spaces for blocks of code

.. code:: ipython2

    # You can combine conditions with logical operators
    # Logical Operators : and, or, not
    age = 15
    if age >= 1 and age <= 18:
        print("You get a birthday party")
        print "yo"
    elif age == 21 or age >= 65:
        print("You get a special birthday party")
    elif not age == 30:
        print("You don't get a birthday party")
    else:
        print("You get a birthday party yeah")
     


.. parsed-literal::

    You get a birthday party
    yo


Loop Contructs
~~~~~~~~~~~~~~

.. code:: ipython2

    for i in range(0,10):
        print i

.. code:: ipython2

    print a_list
    for x in a_list:
        print x,


.. parsed-literal::

    [7, 6, 5, 4, 3, 2, 1]
    7 6 5 4 3 2 1


.. code:: ipython2

    # You can double up for loops to cycle through lists
    num_list =[[1,2,3],[10,20,30],[100,200,300]];
     
    for x in range(0,3):
        for y in range(0,3):
            print num_list[x][y],

.. code:: ipython2

    v_str = 'python loves you'
     
    # Take steps of 2 in a string sequence
    for x in v_str[0::2]:    
        print x,
     
    print "---"
     
    # Now reverse the order
    for x in v_str[-1::-1]:   
        print x,

.. code:: ipython2

    # WHILE LOOPS -------------
    # While loops are used when you don't know ahead of time how many
    # times you'll have to loop
    # An iterator for a while loop is defined before the loop
    i = 0
    while (i <= 20):
        if(i%2 == 0):
            print(i)
        elif(i == 9):
            # Forces the loop to end all together
            break
        else:
            # Shorthand for i = i + 1
            i += 1
            # Skips to the next iteration of the loop
            continue
        i += 1
    print "outside while loop", i

Functions
~~~~~~~~~

.. code:: ipython2

    # FUNCTIONS -------------
    # Functions allow you to reuse and write readable code
    # Type def (define), function name and parameters it receives
    # return is used to return something to the caller of the function
    def addNumbers(fNum, sNum):
        sumNum = fNum + sNum
        return sumNum,fNum
    addNumbers(56,3)
    addNumbers("number 1"," number 2")




.. parsed-literal::

    ('number 1 number 2', 'number 1')



.. code:: ipython2

    # NOTE ON ALIASING
    def do_something(arg):
        print id(arg)
        arg += 2
        return arg
        #args.append(1)
    x = 5
    do_something(x)
    print x, id(x)


.. parsed-literal::

    43634968
    5 43634968


.. code:: ipython2

    def do_something(arg):
        arg = arg * 2 # BREAKS alisasing
        arg.append(1)
    x = [5]
    do_something(x)
    print x


.. parsed-literal::

    [5]


PIP
---

Python Package index
~~~~~~~~~~~~~~~~~~~~

.. code:: ipython2

    #LINUX OR MACOS USERS
    #sudo easy_install pip
    #sudo pip <command> <args>
    sudo pip install requests

.. code:: ipython2

    # Windows
    #python -m pip install -U pip setuptools
    python
    import pip
    #go to terminal
    python -m pip install requests
    python
    import requests
    #python -m pip install <package-name>

.. code:: ipython2

    # for those on Windows having problem visit 
    #http://stackoverflow.com/questions/4750806/how-do-i-install-pip-on-windows?rq=1


.. code:: ipython2

    #pip
    #pip install
    #pip download
    #pip uninstall
    #pip freeze
    #pip list
    #pip show
    #pip search
    #pip wheel
    #pip hash

.. code:: ipython2

    #pip install requests            # latest version
    #pip install SomePackage==1.0.4     # specific version
    #pip install 'SomePackage>=1.0.4'     # minimum version
    #sudo pip install requests>=2.12.5
    #sudo pip install BeautifulSoup
    #-I, ignore installed
    #--upgrade
    #pip uninstall [options] <package> 
    #pip seach modulename
    #pip list
    #pip show <modulename>

