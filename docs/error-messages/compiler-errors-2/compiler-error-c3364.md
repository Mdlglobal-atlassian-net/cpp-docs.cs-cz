---
title: Chyba kompilátoru C3364
ms.date: 11/04/2016
f1_keywords:
- C3364
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
ms.openlocfilehash: e99ab3919edcfb883701c08c52cd7aad60cd4591
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498784"
---
# <a name="compiler-error-c3364"></a>Chyba kompilátoru C3364

'delegování': konstruktor delegate: argument musí být ukazatel na členskou funkci třídy spravované nebo globální funkce

Druhý parametr konstruktoru delegáta přebírá adresu členské funkce nebo adresu statické členské funkce libovolné třídy. Obě jsou považovány za jednoduché adresy.

Následující ukázka generuje C3364:

```
// C3364_2.cpp
// compile with: /clr

delegate int D( int, int );

ref class C {
public:
   int mf( int, int ) {
      return 1;
   }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364

   // try the following line instead
   // System::Delegate^ pD = gcnew D(pC, &C::mf);
}
```
