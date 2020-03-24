---
title: Upozornění kompilátoru (úroveň 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: c0e79dfa4564960a5660f0932b142b436370ac05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173917"
---
# <a name="compiler-warning-level-4-c4232"></a>Upozornění kompilátoru (úroveň 4) C4232

používá se nestandardní rozšíření: ' identifier ': adresa dllimport ' dllimport ' není statická, identita není zaručena.

V části rozšíření společnosti Microsoft (/ze) můžete poskytnout nestatickou hodnotu jako adresu funkce deklarované pomocí modifikátoru **dllimport** . V části Kompatibilita s ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) dojde k chybě.

Následující ukázka generuje C4232:

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```
