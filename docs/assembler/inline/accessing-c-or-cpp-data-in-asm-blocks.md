---
title: "Přístup k datům C++ v blocích __asm nebo C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f981944958f55c4a66828dba2b2fdad5f1718d07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>Přístup k datům jazyka C nebo C++ v blocích __asm
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Skvělé vloženého sestavení je schopnost odkazují na proměnné jazyka C nebo C++ podle názvu. `__asm` Bloku se může vztahovat na všechny symboly, včetně názvy proměnných, které jsou v oboru, kde se zobrazí bloku. Například pokud proměnnou C `var` nachází v oboru, pokyn  
  
```  
__asm mov eax, var  
```  
  
 ukládá hodnotu identifikátoru `var` v EAX.  
  
 Pokud je třída, struktura nebo členů sjednocení má jedinečný název, `__asm` bloku najdete pomocí pouze název člena bez zadání proměnnou nebo `typedef` název před doby (**.**) operátor. Pokud není jedinečný název člena, ale musíte umístit do proměnné nebo `typedef` názvem bezprostředně před období operátor. Například typy struktur ve sdílené složce následující ukázka `same_name` jako jejich název člena:.  
  
 Pokud deklarujte proměnné s typy  
  
```  
struct first_type hal;  
struct second_type oat;  
```  
  
 všechny odkazy na člen `same_name` musí použijte název proměnné, protože `same_name` není jedinečný. Ale člen `weasel` má jedinečný název, takže je možné odkazovat na ni pomocí jenom jeho název člena:  
  
```  
// InlineAssembler_Accessing_C_asm_Blocks.cpp  
// processor: x86  
#include <stdio.h>  
struct first_type  
{  
   char *weasel;  
   int same_name;  
};  
  
struct second_type  
{  
   int wonton;  
   long same_name;  
};  
  
int main()  
{  
   struct first_type hal;  
   struct second_type oat;  
  
   __asm  
   {  
      lea ebx, hal  
      mov ecx, [ebx]hal.same_name ; Must use 'hal'  
      mov esi, [ebx].weasel       ; Can omit 'hal'  
   }  
   return 0;  
}  
```  
  
 Všimněte si, že vynechání název proměnné je jenom pro kódování vaše pohodlí. Stejné pokyny sestavení jsou generovány, zda se nachází název proměnné.  
  
 Datové členy v jazyce C++ bez ohledu na omezení přístupu můžete přistupovat. Člena ale nemůžete volat funkce.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)