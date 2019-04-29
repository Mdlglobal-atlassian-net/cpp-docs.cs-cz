---
title: Chyba kompilátoru C3278
ms.date: 11/04/2016
f1_keywords:
- C3278
helpviewer_keywords:
- C3278
ms.assetid: 56f818f5-85a6-4792-843b-54fe16327658
ms.openlocfilehash: 7618336c08dd111e495d7e4102b8e61c6e927c39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382084"
---
# <a name="compiler-error-c3278"></a>Chyba kompilátoru C3278

> Přímá volání metody interface nebo pure "*metoda*" selže v době běhu

## <a name="remarks"></a>Poznámky

Došlo k volání metody rozhraní nebo čistě metody, což není povoleno.

## <a name="example"></a>Příklad

Následující ukázka generuje C3278:

```cpp
// C3278_2.cpp
// compile with: /clr
using namespace System;
interface class I
{
   void vmf();
};

public ref class C: public I
{
public:
   void vmf()
   {
      Console::WriteLine( "In C::vmf()" );
      I::vmf(); // C3278
   }

};

int main()
{
   C^ pC = gcnew C;
   pC->vmf();
}
```