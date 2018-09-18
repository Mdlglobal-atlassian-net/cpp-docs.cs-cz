---
title: Chyba kompilátoru C2071 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 757110c88d3279964ab0c26f753e4d3b1f2889d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025855"
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