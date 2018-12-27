---
title: alignof a alignas (C++)
ms.date: 11/04/2016
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
ms.openlocfilehash: 825df25494497e13d29212f7f951be8247b6f136
ms.sourcegitcommit: 185b8ee6dd4e10045df730c5b957b9729813da2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411920"
---
# <a name="alignof-and-alignas-c"></a>alignof a alignas (C++)

**Alignas** je specifikátor typu portable, C++ standardní způsob, jak určit vlastní zarovnání proměnné a uživatelsky definované typy. **Alignof** operátor je také standardní, přenosný způsob, jak získat zarovnání zadaného typu nebo proměnné.

## <a name="example"></a>Příklad

Můžete použít **alignas** na třídu, strukturu nebo sjednocení nebo na jednotlivé členy. Když více **alignas** specifikátory vyskytují, kompilátor zvolí nejpřísnější jeden, (ta největší hodnotou).

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>Viz také:

[Zarovnání](../cpp/alignment-cpp-declarations.md)
