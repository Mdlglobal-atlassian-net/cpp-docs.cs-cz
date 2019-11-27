---
title: Upozornění kompilátoru (úroveň 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: b55594608eccc5d1e5e764bffb73ecb3787af1e4
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541586"
---
# <a name="compiler-warning-level-4-c4130"></a>Upozornění kompilátoru (úroveň 4) C4130

' operator ': Logická operace na adrese řetězcové konstanty

Použití operátoru s adresou řetězcového literálu vytvoří neočekávaný kód.

Následující ukázka generuje C4130:

```cpp
// C4130.cpp
// compile with: /W4
int main()
{
   char *pc;
   pc = "Hello";
   if (pc == "Hello") // C4130
   {
   }
}
```

Příkaz **if** porovnává hodnotu uloženou v ukazateli `pc` na adresu řetězce "Hello", který je přidělen samostatně při každém výskytu řetězce v kódu. Příkaz **if** neporovnávání řetězce, na který odkazuje, `pc` s řetězcem "Hello".

Chcete-li porovnat řetězce, použijte funkci `strcmp`.