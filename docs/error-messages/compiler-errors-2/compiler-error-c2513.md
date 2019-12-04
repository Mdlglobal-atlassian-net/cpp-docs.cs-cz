---
title: Chyba kompilátoru C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 093a5856fdcfa6311fcef93214672b035c91b4fc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746523"
---
# <a name="compiler-error-c2513"></a>Chyba kompilátoru C2513

' type ': není deklarována žádná proměnná před znakem ' = '

V deklaraci bez identifikátoru proměnné se zobrazí specifikátor typu.

Následující ukázka generuje C2513:

```cpp
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Tato chyba se může vygenerovat taky v důsledku práce s podmnožinou shody s kompilátorem pro Visual Studio .NET 2003: inicializace typedef už není povolená. Inicializace typedef není povolená standardem a teď generuje chybu kompilátoru.

```cpp
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Alternativou je odstranění `typedef` k definování proměnné se seznamem agregačních inicializátorů, ale to se nedoporučuje, protože vytvoří proměnnou se stejným názvem jako typ a skryje název typu.
