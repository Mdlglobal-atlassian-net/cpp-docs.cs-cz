---
title: Použití a zachování registrů ve vloženém sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60506f53eb1933e5acbb03318edada82a8904386
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677015"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Použití a zachování registrů v sestavení inline assemblerem

**Specifické pro Microsoft**

Obecně platí, by neměla předpokládají, že registru bude mít předané hodnoty při `__asm` zahájení bloku. Hodnot registru nemají zaručenu zachovaná napříč samostatnými `__asm` bloky. Je-li ukončit blok vloženého kódu a začnete jiného, nelze spoléhat na registry v druhé bloku zachovat jejich hodnoty z prvního bloku. `__asm` Bloku dědí cokoli, co registrace hodnoty výsledek z normálního toku řízení.

Pokud používáte `__fastcall` konvence volání, kompilátor předá funkci argumenty v registrech místo v zásobníku. To může způsobit problémy s funkcí `__asm` blokuje, protože funkce nemá žádný způsob, jak zjistit, který parametr v které registru. Pokud dojde k přijímat parametr v eax VRÁTÍ funkci a okamžitě ukládá v eax VRÁTÍ jiný, dojde ke ztrátě původního parametru. Kromě toho musíte zachovat do ECX registru v jakékoli funkce deklarovaná pomocí `__fastcall`.

Aby nedocházelo ke konfliktům takové registr, nepoužívejte `__fastcall` konvence pro funkce, které obsahují `__asm` bloku. Pokud zadáte `__fastcall` globálně pomocí možnosti kompilátoru /Gr konvence deklarovat každé funkce obsahující `__asm` blokovat s `__cdecl` nebo `__stdcall`. ( `__cdecl` Atribut oznamuje kompilátoru, aby použil konvence volání jazyka C pro tuto funkci.) Pokud nejsou kompilace s GR, vyhněte se deklarování funkce s `__fastcall` atribut.

Při použití `__asm` psaní jazyka sestavení v funkcí jazyka C/C++, není nutné pro zachování registrů EAX, EBX, ECX, EDX, ESI nebo EDI. Například v POWER2. Příklad jazyka C v [zápis funkcí s vloženým sestavením](../../assembler/inline/writing-functions-with-inline-assembly.md), `power2` funkce nezachová hodnotu v registru eax. Nicméně pomocí těchto registrů bude mít vliv na kvalitu kódu protože přidělování registru nelze použít k ukládání hodnot v rámci `__asm` bloky. Kromě toho pomocí EBX a ESI, EDI ve vložený kód sestavení, můžete donutit kompilátor k uložení a obnovení těchto registrů ve funkci prologu a epilogu.

Další registry používat (například DS, SS, SP, doporučených postupů a příznaky Registry) by měl zachovat rozsahu `__asm` bloku. ESP a EBP registrů mělo zachovat, pokud máte z nějakého důvodu chcete-li změnit jejich (Chcete-li přepnout zásobníků, třeba). Viz také [optimalizace sestavení inline Assemblerem](../../assembler/inline/optimizing-inline-assembly.md).

Některé typy SSE vyžadují osm bajtů zásobníku zarovnání, vynucuje kompilátor generuje kód dynamické zásobníku zarovnání. Aby bylo možné pro přístup k místní proměnné a parametry funkce po zarovnání, kompilátor udržuje dva ukazatele na rámce.  Pokud kompilátor provádí vynechání ukazatele na rámce (FPO), použije EBP a ESP.  Pokud kompilátor neprovádí FPO, použije EBX a EBP. Aby se zajistilo kód běží správně, neprovádějte žádné změny EBX v kódu asm je-li funkci vyžaduje dynamické protokolů, jak ho změnit tak, ukazatel na rámec. Přesuňte zarovnané typy osmibajtového mimo funkci, nebo nepoužívejte EBX.

> [!NOTE]
>  Pokud se váš kód vloženého sestavení změní příznak směru, podle pokynů STD nebo CLD, je nutné obnovit příznak na původní hodnotu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>