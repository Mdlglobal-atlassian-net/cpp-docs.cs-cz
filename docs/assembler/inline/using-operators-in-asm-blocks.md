---
title: "Používání operátorů v blocích __asm | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ca8ac739793c81ef18f8657cbf53c9cb018b3e38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-operators-in-asm-blocks"></a>Používání operátorů v blocích __asm
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 `__asm` Bloku nelze použít konkrétní operátory jazyka C nebo C++, jako  **<<**  operátor. Ale operátory sdílí C a MASM, například \* operátor, se interpretují jako operátory jazyka sestavení. Například mimo `__asm` blok hranaté závorky (**[]**) se interpretují jako uzavření dolní indexy pole, které C automaticky přizpůsobí velikost element v poli. Uvnitř `__asm` bloku, jsou považovány za MASM operátoru indexu, která dává posun bez měřítka bajtů v jakémkoli datový objekt nebo popisek (nikoli pouze pole). Následující kód ukazuje rozdíl:  
  
```  
int array[10];  
  
__asm mov array[6], bx ;  Store BX at array+6 (not scaled)  
  
array[6] = 0;         /* Store 0 at array+24 (scaled) */  
```  
  
 První odkaz na `array` není škálovat, ale druhý. Všimněte si, že můžete použít **typ** operátor k dosažení škálování podle konstanta. Například odpovídají následující příkazy:  
  
```  
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24  
  
array[6] = 0;                   /* Store 0 at array + 24 */  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)