---
title: Kompilátor upozornění (úroveň 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 28b3e49717993a3bf20c8cfec5938d698266c0f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476073"
---
# <a name="compiler-warning-level-1-c4804"></a>Kompilátor upozornění (úroveň 1) C4804

'operation': potenciálně nebezpečné používání typu 'bool' v operaci

Toto upozornění je při použití `bool` proměnné nebo hodnota neočekávaným způsobem. Například C4804 se vygeneruje, pokud používáte operátorů, například záporné unární operátor (**-**) nebo doplňkovým operátorem (`~`). Kompilátor vyhodnotí výraz.

## <a name="example"></a>Příklad

Následující ukázka generuje C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```