# Work

## Colour Values

You are creating a colour processing program, and need to get the colour information out of the given data. Use bitwise operators to extract the Alpha, Red, Green, and Blue components out of the given 32 bit unsigned integer.

```
32 bit colour data = 00000000 00000000 00000000 00000000
                     [ 8 bits: Alpha | 8 bits: Red | 8 bits: Green | 8 bits: Blue ]
```

Given the input 4281403152, the program should output:  
**Alpha**: 255  
**Red**: 49  
**Green**: 7  
**Blue**: 16

```cpp
#include <iostream>
using namespace std;

void processColours(unsigned int colours)
{
  unsigned int alpha = ...;
  unsigned int red = ...;
  unsigned int green = ...;
  unsigned int blue = ...;
  
  cout << alpha << endl
       << red   << endl
       << green << endl
       << blue  << endl;
}

int main()
{
  unsigned int colours = 4281403152;
  
  processColours(colours);
  
  return 0;
}
```
