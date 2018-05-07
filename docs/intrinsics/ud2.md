---
title: __ud2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ud2
dev_langs:
- C++
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c282456f74fa86940e3d1ffc77d0226a28ed0b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ud2"></a>__ud2
**Konkrétní Microsoft**  
  
 Generuje nedefinované instrukce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __ud2();  
```  
  
## <a name="remarks"></a>Poznámky  
 Procesor vyvolá výjimku neplatný kód operace, je-li provést nedefinované instrukci.  
  
 `__ud2` Funkce je ekvivalentní volání `UD2` počítač instrukce a je k dispozici pouze v režimu jádra. Další informace naleznete v dokumentu "vyvíjející Software Intel architektura ruční svazku 2: odkaz na sadu instrukce," v [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__ud2`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="example"></a>Příklad  
 Následující příklad spustí nedefinované instrukce, které vyvolá výjimku. Obslužná rutina výjimky poté změní návratový kód od nuly do jednoho.  
  
```  
// __ud2_intrinsic.cpp  
#include <stdio.h>  
#include <intrin.h>  
#include <excpt.h>  
// compile with /EHa  
  
int main() {  
  
// Initialize the return code to 0.  
 int ret = 0;  
  
// Attempt to execute an undefined instruction.  
  printf("Before __ud2(). Return code = %d.\n", ret);  
  __try {   
  __ud2();   
  }  
  
// Catch any exceptions and set the return code to 1.  
  __except(EXCEPTION_EXECUTE_HANDLER){  
  printf("  In the exception handler.\n");  
  ret = 1;  
  }  
  
// Report the value of the return code.   
  printf("After __ud2().  Return code = %d.\n", ret);  
  return ret;  
}  
```  
  
```Output  
Before __ud2(). Return code = 0.  
  In the exception handler.  
After __ud2().  Return code = 1.  
```  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)