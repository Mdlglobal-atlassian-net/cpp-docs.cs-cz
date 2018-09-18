---
title: Upozornění (úroveň 3) C4800 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5a19c27731192a5fe2930aec3e78fb66d790484
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090903"
---
# <a name="compiler-warning-level-3-c4800"></a>Kompilátor upozornění (úroveň 3) C4800

> "*typ*': vynucení hodnota logická hodnota"true"nebo"Nepravda"(upozornění ohledně výkonu)

Toto upozornění se vygeneruje, když hodnota, která není `bool` přiřazený nebo převést na typ `bool`. Obvykle se tato zpráva způsoben přirazením `int` proměnné `bool` proměnné kde `int` proměnná obsahuje pouze hodnoty **true** a **false**a může být znova deklarovat jako typ `bool`. Pokud nelze přepsat výraz, který má použít typ `bool`, potom můžete přidat "`!=0`" na výraz, který poskytuje typ výrazu `bool`. Přetypování na typ výrazu `bool` nezakáže upozornění, která je záměrné.

Toto upozornění je generováno již v sadě Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje C4800 a ukazuje, jak ho opravit:

```cpp
// C4800.cpp
// compile with: /W3
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```