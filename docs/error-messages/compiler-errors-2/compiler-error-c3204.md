---
title: Chyba kompilátoru C3204
ms.date: 11/04/2016
f1_keywords:
- C3204
helpviewer_keywords:
- C3204
ms.assetid: 06e578da-0262-48c8-b2ae-be1cd6d28884
ms.openlocfilehash: 4c34ad35916f01323a72102c7099d4afd0ab17be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539292"
---
# <a name="compiler-error-c3204"></a>Chyba kompilátoru C3204

"_alloca: nejde volat z bloku catch.

K této chybě dochází, když použijete volání [_alloca](../../c-runtime-library/reference/alloca.md) z v rámci bloku catch.

## <a name="example"></a>Příklad

Následující ukázka generuje C3204:

```
// C3204.cpp
// compile with: /EHsc
#include <malloc.h>

void ShowError(void)
{
   try
   {
   }
   catch(...)
   {
      _alloca(1);   // C3204
   }
}
```