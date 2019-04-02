---
title: 'Postupy: PIN kód ukazatelů a polí'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
ms.openlocfilehash: 0b75b9c59c24f276142f6b8b5d662f86bb04d177
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787038"
---
# <a name="how-to-pin-pointers-and-arrays"></a>Postupy: PIN kód ukazatelů a polí

Připnutí dílčí objekt definovaný v spravovaný objekt má za následek Připnutí celý objekt.  Například pokud je připnutý libovolný prvek pole, pak celé pole je také připnout. Nejsou žádná rozšíření jazyka pro deklarování připnuté pole. Chcete-li připnout pole, deklarujte ukazatel Připnutí a jeho typ elementu, Připne jeden z jeho prvků.

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

```cpp
// pin_ptr_array.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

int main() {
   array<Byte>^ arr = gcnew array<Byte>(4);
   arr[0] = 'C';
   arr[1] = '+';
   arr[2] = '+';
   arr[3] = '\0';
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned
   unsigned char * cp = p;

   printf_s("%s\n", cp); // bytes pointed at by cp
                         // will not move during call
}
```

```Output
++
```

## <a name="see-also"></a>Viz také

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)