---
title: Upozornění (úroveň 4) C4232 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4232
dev_langs:
- C++
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 450c764cfc130acf28e3edfb40fcd17c8ac3b664
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118281"
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