---
title: Chyba kompilátoru C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 1dc9781bc0cf1bc6c7f879cc3971828983471c6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757745"
---
# <a name="compiler-error-c2071"></a>Chyba kompilátoru C2071

' identifier ': Neplatná třída úložiště

`identifier` byla deklarována s neplatnou [třídou úložiště](../../c-language/c-storage-classes.md). Tato chyba může být způsobena tím, že pro identifikátor je zadána více než jedna třída úložiště nebo když definice není kompatibilní s deklarací třídy úložiště.

Chcete-li tento problém vyřešit, pochopení zamýšlené třídy úložiště identifikátoru, například `static` nebo `extern`– a opravte deklaraci, která se má shodovat.

## <a name="example"></a>Příklad

Následující ukázka generuje C2071.

```cpp
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C2071.

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
