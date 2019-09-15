---
title: How dictionaries are implemented in the Python language
author: Denis Trofimov
type: post
date: 2018-09-28T19:12:58+00:00
url: /how-dictionaries-are-implemented-in-the-python-language/
featured_image: The-hash-function-for-strings-in-Python-for-a-table-size-of-8.png
accesspress_mag_post_template_layout:
  - global-template
accesspress_mag_sidebar_layout:
  - global-sidebar
categories:
  - learning
tags:
  - algorithms
  - code
  - data structures
  - interview
  - programming
  - python

---
<div class="story-content">
  <p>
    This post describes how dictionaries are implemented in the Python language.
  </p>
  
  <p>
    This article is actually a repost of originally posted at <a href="https://www.laurentluce.com/posts/python-dictionary-implementation/">Laurent Luce&#8217;s Blog</a> August 29, 2011 by Laurent Luce. I mentor several students of russian <a href="https://learn.python.ru/">Learn Python</a> courses. They have questions about structures in Python and how to use them. I found this post a good help to me and possibly to my students.
  </p>
</div>

<!--more-->

Dictionaries are indexed by keys and they can be seen as associative arrays. Let’s add 3 key/value pairs to a dictionary:

```py
>>> d = {'a': 1, 'b': 2}
>>> d['c'] = 3
>>> d
{'a': 1, 'b': 2, 'c': 3}
```

The values can be accessed this way:

```py
>>> d['a']
1
>>> d['b']
2
>>> d['c']
3
>>> d['d']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'd'
```
  
The key ‘d’ does not exist so a KeyError exception is raised.
  
## Hash tables

Python dictionaries are implemented using hash tables. It is an array whose indexes are obtained using a hash function on the keys. The goal of a hash function is to distribute the keys evenly in the array. A good hash function minimizes the number of collisions e.g. different keys having the same hash. Python does not have this kind of hash function. Its most important hash functions (for strings and ints) are very regular in common cases:

```py
>>> map(hash, (0, 1, 2, 3))
[0, 1, 2, 3]
>>> map(hash, ("namea", "nameb", "namec", "named"))
[-1658398457, -1658398460, -1658398459, -1658398462]
```

We are going to assume that we are using strings as keys for the rest of this post. The hash function for strings in Python is defined as:

```py
arguments: string object
returns: hash
function string_hash:
    if hash cached:
        return it
    set len to string's length
    initialize var p pointing to 1st char of string object
    set x to value pointed by p left shifted by 7 bits
    while len >= 0:
        set var x to (1000003 * x) xor value pointed by p
        increment pointer p
    set x to x xor length of string object
    cache x as the hash so we don't need to calculate it again
    return x as the hash
```

If you run hash(‘a’) in Python, it will execute string_hash() and return 12416037344. Here we assume we are using a 64-bit machine.

If an array of size x is used to store the key/value pairs then we use a mask equal to x-1 to calculate the slot index of the pair in the array. This makes the computation of the slot index fast. The probability to find an empty slot is high due to the resizing mechanism described below. This means that having a simple computation makes sense in most of the cases. If the size of the array is 8, the index for ‘a’ will be: hash(‘a’) & 7 = 0. The index for ‘b’ is 3, the index for ‘c’ is 2, the index for ‘z’ is 3 which is the same as ‘b’, here we have a collision.
  
  <p>
    <img class="alignnone" src="https://www.laurentluce.com/images/blog/dict/hash.png" alt="The hash function for strings in Python for a table size of 8" width="375" height="311" />
  </p>
  
  <p>
    We can see that the Python hash function does a good job when the keys are consecutive which is good because it is quite common to have this type of data to work with. However, once we add the key ‘z’, there is a collision because it is not consecutive enough.
  </p>
  
  <p>
    We could use a linked list to store the pairs having the same hash but it would increase the lookup time e.g. not O(1) average anymore. The next section describes the collision resolution method used in the case of Python dictionaries.
  </p>
  
  <h2>
    Open addressing
  </h2>
  
  <p>
    Open addressing is a method of collision resolution where probing is used. In case of ‘z’, the slot index 3 is already used in the array so we need to probe for a different index to find one which is not already used. Adding a key/value pair will average O(1) and the lookup operation too.
  </p>
  
  <p>
    A quadratic probing sequence is used to find a free slot. The code is the following:
  </p>

