---
title: novtable | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- novtable_cpp
dev_langs:
- C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ad0c50330d174a6139ce6e588b278e03cd99562
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947634"
---
# <a name="novtable"></a>novtable
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Jedná se **__declspec** rozšířeného atributu.  
  
 Tato forma **__declspec** lze použít pro všechny deklarace tříd, ale bude použito pouze na rozhraní třídy, tedy třídy, které se nikde nebude vytvořena instance samostatně. **__Declspec** zastaví kompilátoru generování kódu inicializace konstruktoru vfptr a destruktoru třídy. V mnoha případech jsou tímto odebrány odkazy na tabulku vtable, které jsou přidruženy ke třídě a budou tedy odebrány linkerem. Použití této formy atributu **__declspec** může vést k významnému snížení velikosti kódu.  
  
 Při pokusu o vytvoření instance třídy označené jako `novtable` a následném přístupu k členu třídy obdržíte zprávu o narušení přístupu (AV).  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)