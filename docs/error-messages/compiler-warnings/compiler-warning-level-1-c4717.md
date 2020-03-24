---
title: Upozornění kompilátoru (úroveň 1) C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 40897e54601793431671bc14f855db43e905c656
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175285"
---
# <a name="compiler-warning-level-1-c4717"></a>Upozornění kompilátoru (úroveň 1) C4717

' function ': rekurzivní pro všechny cesty ovládacích prvků, funkce způsobí přetečení zásobníku za běhu.

Každá cesta prostřednictvím funkce obsahuje volání funkce. Vzhledem k tomu, že neexistuje žádný způsob, jak funkci ukončit, aniž by bylo nutné nejprve volat sama sebe, funkce nebude nikdy ukončena.

Následující ukázka generuje C4717:

```cpp
// C4717.cpp
// compile with: /W1 /c
// C4717 expected
int func(int x) {
   if (x > 1)
      return func(x - 1); // recursive call
   else {
      int y = func(0) + 1; // recursive call
      return y;
   }
}

int main(){
   func(1);
}
```
