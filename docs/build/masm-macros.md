---
title: MASM – makra
ms.date: 11/04/2016
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
ms.openlocfilehash: 8a00852a3a763aae5fda34d7e0fde664997a0bdb
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328822"
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