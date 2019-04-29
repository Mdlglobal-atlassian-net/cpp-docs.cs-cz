---
title: Chyba kompilátoru C3896
ms.date: 11/04/2016
f1_keywords:
- C3896
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
ms.openlocfilehash: 00e103720dc666b17566b67da19d4e908bb3addd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385521"
---
# <a name="compiler-error-c3896"></a>Chyba kompilátoru C3896

'member': nesprávný inicializátor: Tento datový člen literálu se dá inicializovat jenom s "nullptr"

A [literálu](../../extensions/literal-cpp-component-extensions.md) datový člen byl inicializován nesprávně.  Zobrazit [nullptr](../../extensions/nullptr-cpp-component-extensions.md) Další informace.

Následující ukázka generuje C3896:

```
// C3896.cpp
// compile with: /clr /c
ref class R{};

value class V {
   literal R ^ r = "test";   // C3896
   literal R ^ r2 = nullptr;   // OK
};
```