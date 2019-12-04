---
title: Chyba kompilátoru C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: 436fb112758dfdec9997ff7e6dd7ef8f9dcdc66e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761774"
---
# <a name="compiler-error-c3163"></a>Chyba kompilátoru C3163

' CONSTRUCT ': atributy nejsou konzistentní s předchozí deklarací

Atributy, které jsou aplikovány na definici v konfliktu s atributy, které jsou aplikovány na deklaraci.

Jedním ze způsobů, jak vyřešit C3163, je eliminace atributů u dopředné deklarace. Všechny atributy v dopředných deklaracích by měly být menší než atributy v definici nebo, nejvíce rovny.

Možnou příčinou chyby C3163 je, že se jedná o jazyk Microsoft zdrojového kódu poznámek (SAL). Makra SAL se nerozšiřují, pokud projekt nezkompilujete pomocí příznaku **/analyze** . Program, který se zkompiluje čistě bez/analyze, může vyvolat C3163, pokud se pokusíte ho znovu zkompilovat s možností/Analyze. Další informace o SAL najdete v tématu [poznámky SAL](../../c-runtime-library/sal-annotations.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3163.

```cpp
// C3163.cpp
// compile with: /clr /c
using namespace System;

[CLSCompliant(true)] void f();
[CLSCompliant(false)] void f() {}   // C3163
// try the following line instead
// [CLSCompliant(true)] void f() {}
```

## <a name="see-also"></a>Viz také:

[Poznámky SAL](../../c-runtime-library/sal-annotations.md)
