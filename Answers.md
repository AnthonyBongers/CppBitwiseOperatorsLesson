# Work Answers

## Colour Values

```cpp
#include <iostream>
using namespace std;

void processColours(unsigned int colours)
{
  const unsigned int mask = 255;
  
  unsigned int alpha = (colours >> 24) & mask;
  unsigned int red =   (colours >> 16) & mask;
  unsigned int green = (colours >> 8)  & mask;
  unsigned int blue =  (colours >> 0)  & mask;

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
