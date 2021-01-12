# TipsNTricks
This repository includes various tips and tricks to solve different Coding Questions (in C++).

---  

+ ### To intialise a vector with given size and value.  
  For eg- Intialize a vector of size 5 and value of all elements as 0.  
  **Syntax :**  
  ```  
    vector<int> vector1(size, value);
  ```  
  
  ```
    vector<int> vector1(5, 0);
  ```   
  
---

+ ### To insert a map with digits as key and frequency of digits as value  
  ```  
    unordered_map<int,int> result;  
    for(int i=0; i<n; i++)  
    {  
      result[arr[i]]++;  
    }  
  ```  
  
---

+ ### To declare an integer with maximum / minimum value  
  ```  
    int max = INT_MAX;  
    int min = INT_MIN;  
  ```  
  
---
    
+ ### To find number of digits in factorial of a number (No. of digits < 10^6)  
    We know,  
    log(a*b) = log(a) + log(b)  

    Therefore  
    log( n! ) = log(1*2*3....... * n)   
              = log(1) + log(2) + ........ +log(n)  

    Now, observe that the floor value of log base 10 increased by 1, of any number, gives the number of digits present in that number.  

    Hence, output would be : floor(log(n!)) + 1.  
  ```
  int findDigits(int n) 
  { 

      if (n < 0) 
          return 0; 
      if (n <= 1) 
          return 1; 
      double digits = 0; 
      for (int i=2; i<=n; i++) 
          digits += log10(i); 

      return floor(digits) + 1; 
  } 
  ```  

---

+ ### To find number of digits in factorial of a number (No. of digits > 10^6)  
  We can use Kamenetsky’s formula to find our answer !

  It approximates the number of digits in a factorial by :
  f(x) =    log10( ((n/e)^n) * sqrt(2*pi*n))

  Thus, we can pretty easily use the property of logarithms to,
  f(x) = n* log10(( n/ e)) + log10(2*pi*n)/2
  
  ```
  long long findDigits(int n) 
  { 
    // factorial of -ve number  
    // doesn't exists 
    if (n < 0) 
        return 0; 
  
    // base case 
    if (n <= 1) 
        return 1; 
  
    // Use Kamenetsky formula to calculate 
    // the number of digits 
    double x = ((n * log10(n / M_E) +  
                 log10(2 * M_PI * n) / 
                 2.0)); 
  
    return floor(x) + 1; 
  } 
```

---
