<div align="center">

## Read: "Avoiding new operator failure" from my new book\-&gt; " 0 error\(s\) \- 0 warning\(s\)"


</div>

### Description

Avoiding runtime errors caused by the "new" operator using exception handling with simple three different methods
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[ahmed mohamed alaa](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/ahmed-mohamed-alaa.md)
**Level**          |Advanced
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |Microsoft Visual C\+\+
**Category**       |[Debugging and Error Handling](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/debugging-and-error-handling__3-6.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/ahmed-mohamed-alaa-read-avoiding-new-operator-failure-from-my-new-book-gt-0-error-s-0-warn__3-12317/archive/master.zip)





### Source Code

```

This article is extracted from my new book ; " 0 error(s) - 0 warning(s) " which will be published soon...
"In any programming language, arrays are the most popular and practical way for storing data, however, when allocating memory to be dedicated to an array in a C++ code, you must decide the number of elements in it when defining the array, without postponing this step to runtime.
 One might think of a code such as:
 cout<<”Enter the size of array”<<endl;
 cin>>array_size;
 int A[array_size];
 However, such code is not acceptable by the compiler as it demands a constant (static) memory allocation that can’t be changed in course of program execution…
 This problem can be solved thanks to the “new” operator , as in most programs the size of the array is not decided at the compile time, we use the “new’’ to capture a whole memory block and dedicate it to the array , such style is called “dynamic memory allocation” …
Now we can write the following code:
 cout<<”Enter the size of the array”<<endl;
 cin>>array_size;
 int* array_A ;
 array_A = new int [array_size];
In many occasions, the new operator fails to allocate memory for many reasons that are beyond the scope of this article, we will discuss 3 methods for avoiding this problem, and process new failures.
First method: The classical method!!
 A classical method is to check whether the pointer is equal to zero after dynamic allocation , the pointer is equal to zero if the new operator fails to allocate memory this can be checked by a very simple if statement after using the new operator.
Second method: Handling the exception!
 Using exception handling statements, we can write a try – catch statement that catches an exception called bad_alloc defined in the <new> library this can be illustrated by this code:
 #include<new>
 Using std::bad_alloc
 Void main (void)
 {
  Double *pointer [100];
    try
      {
        for (int i = 0; i < 100; i++)
      {
        Pointer[i] = new double [1000000];
    cout<<”Managed to allocate for”<<i<<”pointer”<<endl;
       }
       }
 catch( bad_alloc &b)
   {
     cout<<b.what () <<endl;
   }
return;
     }
    As you can see in the for loop within the try statement, I tried to allocate a million element for each of the 100 pointers trying to create a 100 x million matrix, this forces the compiler to fail at some point, that is when the new pointer throws “bad_alloc” exception and detect the failure of the operator, thus avoiding any runtime errors.
Third method: Setting a new handler!
 If you are not interested in throwing and catching , again you can include the <new> header and use “set_new_handler” , this function takes a pointer to function as an argument (a function with no arguments and returns void) , once registered , the passed function is called automatically instead of “bad_alloc” , to avoid runtime errors…"
To download the original text in Word format , visit my website AhmedMAlaa.webs.com, the book will be published soon and available at Amazon.cm
```

