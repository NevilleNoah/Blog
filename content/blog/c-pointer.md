+++
categories = ["C/C++"]
date = 2020-02-22T16:00:00Z
description = "Let you fully understand how to use C Pointer."
draft = true
image = ""
tags = ["C/C++"]
title = "C Pointer"
type = "post"

+++
You may be immersed in pain due to C Pointer. 

'*' and '&' baffle you?

Don't worry! Today I'll help you to get it all at once.

Note: For the convenience of discussion, our discuss will be based on 32 bit to make sure our size of **int** is 4B.

# Ordinary variables and Pointer variables

Declaring variables：

    // Ordinary variables
    int ordinary = 1;
    
    // Pointer variables
    int * pointer = 2;

We all know **ordinary**'s type is **int**.But do you know what **pointer**'s type is?

**pointer**'s type is __int *__, you must remember __int *__ then  **pointer** rather than **int** then *** pointer**.

The First important thing should be repeat three times. Let us repeat it:

* __int *__ then  **pointer**
* __int *__ then  **pointer**
* __int *__ then  **pointer**

When we execute:

    int * pointer = 2;
    * pointer = 10;
    int num = * pointer;

Memory as shown below:

![](/images/post/0E040117-5DAC-4E76-90B5-FBA37EE7226D.png)

**pointer** store the address,  *** pointer** store the value of address from 2 to 6 because the size of int is 4B,  **num** store the value from *** pointer**.

We know the *** pointer** 's address because we defined it. But we don't know **pointer** and **num** 's address. You can use **&** to get it when you need them. For example:

    printf("%d", &pointer);
    printf("%d", &num);

# Formal Parameter