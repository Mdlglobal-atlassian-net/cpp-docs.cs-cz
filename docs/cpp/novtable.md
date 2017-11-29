---
title: novtable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: novtable_cpp
dev_langs: C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8c2873410747b740af870ddb32e1d8989c77e60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="novtable"></a>novtable
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Jedná se o rozšířený atribut `__declspec`.  
  
 Tuto formu atributu `__declspec` lze použit pro všechny deklarace tříd, ale měla by být použita pouze na třídy rozhraní, z nichž nikde nebude vytvořena instance samostatně. Atribut `__declspec` ukončí generování kódu kompilátoru za účelem inicializace konstruktoru vfptr a destruktoru třídy. V mnoha případech jsou tímto odebrány odkazy na tabulku vtable, které jsou přidruženy ke třídě a budou tedy odebrány linkerem. Použití této formy atributu `__declspec` může vést k významnému snížení velikosti kódu.  
  
 Při pokusu o vytvoření instance třídy označené jako `novtable` a následném přístupu k členu třídy obdržíte zprávu o narušení přístupu (AV).  
  
## <a name="example"></a>Příklad  
  
```  
// novtable.cpp  
#include <stdio.h>  
  
struct __declspec(novtable) X {  
   virtual void mf();  
};  
  
struct Y : public X {  
   void mf() {  
      printf_s("In Y\n");  
   }  
};  
  
int main() {  
   // X *pX = new X();  
   // pX->mf();   // Causes a runtime access violation.  
  
   Y *pY = new Y();  
   pY->mf();  
}  
```  
  
```Output  
In Y  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)