---
title: Používání operátorů v blocích __asm | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e1c7c4b8415655aff36327db9c6a9f866d82683
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="using-operators-in-asm-blocks"></a>Používání operátorů v blocích __asm
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 `__asm` Bloku nelze použít konkrétní operátory jazyka C nebo C++, jako **<<** operátor. Ale operátory sdílí C a MASM, například \* operátor, se interpretují jako operátory jazyka sestavení. Například mimo `__asm` blok hranaté závorky (**[]**) se interpretují jako uzavření dolní indexy pole, které C automaticky přizpůsobí velikost element v poli. Uvnitř `__asm` bloku, jsou považovány za MASM operátoru indexu, která dává posun bez měřítka bajtů v jakémkoli datový objekt nebo popisek (nikoli pouze pole). Následující kód ukazuje rozdíl:  
  
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