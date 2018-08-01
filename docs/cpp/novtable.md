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
ms.openlocfilehash: 5deee0209866580afd038fbce068a9275f5b5874
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406965"
---
# <a name="novtable"></a>novtable
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Jedná se **__declspec** rozšířeného atributu.  
  
 Tato forma **__declspec** lze použít pro všechny deklarace tříd, ale bude použito pouze na rozhraní třídy, tedy třídy, které se nikde nebude vytvořena instance samostatně. **__Declspec** zastaví kompilátoru generování kódu inicializace konstruktoru vfptr a destruktoru třídy. V mnoha případech jsou tímto odebrány odkazy na tabulku vtable, které jsou přidruženy ke třídě a budou tedy odebrány linkerem. Použití této formy atributu **__declspec** může vést k významnému snížení velikosti kódu.  
  
 Při pokusu o vytvoření instance třídy označené **novtable** a poté přístup člena třídy, zobrazí se narušení přístupu (AV).  
  
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
  
## <a name="see-also"></a>Viz také:  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)