---
title: Chyba kompilátoru C2513 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2513
dev_langs:
- C++
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82df537e49ca17140d70977486314f43a072022d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045429"
---
# <a name="compiler-error-c2513"></a>Chyba kompilátoru C2513

'type': deklarovaná žádná proměnná před '='

Specifikátor typu se zobrazí v deklaraci s identifikátorem žádné proměnné.

Následující ukázka generuje C2513:

```
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Tato chyba může být také generovány jako důsledek kompilátoru shoda práce pro Visual Studio .NET 2003: Inicializace již není povolena definice typu. Inicializace definice typu není povolený Standard a nyní generuje chybu kompilátoru.

```
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Alternativou může být odstranění `typedef` k definování proměnné s agregační inicializátor seznamu, ale to se nedoporučuje, protože ho vytvořit proměnnou se stejným názvem jako typ, který se skrýt název typu.