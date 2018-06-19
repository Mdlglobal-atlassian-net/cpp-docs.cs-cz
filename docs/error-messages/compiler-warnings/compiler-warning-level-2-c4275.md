---
title: Kompilátoru (úroveň 2) upozornění C4275 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5d2a3cd7c4b937f8bee1b8f8e37e0619cc224ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292068"
---
# <a name="compiler-warning-level-2-c4275"></a>C4275 kompilátoru upozornění (úroveň 2)
bez – knihovny DLL rozhraní classkey "identifikátor" použitý jako základní položka pro knihovnu DLL rozhraní classkey "identifikátor"  
  
 Třídu exportovaný odvozený od třídy, který nebyl exportován.  
  
 Aby se minimalizovala možnost poškození dat při exportu tříd se [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), ujistěte se, že:  
  
-   Všechny statických dat přistupuje prostřednictvím funkce, které byly exportovány z knihovny DLL.  
  
-   Žádné vložená metody vaší třídy můžete upravit statických dat.  
  
-   Žádné vložená metody vaší třídy použijte funkcí CRT nebo jiné funkce knihovny použijte statických dat.  
  
-   Žádné funkce vložená tříd použít CRT – funkce nebo další funkce knihovny, například odkud statických dat.  
  
-   Žádné metody vaší třídy (bez ohledu na vložené) můžete použít typy, kde instance v EXE a soubor DLL mají statických dat rozdíly.  
  
 Export tříd, které knihovny DLL, která definuje třídu s virtuální funkce a funkce, které můžete volat k vytvoření instance definováním a odstranit objekty typu se můžete vyhnout.  Potom můžete stačí zavolat virtuální funkce na typu.  
  
 Další informace o exportování šablony naleznete v tématu [ http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 C4275 můžete ignorovat v jazyce Visual C++, pokud jsou odvozování z typu v standardní knihovna C++ kompilování ladicí verze (**/MTd**) a kde se chybová zpráva kompilátoru odkazuje na _Container_base.  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```