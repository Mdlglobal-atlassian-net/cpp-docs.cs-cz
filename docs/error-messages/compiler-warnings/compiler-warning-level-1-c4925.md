---
title: Upozornění (úroveň 1) C4925 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4925
dev_langs:
- C++
helpviewer_keywords:
- C4925
ms.assetid: a4b206c0-016a-4f28-873a-bb8bb41bad50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62c661b4fffee6c6da17d72724d61b7df39a3268
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109441"
---
# <a name="compiler-warning-level-1-c4925"></a>Kompilátor upozornění (úroveň 1) C4925

"metoda": metodu dispinterface nejde volat ze skriptu

Skriptovací jazyky nelze vytvořit VT_BYREF v parametru, VT_BYREF může vytvářet pouze výstupní parametry.

Dalším způsobem, jak vyřešit toto upozornění Nedovolte, aby byly parametr (v definici a implementaci) typ ukazatele.

Následující ukázka generuje C4925:

```
// C4925.cpp
// compile with: /LD /W1
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[ module(name="Test")];

[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IDisp {
   [id(9)] void f([in] int*);
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002")  ]
struct CDisp : IDisp {   // C4925
   void f(int*) {}
};
```