```c
j = (5*j) + 1 + perturb;
perturb >>= PERTURB_SHIFT;
use j % 2**i as the next table index;
```
  
  <p>
    Recurring on 5*j+1 quickly magnifies small differences in the bits that didn’t affect the initial index. The variable “perturb” gets the other bits of the hash code into play.
  </p>
  
  <p>
    Just out of curiosity, let’s look at the probing sequence when the table size is 32 and j = 3.<br /> 3 -> 11 -> 19 -> 29 -> 5 -> 6 -> 16 -> 31 -> 28 -> 13 -> 2…
  </p>
  
  <p>
    You can read more about this probing sequence by looking at the source code of <a href="http://svn.python.org/projects/python/trunk/Objects/dictobject.c">dictobject.c</a>. A detailed explanation of the probing mechanism can be found at the top of the file.
  </p>
  
  <p>
    <img src="https://www.laurentluce.com/images/blog/dict/probing.png" alt="open addressing" />
  </p>
  
  <p>
    Now, let’s look at the Python internal code along with an example.
  </p>
  
  <h2>
    Dictionary C structures
  </h2>
  
  <p>
    The following C structure is used to store a dictionary entry: key/value pair. The hash, key and value are stored. PyObject is the base class of the Python objects.
  </p>
  
```c
typedef struct {
  Py_ssize_t me_hash;
  PyObject *me_key;
  PyObject *me_value;
} PyDictEntry;
```

  <p>
    The following structure represents a dictionary. ma_fill is the number of used slots + dummy slots. A slot is marked dummy when a key pair is removed. ma_used is the number of used slots (active). ma_mask is equal to the array’s size minus 1 and is used to calculate the slot index. ma_table is the array and ma_smalltable is the initial array of size 8.
  </p>
  
```c
typedef struct _dictobject PyDictObject;
struct _dictobject {
    PyObject_HEAD
    Py_ssize_t ma_fill;
    Py_ssize_t ma_used;
    Py_ssize_t ma_mask;
    PyDictEntry *ma_table;
    PyDictEntry *(*ma_lookup)(PyDictObject *mp, PyObject *key, long hash);
    PyDictEntry ma_smalltable[PyDict_MINSIZE];
};
```
  
## Dictionary initialization
  
  <p>
    When you first create a dictionary, the function PyDict_New() is called. I removed some of the lines and converted the C code to pseudocode to concentrate on the key concepts.
  </p>

```c
returns new dictionary object
function PyDict_New:
    allocate new dictionary object
    clear dictionary's table
    set dictionary's number of used slots + dummy slots (ma_fill) to 0
    set dictionary's number of active slots (ma_used) to 0
    set dictionary's mask (ma_value) to dictionary size - 1 = 7
    set dictionary's lookup function to lookdict_string
    return allocated dictionary object
```
  
  <h2>
    Adding items
  </h2>
  
  <p>
    When a new key/value pair is added, PyDict_SetItem() is called. This function takes a pointer to the dictionary object and the key/value pair. It checks if the key is a string and calculates the hash or reuses the one cached if it exists. insertdict() is called to add the new key/value pair and the dictionary is resized if the number of used slots + dummy slots is greater than 2/3 of the array’s size.<br /> Why 2/3? It is to make sure the probing sequence can find a free slot fast enough. We will look at the resizing function later.
  </p>
  
```py
arguments: dictionary, key, value
returns: 0 if OK or -1
function PyDict_SetItem:
    if key's hash cached:
        use hash
    else:
        calculate hash
    call insertdict with dictionary object, key, hash and value
    if key/value pair added successfully and capacity over 2/3:
        call dictresize to resize dictionary's table
```
  
  <p>
    inserdict() uses the lookup function lookdict_string() to find a free slot. This is the same function used to find a key. lookdict_string() calculates the slot index using the hash and the mask values. If it cannot find the key in the slot index = hash & mask, it starts probing using the loop described above, until it finds a free slot. At the first probing try, if the key is null, it returns the dummy slot if found during the first lookup. This gives priority to re-use the previously deleted slots.
  </p>
  
  <p>
    We want to add the following key/value pairs: {‘a’: 1, ‘b’: 2′, ‘z’: 26, ‘y’: 25, ‘c’: 5, ‘x’: 24}. This is what happens:
  </p>
  
  <p>
    A dictionary structure is allocated with internal table size of 8.
  </p>
  
