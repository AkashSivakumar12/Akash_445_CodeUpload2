# Akash_445_CodeUpload2
## Hackerrank Code Used
### Problem 1
Printing Pattern Using Loops
```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() 
{

    int n;
    scanf("%d", &n);
    int len = (n*2)-1;
    for(int i=0;i<len;i++)
    {
        for(int j=0;j<len;j++)
        {
            int min = i<j?i:j;
            min=min<len-i?min:len-i-1;
            min=min<len-j-1?min:len-j-1;
            printf("%d ",n-min);
        }
        printf("\n");
    }
}
```
### Problem 2
Power digit sum
```
#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <assert.h>
#include <limits.h>
#include <stdbool.h>

#define size_of_number 3330 
#define base 10

void find_power(int number[], int num, int exponent)
{
    int i, first_digit;
    int carry, replace, product, power_counter;


    first_digit = 0;
    number[first_digit] = 1; 
  
    for(power_counter = 1; power_counter <= exponent; power_counter++)
    {
       
        carry = 0;
        for(i = 0; i <= first_digit; i++)
        {
            product = num*number[i] + carry;
            replace = product%base; 
            carry = product/base; 

            number[i] = replace;

            
            if( (i == first_digit) && (carry > 0) )
            {
                first_digit++;
            }
        }

    }
}

int sum_of_digits(int number[])
{
    int i, sum = 0;


    for(i = 0; i < size_of_number; i++)
    {
        sum = sum + number[i];
    }
    return sum;
}

void solve()
{
    int number[size_of_number] = {0}, sum, exponent, num = 2;
    scanf("%d", &exponent);

    find_power(number, num, exponent);
    sum = sum_of_digits(number);
    printf("%d\n",sum);
}

int main()
{
    int no_of_queries;
    scanf("%d", &no_of_queries);
    while(no_of_queries-- != 0)
        solve();

    return 0;
}
```
### Problem 3
Even Fibonacci numbers
```
#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <assert.h>
#include <limits.h>
#include <stdbool.h>

int main()
{
 long int testcase;
 scanf("%lld",&testcase);
 while(testcase--)
 {
  long long int value,fact=0,temp=0,odd=1,even=2,count=0;
  scanf("%lld",&value);
  temp=value;
  while(temp--)
  {
   fact=odd+even;
   odd=even;
   even=fact;
   if(value>fact)
   {
   if(fact%2==0)
   count+=fact;
   }
   else
   break;
   
  }
  printf("%lld\n",count+2);
 }
 return 0;
}
```
### Problem 4
Largest palindrome product
```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int palindrome(long int v)
{
   
 long int reverse,n,i,j;
    n=v;
    while (n != 0)
   {
      reverse = reverse * 10;
      reverse = reverse + n%10;
      n       = n/10;
   }
    if(reverse==v)
    {
     for(i=100;i<=999;i++)
         {
         for(j=100;j<=999;j++)
          {
           if(i*j==v)
               return 1;

         }
     }
        return 0;
    }
    else
        {
        return 0;
    }
}
int main() {

    int t;
    scanf("%d",&t);
    while(t--)
        {
        long int val;
        scanf("%ld",&val);
        int f=0;
        while(f==0)
            {
            f=palindrome(--val);
        }
        printf("%ld\n",val);
    }
    return 0;
}
```
### Problem 5
Printing Tokens
```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {

    char *s;
    s = malloc(1024 * sizeof(char));
    scanf("%[^\n]", s);
    s = realloc(s, strlen(s) + 1);
    //Write your logic to print the tokens of the sentence here.
    int i;
    for(i=0; s[i]!='\0'; i++)
    {
      printf("%c", s[i]);

      if(s[i]==' ')
      {
         printf("\n");
      }
    }
    return 0;
}
```
### Problem 6
Multiples of 3 and 5
```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {
unsigned long long n,i,sum=0,t;
    scanf("%llu",&t);
    while(t--)
        {
   
        scanf("%lld",&n);
        --n;
         unsigned long long n1,n2,n3;
         n1=n/3;
         n2=n/5;
         n3=n/15;
         sum=(3*n1*(n1+1))/2+(5*n2*(n2+1))/2-(15*n3*(n3+1))/2;
         printf("%lld\n",sum);
    }
    return 0;
}
```
### Problem 7
Factorial digit sum
```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

     int res[10000],k=0;

void func(int x)
{
       int i,c=0;
       for(i=0;i<=k;i++)
       {
              res[i] = (res[i]*x) + c;
              c = res[i]/10;
              res[i] = res[i]%10;
       }
       while(c>0)
       {
              k++;
              res[k] = c%10;
              c= c/10;
       }
       return;
}


int main()
{
       int t;
       scanf("%d",&t);
       while(t--)
       {
              int n,i;
              scanf("%d",&n);
              k = 0;
              res[k] = 1;
              for(i=2;i<=n;i++)
              {
                     func(i);
              }
              unsigned long long int s=0;
              for(i=k;i>=0;i--)
              {
                     s = s+res[i];
              }
              printf("%llu\n",s);
       }
    return 0;
}
```
