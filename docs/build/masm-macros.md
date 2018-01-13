---
title: "MASM – makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 043ad96ada12467ce9c2ff39c9e337e0da9d2391
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="masm-macros"></a>MASM – makra
Aby bylo možné zjednodušit použití [Pseudooperace nezpracovaná](../build/raw-pseudo-operations.md), existuje sada maker, definovaných v ksamd64.inc, která slouží k vytvoření prologů a epilogů typických procedur.  
  
## <a name="remarks"></a>Poznámky  
  
|– Makro|Popis|  
|-----------|-----------------|  
|alloc_stack(n)|Přidělení rámce zásobníku n bajtů (pomocí sub konfigurace n) a vysílá příslušné unwind informace (.allocstack – n)|  
|save_reg reg, umístění|Ukládá stálý registr reg v zásobníku na posunu loc konfigurace a vysílá příslušné unwind informace. (.savereg – reg, umístění)|  
|push_reg registru|Vkládá stálý registr reg v zásobníku a vysílá příslušné unwind informace. (.pushreg – registru)|  
|rex_push_reg registru|Uložení stálého registru do zásobníku použití nabízené 2 bajtů a vysílá příslušné unwind informace (.pushreg – reg), mělo by být použito, pokud je první pokynů ve funkci a zajistěte, aby byla funkce patchable za provozu.|  
|save_xmm128 reg, umístění|Ukládá stálý XMM registr reg v zásobníku na posunu loc konfigurace a vysílá příslušné unwind informace (.savexmm128 reg, umístění)|  
|Posun set_frame registru|Nastaví registr reg rámce být konfigurace + posun (pomocí mov nebo lea) a vysílá příslušné unwind informace (.set_frame reg, posun)|  
|push_eflags|Vkládá eflags s instrukcí pushfq a vysílá příslušné unwind informace (.alloc_stack 8)|  
  
 Tady je ukázkový prolog funkce s správné použití makra:  
  
```  
SkFrame struct   
Fill    dq ?; fill to 8 mod 16   
SavedRdi dq ?; saved register RDI   
SavedRsi dq ?; saved register RSI   
SkFrame ends  
  
sampleFrame struct  
Filldq?; fill to 8 mod 16  
SavedRdidq?; Saved Register RDI   
SavedRsi  dq?; Saved Register RSI  
sampleFrame ends  
  
sample2 PROC FRAME  
alloc_stack(sizeof sampleFrame)  
save_reg rdi, sampleFrame.SavedRdi  
save_reg rsi, sampleFrame.SavedRsi  
.end_prolog  
  
; function body  
  
mov rsi, sampleFrame.SavedRsi[rsp]  
mov rdi, sampleFrame.SavedRdi[rsp]  
  
; Here’s the official epilog  
  
add rsp, (sizeof sampleFrame)  
ret  
sample2 ENDP  
```  
  
## <a name="see-also"></a>Viz také  
 [Unwind pomocníci pro MASM](../build/unwind-helpers-for-masm.md)