<ul>
<li>PyDict_SetItem: key = &#8216;a&#8217;, value = 1</li>
<ul>
<li>hash = hash(&#8216;a&#8217;) = 12416037344</li>
<li>insertdict</li>
<ul>
<li>lookdict_string</li>
<ul>
<li>slot index = hash &#038; mask = 12416037344 &#038; 7 = 0</li>
<li>slot 0 is not used so return it</li>
</ul>
<li>init entry at index 0 with key, value and hash</li>
<li>ma_used = 1, ma_fill = 1</li>
</ul>
</ul>
<li>PyDict_SetItem: key = &#8216;b&#8217;, value = 2</li>
<ul>
<li>hash = hash(&#8216;b&#8217;) = 12544037731</li>
<li>insertdict</li>
<ul>
<li>lookdict_string</li>
<ul>
<li>slot index = hash &#038; mask = 12544037731 &#038; 7 = 3</li>
<li>slot 3 is not used so return it</li>
</ul>
<li>init entry at index 3 with key, value and hash</li>
<li>ma_used = 2, ma_fill = 2</li>
</ul>
</ul>
<li>PyDict_SetItem: key = &#8216;z&#8217;, value = 26</li>
<ul>
<li>hash = hash(&#8216;z&#8217;) = 15616046971</li>
<li>insertdict</li>
<ul>
<li>lookdict_string</li>
<ul>
<li>slot index = hash &#038; mask = 15616046971 &#038; 7 = 3</li>
<li>slot 3 is used so probe for a different slot: 5 is free</li>
</ul>
<li>init entry at index 5 with key, value and hash</li>
<li>ma_used = 3, ma_fill = 3</li>
</ul>
</ul>
<li>PyDict_SetItem: key = &#8216;y&#8217;, value = 25</li>
<ul>
<li>hash = hash(&#8216;y&#8217;) = 15488046584</li>
<li>insertdict</li>
<ul>
<li>lookdict_string</li>
<ul>
<li>slot index = hash &#038; mask = 15488046584 &#038; 7 = 0</li>
<li>slot 0 is used so probe for a different slot: 1 is free</li>
</ul>
<li>init entry at index 1 with key, value and hash</li>
<li>ma_used = 4, ma_fill = 4</li>
</ul>
</ul>
<li>PyDict_SetItem: key = &#8216;c&#8217;, value = 3</li>
<ul>
<li>hash = hash(&#8216;c&#8217;) = 12672038114</li>
<li>insertdict</li>
<ul>
<li>lookdict_string</li>
<ul>
<li>slot index = hash &#038; mask = 12672038114 &#038; 7 = 2</li>
<li>slot 2 is free so return it</li>
</ul>
<li>init entry at index 2 with key, value and hash</li>
<li>ma_used = 5, ma_fill = 5</li>
</ul>
</ul>
<li>PyDict_SetItem: key = &#8216;x&#8217;, value = 24</li>
<ul>
<li>hash = hash(&#8216;x&#8217;) = 15360046201</li>
<li>insertdict</li>
<ul>
<li>lookdict_string</li>
<ul>
<li>slot index = hash &#038; mask = 15360046201 &#038; 7 = 1</li>
<li>slot 1 is used so probe for a different slot: 7 is free</li>
</ul>
<li>init entry at index 7 with key, value and hash</li>
<li>ma_used = 6, ma_fill = 6</li>
</ul>
</ul>
</ul>

  
  <p>
    This is what we have so far:
  </p>
  
  <p>
    <img src="https://www.laurentluce.com/images/blog/dict/insert.png" alt="python dictionary insert" />
  </p>
  
  <p>
    6 slots on 8 are used now so we are over 2/3 of the array’s capacity. dictresize() is called to allocate a larger array. This function also takes care of copying the old table entries to the new table.
  </p>
  
  <p>
    dictresize() is called with minused = 24 in our case which is 4 * ma_used. 2 * ma_used is used when the number of used slots is very large (greater than 50000). Why 4 times the number of used slots? It reduces the number of resize steps and it increases sparseness.
  </p>
  
  <p>
    The new table size needs to be greater than 24 and it is calculated by shifting the current size 1 bit left until it is greater than 24. It ends up being 32 e.g. 8 -> 16 -> 32.
  </p>
  
  <p>
    This is what happens with our table during resizing: a new table of size 32 is allocated. Old table entries are inserted into the new table using the new mask value which is 31. We end up with the following:
  </p>
  
  <p>
    <img src="https://www.laurentluce.com/images/blog/dict/resizing.png" alt="python dictionary table resizing" />
  </p>
  
  <h2>
    Removing items
  </h2>
  
  <p>
    PyDict_DelItem() is called to remove an entry. The hash for this key is calculated and the lookup function is called to return the entry. The slot is now a dummy slot.
  </p>
  
  <p>
    We want to remove the key ‘c’ from our dictionary. We end up with the following array:
  </p>
  
  <p>
    <img src="https://www.laurentluce.com/images/blog/dict/delete.png" alt="Python dictionary delete key" />
  </p>
  
  <p>
    Note that the delete item operation doesn’t trigger an array resize if the number of used slots is much less that the total number of slots. However, when a key/value pair is added, the need for resize is based on the number of used slots + dummy slots so it can shrink the array too.
  </p>
  
  <p>
    That’s it for now. I hope you enjoyed the article. Please write a comment if you have any feedback.
  </p>
</div>

<!--more-->

<!--more-->

<div class="metawrap">
  <p>
    &nbsp;
  </p>
  
  <p>
    <em>Originally posted at <a href="https://www.laurentluce.com/posts/python-dictionary-implementation/">Laurent Luce&#8217;s Blog</a> August 29, 2011 by Laurent Luce.</em>
  </p>
</div>