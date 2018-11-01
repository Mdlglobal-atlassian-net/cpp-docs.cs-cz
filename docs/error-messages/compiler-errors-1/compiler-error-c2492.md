---
title: Chyba kompilátoru C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: e2b08ef3e46681147c4efd77cbffadb096bbfc16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590456"
---
# <a name="compiler-error-c2492"></a>Chyba kompilátoru C2492

"*proměnnou*': data s dobou trvání úložiště vlákna nemůžou mít rozhraní dll

Proměnná je deklarovaná s [vlákno](../../cpp/thread.md) atribut a interface s knihovnou DLL. Adresa `thread` proměnná není znám, dokud běhu, takže ji nelze ho propojit s knihovny DLL importu nebo exportu.

Následující ukázka generuje C2492:

```
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```