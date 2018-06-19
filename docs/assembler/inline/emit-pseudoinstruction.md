---
title: _emit – pseudoinstrukce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- _emit
dev_langs:
- C++
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ad75f4abf2e86cb08ba646e50e9390650993d05
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050695"
---
# <a name="emit-pseudoinstruction"></a>_emit – pseudoinstrukce
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 **_Emit** – pseudoinstrukce definuje jeden bajt do aktuálního umístění v aktuálním segmentu text. **_Emit** – pseudoinstrukce vypadá takto: [DB](../../assembler/masm/db.md) direktivu MASM.  
  
 Následující fragment bajtů 0x4A 0x43 a 0x4B umístí do kódu:  
  
```  
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B  
 .  
 .  
 .  
__asm {  
     randasm  
     }  
```  
  
> [!CAUTION]
>  Pokud `_emit` generuje pokyny, registry, upravit a zkompilujete aplikace s optimalizace, kompilátor nemůže zjistit, jaké zaregistruje se vztahuje. Například pokud `_emit` generuje instrukci, která upraví **rax** registrace, kompilátor nebude vědět, který **rax** došlo ke změně. Kompilátor může proveďte nesprávný předpokládá o hodnotě v tom, že registrace po provedení vloženého assembleru kódu. Aplikace v důsledku toho může vykazovat nepředvídatelné chování, když je spuštěna.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)