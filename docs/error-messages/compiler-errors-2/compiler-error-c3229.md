---
title: Chyba kompilátoru C3229
ms.date: 11/04/2016
f1_keywords:
- C3229
helpviewer_keywords:
- C3229
ms.assetid: f2d90923-aa8b-444f-ab10-1f37dbb864e1
ms.openlocfilehash: a3716bafd92bbcd5875ab2ba317f0c6826289c59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543881"
---
# <a name="compiler-error-c3229"></a>Chyba kompilátoru C3229

'type': indirekce parametru obecného typu nejsou povoleny.

Nemůže používat obecné parametry s `*`, `^`, nebo `&`.

## <a name="example"></a>Příklad

Následující ukázka generuje C3229.

```
// C3229.cpp
// compile with: /clr /c
generic <class T>
ref class C {
   T^ t;   // C3229
};

// OK
generic <class T>
ref class D {
   T u;
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3229.

```
// C3229_b.cpp
// compile with: /clr /c
generic <class T>   // OK
ref class Utils {
   static void sort(T elems[], size_t size);   // C3229
   static void sort2(T elems, size_t size);   // OK
};
```