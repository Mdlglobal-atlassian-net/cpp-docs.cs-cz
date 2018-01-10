---
title: "Upozornění (úroveň 3) kompilátoru C4800 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4800
dev_langs: C++
helpviewer_keywords: C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 687b0dab996bfbfe2ce30d65b86196383c02b914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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