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

When we see a function like:

    int * p = 1;
    int num = 1;
    
    int * test(int * sum) {
    	// execute something
    }

Don't fear it, it just tell us to input a pointer variables parameter, we can use it like this:

    test(p); //Right!pointer is a pointer variables.
    test(num); // Wrong!num is a ordinary variables.

Of course, even you use **test(num)**, you may pass compilation because here our num's type is **int**, and it will be automatically converted to __int *__, but I won't recommend you to do it due to it is logically wrong unless you have some special goals need to use such way to achieve.

# Array and Pointer

    int arr[] = {1, 3, 4};
    int * p = 1;

**arr** is a final pointer. According above content, we know we can change p's value as we wanna. We can let **p** to point address 2, or 4 or 10 and any address we hope. But we can't change the pointed address of **arr**.

As for formal parameter:

    // Way 1
    int * test(int * arr)
    // Way 2
    int * test(int arr[])

Actually, this two declaring ways is exactly the same. But I recommend you to use way 2, it not only help you to understand pointer, but is also in line with C/C++ writing habits.

Next, let us learn about loop:

    int main() {
    	int a[10];
        int * p;
        p = a; // p point the start address of arr
        * p = 10; // let a[0] = 10
        * (p+1) = 20; // let a[1] = 20. Note: here plus 1 means index plus 1 rather than address plus 1.
        
        for(int i = 0; i < 10; ++i)
        	*(p + i) = i;
        
        ++p; //p point a[1]
        printf("%d", p[0]); // p[0] == *p == a[1]
        p = a + 6; // p point a[6]
        printf("%d", *p); // output 6 because a[6]==6
        return 0;
    }