# YoSoy196
#include <string>
#include <iostream>
#include "BigIntegerLibrary.hh"

using namespace std;

bool is_palindrome(BigInteger n)
{
  string a = bigIntegerToString(n);
  a = string (a.rbegin(), a.rend());
  BigInteger b = stringToBigInteger(a);

  if (b == n)
  {
    return true;
  } else
  {
    return false;
  }
}

BigInteger apply196(BigInteger n)
{
  BigInteger result;
  string a = bigIntegerToString(n);
  a = string (a.rbegin(), a.rend());
  BigInteger b = stringToBigInteger(a);
  result = n + b;
  return result;
}


int main() {
  int UpperBound, LowerBound, NatPalindrome = 0, NonLychrel = 0, Lychrel = 0, counter;
  BigInteger Final;
  cout << "Hello I will calculate the number of natural palindrome, lychrel and nonlychrel numbers in a range"<< endl;
  cout << "Please give me the lower bound:"<< endl;
  cin >> LowerBound;
  cout << "Please give the upper bound:" << endl;
  cin >> UpperBound;

  for ( int i = LowerBound; i<= UpperBound; i++)
  {
    if (is_palindrome(i) == true)
    {
      NatPalindrome = NatPalindrome + 1;
    } else
    {
      Final = i;
      counter = 1;
      while (is_palindrome(Final) == false && counter <= 30)
      {
        Final = apply196(Final);
        counter++;
      }

      if (counter > 30){
        Lychrel = Lychrel + 1;
        cout << "Found a lychrel number: " << i << endl;
      } else {
        NonLychrel = NonLychrel + 1;
      }

    }

    }
  
  cout << "The results are: " << endl;
  cout << "In the range between " << LowerBound << " and " << UpperBound << ", we have:" << endl;
  cout << "Number of natural palindromes: " << NatPalindrome << endl;
  cout << "Number of non lychrel: " << NonLychrel << endl;
  cout << "Number of lychrel: " << Lychrel << endl;

  return 0;
}
