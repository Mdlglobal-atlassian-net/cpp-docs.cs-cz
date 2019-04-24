---
title: Chyba kompilátoru C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: eda3910c99f4c8ea96568f2d475c5d6a1e4cdc7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174221"
---
# <a name="compiler-error-c3163"></a>Chyba kompilátoru C3163

'vytvořit': atributy nejsou konzistentní s předchozí deklarací.

Atributy, které budou použity při definici v konfliktu s atributy, které se použijí k deklaraci.

Jedním ze způsobů řešení C3163 je eliminovat atributy u dopředné deklarace. Libovolné atributy u dopředné deklarace by měla být menší než atributy v definici nebo maximálně stejná k nim.

Možnou příčinou chyby C3163 zahrnuje jazyk Microsoft zdrojového kódu poznámky (SAL). Pokud kompilujete projekt pomocí nebudou rozbaleny SAL makra **/ analyze** příznak. Program, který se zkompiluje bez čistě / analyze může vyvolat C3163, pokud se pokusíte se ji znovu zkompilovat / analyze – možnost. Další informace o SAL naleznete v tématu [poznámky SAL](../../c-runtime-library/sal-annotations.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3163.

```
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