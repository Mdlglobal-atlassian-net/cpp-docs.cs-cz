---
title: Přenositelnost v hranicích ABI
description: Nashrnutá C++ rozhraní pro konvence volání jazyka C v binárních hranicích rozhraní.
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: b3b2b217739ff5900c8ef0329ff3e8909a3fe036
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303319"
---
# <a name="portability-at-abi-boundaries"></a>Přenositelnost v hranicích ABI

Používejte dostatečně přenosné typy a konvence v binárních hranicích rozhraní. "Přenosný typ" je vestavěný typ jazyka C nebo struktura, která obsahuje pouze předdefinované typy jazyka C. Typy tříd lze použít pouze v případě, že volající a volaný volaný souhlasí s rozložením, konvencí volání atd. To je možné pouze v případě, že obě jsou kompilovány se stejným kompilátorem a nastavením kompilátoru.

## <a name="how-to-flatten-a-class-for-c-portability"></a>Jak sloučit třídu pro přenositelnost C

Když mohou být volající kompilováni s jiným kompilátorem nebo jazykem, pak "sloučit" do externího rozhraní API **"C"** s konkrétní konvencí volání:

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

[Vítejte zpět naC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
