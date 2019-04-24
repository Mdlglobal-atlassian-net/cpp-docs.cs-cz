---
title: Chyba kompilátoru C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 95344b5ef675f566f433dfeaed9dee5c38ef77d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303344"
---
# <a name="compiler-error-c2071"></a>Chyba kompilátoru C2071

'identifier': Neplatná třída úložiště

`identifier` byl deklarován s neplatnou [třídu úložiště](../../c-language/c-storage-classes.md). Tato chyba může být způsobena, pokud je zadán více než jedna třída úložiště pro identifikátor, nebo při definici je nekompatibilní s deklarací třídy úložiště.

Chcete-li vyřešit tento problém, pochopit třídy určené úložiště identifikátoru – například `static` nebo `extern`– a opravte deklaraci tak, aby odpovídaly.

## <a name="example"></a>Příklad

Následující ukázka generuje C2071.

```
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

```
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```