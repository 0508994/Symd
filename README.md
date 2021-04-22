# Symd
C++ header only template library designed to make it easier to write high-performance (vector, multi-threaded), image and data processing code on modern machines. It automatically generates vector (SIMD, SSE, AVX, NEON) code.

## Usage
Symd is a header-only library. To use Symd in your project you need to:

 * Copy LibSymd/include folder to your project
 * Include symd.h
 * And you are ready to go

Simple map example:

```cpp
#include <iostream>
#include "../LibSymd/include/symd.h"


void main()
{
    std::vector<int> input = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
    std::vector<int> output(input.size());

    symd::map(output, [](auto x) { return x * 2; }, input);

    for (auto x : output)
        std::cout << x << ", ";
}
```

Output:

```
2, 4, 6, 8, 10, 12, 14, 16, 18,
```

## Requirements

C++17 is requirement.

### Compiler

For development and testing we use Visual Studio 2019 latest updated (16.9.4), with /std:c++17 setting. Library should work on GCC and Clang as well but is currently not tested and probably would require a few tweeks.

### CPU

 * Intel or AMD x64 CPU with [AVX support](https://en.wikipedia.org/wiki/Advanced_Vector_Extensions). Roughly CPUs from 2011 and later.
 * ARM based CPUs with Neon support - still in beta phase.




