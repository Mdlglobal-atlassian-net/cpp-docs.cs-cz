---
title: Upozornění (úroveň 3) kompilátoru C4800 | Microsoft Docs
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
ms.openlocfilehash: ed4b14ae2f3af3218909d6cd4609f1f45d3d7cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4800"></a>Upozornění (úroveň 3) kompilátoru C4800  
  
> '*typ*': vynucení hodnoty bool: true, nebo "Nepravda" (upozornění výkonu)  
  
Toto upozornění se vygeneruje, když hodnota, není `bool` přiřazený nebo převést na typ `bool`. Obvykle je způsobena tuto zprávu přiřazení `int` proměnné, které chcete `bool` proměnné kde `int` proměnná obsahuje pouze hodnoty **true** a **false**a může být znovu deklarována jako typ `bool`. Pokud nelze přepište výraz, který chcete použít typ `bool`, potom můžete přidat "`!=0`" výrazu, což dává typ výrazu `bool`. Přetypování na typ výrazu `bool` nezakáže upozornění, která je záměrné.  
  
Toto upozornění je generováno už ve Visual Studio 2017.  
  
## <a name="example"></a>Příklad
  
 Následující ukázka generuje C4800 a ukazuje, jak to opravit:  
  
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