---
title: Chyba kompilátoru C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: c358553a36104b5c389076f5a5ce02f94f85e85a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667308"
---
# <a name="compiler-error-c2593"></a>Chyba kompilátoru C2593

'operator identifier' je nejednoznačný

Pro přetíženého operátoru je definován více než jeden operátor je to možné.

Tato chyba může být stanovena při použití explicitní přetypování na jeden nebo více skutečných parametrů.

Následující ukázka generuje C2593:

```
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

Tuto chybu může způsobovat serializace typu s plovoucí desetinnou čárkou proměnné pomocí `CArchive` objektu. Kompilátor identifikuje `<<` operátor jako nejednoznačný. C++ pouze primitivní typy, které `CArchive` může serializovat typy pevné velikosti `BYTE`, `WORD`, `DWORD`, a `LONG`. Všechny typy celého čísla musí být přetypovat na některý z těchto typů pro serializaci. Typy s plovoucí desetinnou čárkou musí být archivovat pomocí `CArchive::Write()` členskou funkci.

Následující příklad ukazuje, jak archivovat do proměnné s plovoucí desetinnou čárkou (`f`) do archivní úrovně `ar`:

```
ar.Write(&f, sizeof( float ));
```