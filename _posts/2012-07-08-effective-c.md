---
layout: post
title: "Effective C++"
description: ""
category: 
tags: []
---
{% include JB/setup %}

## Item 2: Prefer cons, enum, and inline to #define

* Use "the enum hack" to declare constant which only affective inside class or specified code block
* Avoid macros.  Use template and inline instead.

    template &lt;typename T &gt;
    inline void callWithMax(const T& a, const T& b)
    {
      f(a > b ? a : b);
    }

## Item 3: Use const whenever possible 

* const to STL iterator works differently than ordinal pointer

    const T *p;   // p points to T which is constant
    T * const p;  // p is a const pointer to a mutable T

    const std::vector &lt;int&gt;::iterator iter = vc.begin(); //iter is as int * const iter
    *iter = 10;   // OK 
    ++iter;       // NG

    std::vector &lt;int&gt;::const_iterator iter = vc.begin(); //iter is as const int *iter
    *iter = 10;   // NG
    ++iter;       //OK

## Item 4: Make sure that objects are initialized before they're used

* C++ version of singleton

    FileSystem& tfs()   //The file system
    {
      static FileSystem fs;
      return fs;
    }

    ...
    std::size_t disk = tfs().numDisks();


## Item 5: Know what functions C++ silently writes and calls

### IMPORTANT: C++ does not provide a way to make a reference refer to a different object!!

* Reference is a object.

    MyClass a;
    MyClass b;
    MyClacc& ref_a = a;
    ref_a = b;          // Now a is equal to b

* If class includes a reference or a const member, compiler does not generate default copy constructor and default copy assignment operator.


## Item 6: Explicitly disallow the use of compiler generated functions you do not want

## Item 7: Declare destructors virtual in polymorphic base class

* Only for classes which meant to be polymorphic base class
* STL containers and string are not to designed to be polymorphic base class so no virtual declarations are made for their destructors.

### Pure virtual destructor needs definition.  (Not for other pure virtual member functions which will never called)
* desctuctor of base classes, even they are pure virtual, will be called when a destructor of their derived class is called.  Therefore, we need a definition.

    class Base
    {
      virtual ~Base() = 0;
    }

    ~Base::Base(){}


