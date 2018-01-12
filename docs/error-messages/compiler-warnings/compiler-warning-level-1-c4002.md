---
title: "Kompilátoru (úroveň 1) upozornění C4002 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4002
dev_langs: C++
helpviewer_keywords: C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c11b40f29ccbd0e58afdce08463a87dc71181d6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4002"></a>C4002 kompilátoru upozornění (úroveň 1)
příliš mnoho parametrů skutečné makro identifikátoru  
  
 Počet aktuálních parametrů v makro překračuje počet formální parametry v definici makra. Preprocesor – shromažďuje další parametry ale ignoruje je během rozšiřování makro.  
  
 C4002 může dojít, když nesprávně pomocí [Variadická makra](../../preprocessor/variadic-macros.md).  
  
 Následující ukázka generuje C4002:  
  
```  
// C4002.cpp  
// compile with: /W1  
#define test(a) (a)  
  
int main() {  
   int a = 1;  
   int b = 2;  
   a = test(a,b);   // C4002  
   // try..  
   a = test(a);  
}  
```  
  
 Tato chyba může být také vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual Studio .NET 2003: navíc čárkami v makro už přijata.  
  
 Kompilátor nebude přijímat další čárkami v makru. Pro kód platný v sadě Visual Studio .NET 2003 a sady Visual Studio .NET verzí aplikace Visual C++ odeberte navíc čárkami.  
  
```  
// C4002b.cpp  
// compile with: /W1  
#define F(x,y)  
int main()  
{  
   F(2,,,,,,3,,,,,,)   // C4002  
   // Try the following line instead:  
   // F(2,3)  
}  
```