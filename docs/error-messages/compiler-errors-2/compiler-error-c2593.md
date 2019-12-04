---
title: Chyba kompilátoru C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 2a385e35376ddce528678980705595bfb98aca95
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759344"
---
# <a name="compiler-error-c2593"></a>Chyba kompilátoru C2593

' identifikátor operátora ' je dvojznačný

Pro přetížený operátor je definován více než jeden možný operátor.

Tato chyba se může opravit, pokud použijete explicitní přetypování na jeden nebo více skutečných parametrů.

Následující ukázka generuje C2593:

```cpp
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

Tato chyba může být způsobena serializací proměnné s plovoucí desetinnou čárkou pomocí objektu `CArchive`. Kompilátor identifikuje operátor `<<` jako dvojznačný. Jedinými primitivními C++ typy, které `CArchive` mohou serializovat, jsou typy pevné velikosti `BYTE`, `WORD`, `DWORD`a `LONG`. Všechny celočíselné typy musí být přetypování na jeden z těchto typů pro serializaci. Typy s plovoucí desetinnou čárkou musí být archivovány pomocí členské funkce `CArchive::Write()`.

Následující příklad ukazuje, jak archivovat proměnnou s plovoucí desetinnou čárkou (`f`) pro archivní `ar`:

```
ar.Write(&f, sizeof( float ));
```
