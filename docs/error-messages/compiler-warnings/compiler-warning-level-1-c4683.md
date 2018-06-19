---
title: Kompilátoru (úroveň 1) upozornění C4683 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 418bf25d565c616d5bc4aaf58361c4f28df298ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285340"
---
# <a name="compiler-warning-level-1-c4683"></a>C4683 kompilátoru upozornění (úroveň 1)
**'**   
 ***funkce* ': 'out' má zdroj události-parametr; cvičení opatrní při zapojování více obslužných rutin událostí**  
  
 Pokud více než jeden jímek událostí naslouchá ke zdroji událostí modelu COM, může být ignorován hodnotu parametr typu out.  
  
 Uvědomte si, že nevrácené paměti dojde v následujících situacích:  
  
1.  Pokud metoda má výstupní parametr, který je interně přiděleno, například BSTR *.  
  
2.  Pokud má více než jeden obslužné rutiny události (je vícesměrového vysílání události)  
  
 Z důvodu nevracení je výstupní parametr bude možné nastavit více než jeden obslužnou rutinou, že vrácený do lokality volání pouze poslední obslužná rutina.  
  
 Následující ukázka generuje C4683:  
  
```  
// C4683.cpp  
// compile with: /W1 /LD  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[ module(name="xx") ];  
  
[ object ]  
__interface I {  
   HRESULT f([out] int* pi);  
   // try the following line instead  
   // HRESULT f(int* pi);  
};  
  
[ coclass, event_source(com) ]  
struct E {  
   __event __interface I;   // C4683  
};  
```