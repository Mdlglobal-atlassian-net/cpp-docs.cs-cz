---
title: Chyba kompilátoru C2492 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fcb9058bf1aac584e8b7728616f821bda4b33f6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096272"
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