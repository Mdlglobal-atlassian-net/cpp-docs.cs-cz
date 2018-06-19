---
title: Kompilátoru (úroveň 1) upozornění C4138 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0865935c30c4934684c7a12e50ab26f3e8b12c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277030"
---
# <a name="compiler-warning-level-1-c4138"></a>C4138 kompilátoru upozornění (úroveň 1)
' * /' nalezen mimo komentář  
  
 Komentář ukončovací oddělovač, který není před otevírání komentář oddělovač. Kompilátor předpokládá mezeru mezi hvězdičku (**\***) a lomítkem (/).  
  
## <a name="example"></a>Příklad  
  
```  
// C4138a.cpp  
// compile with: /W1  
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning  
int main()  
{  
}  
```  
  
 Toto upozornění může být způsobeno pokusu vnořit komentáře.  
  
 Toto upozornění může být vyřešen, pokud jste komentář části kódu, které obsahují komentáře, uzavřete kód v **#if / #endif** blokovat a nastavit řízení výrazu na hodnotu nula:  
  
```  
// C4138b.cpp  
// compile with: /W1  
#if 0  
int my_variable;   /* Declaration currently not needed */  
#endif  
int main()  
{  
}  
```