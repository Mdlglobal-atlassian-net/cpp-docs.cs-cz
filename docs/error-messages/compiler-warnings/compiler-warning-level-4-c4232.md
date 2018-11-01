---
title: Kompilátor upozornění (úroveň 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: dee087b73bf032a68daf0527ea584efcc7579361
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552630"
---
# <a name="compiler-warning-level-4-c4232"></a>Kompilátor upozornění (úroveň 4) C4232

používá se nestandardní rozšíření: 'identifier': adresa DllImport "dllimport" není statická, identita není zaručená.

Pod rozšíření společnosti Microsoft (/Ze), můžete poskytnout nestatické hodnotu jako adresu funkce deklarovat **dllimport** modifikátor. V části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), to způsobí chybu.

Následující ukázka generuje C4232:

```
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```