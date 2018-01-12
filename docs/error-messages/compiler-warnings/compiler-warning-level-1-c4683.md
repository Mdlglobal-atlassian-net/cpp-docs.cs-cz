---
title: "Kompilátoru (úroveň 1) upozornění C4683 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4683
dev_langs: C++
helpviewer_keywords: C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0a8ca498a3c95a1b37229f6ac973cf74a8e28ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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