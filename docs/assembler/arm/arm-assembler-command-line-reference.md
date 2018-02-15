---
title: "Reference k příkazovému řádku assembleru ARM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb6b395ec8f47e820cb3184c0d88b4c91e712eb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="arm-assembler-command-line-reference"></a>Referenční dokumentace pro použití nástroje assembleru ARM v příkazovém řádku
Tento článek obsahuje informace o assembleru Microsoft ARM, příkazového řádku *armasm*, který kompilovaný jazyk sestavení ARMv7 jezdec do implementace Microsoft z běžné objekt souboru formátu (COFF). Linkeru můžete propojit COFF kód s kódem objekt, který je vytvořen pomocí assembleru ARM nebo kompilátorem C, společně s objekt knihovny, které jsou vytvořené pomocí librarian.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
armasm [[options]] sourcefile objectfile  
```  
  
```  
armasm [[options]] -o objectfile sourcefile  
```  
  
#### <a name="parameters"></a>Parametry  
 `options`  
 – chyby `filename`  
 Přesměrování chybové zprávy a upozornění na `filename`.  
  
 -i `dir[;dir]`  
 Cesta hledání zahrnout přidáte zadaných adresářích.  
  
 -předdefinovat `directive`  
 Zadejte direktivu SETA, SETL nebo NASTAVÍ předdefinovat symbol. Příklad: **armasm.exe-předdefinovat "Počet SETA 150" source.asm**. Další informace najdete v tématu [příručka nástroje assembleru ARM](http://go.microsoft.com/fwlink/p/?linkid=246102).  
  
 -nowarn  
 Zakažte všechny zprávy upozornění.  
  
 -Ignorovat `warning`  
 Zakážete zadaný upozornění. Možné hodnoty najdete v části o upozornění.  
  
 – Nápověda  
 Tisk zpráv Nápověda příkazového řádku.  
  
 -počítač `machine`  
 Zadejte typ počítače, který má nastaveny v hlavičce PE.  Možné hodnoty `machine` jsou:  
**ARM**– nastaví typ počítač IMAGE_FILE_MACHINE_ARMNT. Toto nastavení je výchozí.   
**JEZDEC**– nastaví typ počítač IMAGE_FILE_MACHINE_THUMB.  
  
 -oldit  
 Generovat stylu ARMv7 IT bloky.  Ve výchozím nastavení jsou kompatibilní s ARMv8 IT bloky se generují.  
  
 -prostřednictvím `filename`  
 Přečtěte si další argumenty příkazového řádku z `filename`.  
  
 -16  
 Sestavte zdroj jako pokyny jezdec 16 bitů.  Toto nastavení je výchozí.  
  
 -32  
 Sestavte zdroj jako 32bitový ARM pokyny.  
  
 -g  
 Generovat ladicí informace.  
  
 -errorReport: `option`  
 Zadejte jak interní assembleru vznikly chyby společnosti Microsoft.  Možné hodnoty `option` jsou:   
**žádný**– Neodesílat sestavy.   
**řádku**– vyzvat uživatele k zprávy odesílat hned.   
**fronty**– vyzvat uživatele k odeslání zpráv při dalším přihlášení správce. Toto nastavení je výchozí.   
**Odeslat**– odesílání sestav automaticky.  
  
 `sourcefile`  
 Název zdrojového souboru.  
  
 `objectfile`  
 Název souboru objektu (výstup).  
  
 Následující příklad ukazuje, jak používat armasm v Typický scénář. Nejprve pomocí armasm sestavení souboru jazyk sestavení zdroje (.asm) do souboru objektu (.obj). Pak používat kompilátoru CL příkazového řádku jazyka C pro kompilaci souboru zdroje (.c) a také zadat linkeru možnost propojit soubor objektu ARM.  
  
 **armasm myasmcode.asm -o myasmcode.obj**  
  
 **cl myccode.c /link myasmcode.obj**  
  
## <a name="see-also"></a>Viz také  
 [Diagnostické zprávy assembleru ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)   
 [Direktivy assembleru ARM](../../assembler/arm/arm-assembler-directives.md)