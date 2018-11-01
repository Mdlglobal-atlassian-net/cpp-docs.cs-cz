---
title: Přenositelnost u rozhraní ABI (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: 12f60b92e71c15a94546e5b099c3b49e3685b68b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549952"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>Přenositelnost u rozhraní ABI (moderní verze jazyka C++)

Použití dostatečně přenosné typy a pravidla týkající se na binární rozhraní hranice. "Přenosné type" je předdefinovaný typ jazyka C nebo struktura, která obsahuje pouze předdefinované typy jazyka C. Typy tříd jde použít jenom při volajícím a volaným shodnout na rozložení, volání konvence atd. To je možné, pouze když obě jsou kompilovány pomocí stejného kompilátoru a nastavení kompilátoru.

## <a name="how-to-flatten-a-class-for-c-portability"></a>Jak sloučit třídy pro přenositelnost jazyka C

Když volající může být kompilována s jinou kompilátoru a jazyk a pak "sloučit" k **extern "C"** rozhraní API s konkrétní konvence volání:

```cpp
// class widget {
//   widget();
//   ~widget();
//   double method( int, gadget& );
// };
extern "C" {        // functions using explicit "this"
   struct widget;   // opaque type (forward declaration only)
   widget* STDCALL widget_create();      // constructor creates new "this"
   void STDCALL widget_destroy(widget*); // destructor consumes "this"
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"
}
```

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)