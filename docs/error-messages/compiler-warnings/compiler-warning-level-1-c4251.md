---
title: "Kompilátoru (úroveň 1) upozornění C4251 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b220913d97755547a9cb35fe326f9fb9a06e40a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4251"></a>C4251 kompilátoru upozornění (úroveň 1)
"identifikátor": Třída typu type, musí mít dll rozhraní používat klienti třídy 'type2'.  
  
 Aby se minimalizovala možnost poškození dat při exportu tříd se [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), ujistěte se, že:  
  
-   Všechny statických dat je přístup přes funkce, které byly exportovány z knihovny DLL.  
  
-   Žádné vložená metody vaší třídy můžete upravit statických dat.  
  
-   Žádné vložená metody vaší třídy použijte funkcí CRT nebo jiné funkce knihovny použijte statických dat (viz [potenciální chyby předávání CRT objekty přes hranice knihovny DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) informace).  
  
-   Žádné metody vaší třídy (bez ohledu na vložené) můžete použít typy, kde instance v EXE a soubor DLL mají statických dat rozdíly.  
  
 Export tříd, které knihovny DLL, která definuje třídu s virtuální funkce a funkce, které můžete volat k vytvoření instance definováním a odstranit objekty typu se můžete vyhnout.  Potom můžete stačí zavolat virtuální funkce na typu.  
  
 Další informace o exportování šablony naleznete v tématu [http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 C4251 můžete ignorovat, pokud jsou odvozování z typu v standardní knihovna C++ kompilování ladicí verze (**/MTd**) a kde se chybová zpráva kompilátoru odkazuje na _Container_base.  
  
```  
// C4251.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251  
```