---
title: Upozornění kompilátoru (úroveň 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 97ad076325b11329896d98367fb3ac311ec5ded9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051561"
---
# <a name="compiler-warning-level-1-c4804"></a>Upozornění kompilátoru (úroveň 1) C4804

' operation ': nebezpečné použití typu ' bool ' v operaci

Toto upozornění je určené pro použití `bool` proměnné nebo hodnoty neočekávaným způsobem. Například C4804 je vygenerována, pokud používáte operátory, jako je negativní unární operátor ( **-** ) nebo operátor doplňku (`~`). Kompilátor vyhodnotí výraz.

## <a name="example"></a>Příklad

Následující ukázka generuje C4804:

```cpp
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