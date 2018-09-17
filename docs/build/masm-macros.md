---
title: MASM – makra | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb436acae117c78bfa5c752b905bd3f4f910e9da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707847"
---
# <a name="masm-macros"></a>MASM – makra

Pro zjednodušení používání [Pseudooperace nezpracovaná](../build/raw-pseudo-operations.md), je sada makra, definovaná v ksamd64.inc, která slouží k vytvoření prologů typický postup a epilogů.

## <a name="remarks"></a>Poznámky

|– Makro|Popis|
|-----------|-----------------|
|alloc_stack(n)|Přiděluje blok zásobníku (pomocí sub rsp, n) n bajtů a vydává příslušné unwind informace (.allocstack n)|
|save_reg reg, umístění|Uloží reg stálé registru do zásobníku na posunu loc RSP a generuje příslušné informace unwind. (.savereg reg umístění)|
|push_reg registru|Vložení reg stálé registru do zásobníku a generuje příslušné informace unwind. (.pushreg registru)|
|rex_push_reg registru|Uložení stálé registru do zásobníku pomocí operace push 2 bajtů a vydává příslušné unwind informace (.pushreg reg) by měl ten použije, pokud je první instrukci ve funkci tak, aby byl funkci horká-opravitelnou za provozu.|
|save_xmm128 reg, umístění|Uloží stálého registru XMM registru do zásobníku na posunu loc RSP a generuje příslušné unwind informace (.savexmm128 reg, umístění)|
|Posun set_frame registru|Nastaví registr reg rámce na RSP + posun (pomocí mov nebo lea) a generuje příslušné unwind informace (.set_frame reg, posunu)|
|push_eflags|Vkládá eflags s instrukcí pushfq a generuje příslušné unwind informace (.alloc_stack 8)|

Tady je ukázkový prolog funkce s správné použití makra:

```asm
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