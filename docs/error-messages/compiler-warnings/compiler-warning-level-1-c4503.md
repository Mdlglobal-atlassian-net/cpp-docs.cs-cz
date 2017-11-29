---
title: "Kompilátoru (úroveň 1) upozornění C4503 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4503
dev_langs: C++
helpviewer_keywords: C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b174ac92abb0f095895eb587afcba860f4abbe0d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4503"></a>Kompilátoru (úroveň 1) upozornění C4503
"identifikátor": dekorované délka názvu překročení název byl zkrácen.  
  
 Upravený název byl delší než omezení kompilátoru (4096) a byla zkrácena. Zabráníte tak toto upozornění a zkrácení, snižte počet argumentů nebo délka názvu identifikátorů použít.  
  
 Jeden situaci, kdy se objeví toto upozornění je když váš kód obsahuje šablony specializuje na šablony opakovaně.  Například mapa mapy (ze standardní knihovna C++).  V takovém případě můžete nastavit vaše definice TypeDef typu (například struktura), který obsahuje mapy.  
  
 Může se však rozhodnout není změny struktury kódu.  Je možné dodávat aplikaci, která generuje C4503, ale pokud dojde k chybám čas odkaz na zkrácený symbol, bude obtížné určit typ symbolu v chybě.  Ladění bude také obtížnější; ladicí program bude mít i vyskytnout potíže mapování názvu symbolu k zadání názvu.  Správnost programu, je však nemá vliv na zkrácený název.  
  
 Následující ukázka generuje C4503:  
  
```  
// C4503.cpp  
// compile with: /W1 /EHsc /c  
// C4503 expected  
#include <string>  
#include <map>  
  
class Field{};  
  
typedef std::map<std::string, Field> Screen;  
typedef std::map<std::string, Screen> WebApp;  
typedef std::map<std::string, WebApp> WebAppTest;  
typedef std::map<std::string, WebAppTest> Hello;  
Hello MyWAT;  
```  
  
 Následující příklad ukazuje jeden ze způsobů přepište kód vyřešit C4503:  
  
```  
// C4503b.cpp  
// compile with: /W1 /EHsc /c  
#include <string>  
#include <map>  
  
class Field{};  
struct Screen2 {  
   std::map<std::string, Field> Element;  
};  
  
struct WebApp2 {  
   std::map<std::string, Screen2> Element;  
};  
  
struct WebAppTest2 {  
   std::map<std::string, WebApp2> Element;  
};  
  
struct Hello2 {  
   std::map<std::string, WebAppTest2> Element;  
};  
  
Hello2 MyWAT2;  
```