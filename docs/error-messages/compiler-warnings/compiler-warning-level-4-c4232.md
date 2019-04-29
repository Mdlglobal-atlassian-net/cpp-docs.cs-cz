---
title: Kompilátor upozornění (úroveň 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: dee087b73bf032a68daf0527ea584efcc7579361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401082"
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