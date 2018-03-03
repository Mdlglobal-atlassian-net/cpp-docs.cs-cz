---
title: "Použití a zachování registrů ve vloženém sestavení | Microsoft Docs"
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
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 66805c6e9331f55beb01b13a536596c53e35049c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Použití a zachování registrů v sestavení inline assemblerem
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Obecně platí, můžete nesmí předpokládá, že do registru se dané hodnoty při `__asm` začne bloku. Registrace hodnoty nemusí být zachována napříč samostatné `__asm` bloky. Pokud ukončit blok kódu vloženého a vytvoříte další, nelze spoléhat na registruje v druhé bloku na původní hodnoty z prvního bloku. `__asm` Bloku dědí, ať zaregistrovat výsledek hodnoty z normálního toku řízení.  
  
 Pokud použijete `__fastcall` konvence volání do kompilátoru předá argumenty funkce v registrech místo v zásobníku. To může způsobit problémy s funkcí s `__asm` blokuje, protože funkce nemá možnost nijak zjistit, které parametr v které registrace. Pokud funkce se stane k odběru parametr EAX a okamžitě ukládá něco jiného v EAX, dojde ke ztrátě původního parametr. Kromě toho musí zachovat ECX registrace v jakékoli funkce deklarovat s `__fastcall`.  
  
 Aby nedocházelo ke konfliktům takové registrace, nepoužívejte `__fastcall` názvů pro funkce, které obsahují `__asm` bloku. Pokud zadáte `__fastcall` konvence globálně s možností kompilátoru GR deklarovat všechny funkce obsahující `__asm` blokovat s `__cdecl` nebo `__stdcall`. ( `__cdecl` Atribut říká kompilátoru používat konvence volání jazyka C pro tuto funkci.) Pokud nejsou kompilujete s GR, vyhněte se deklarace funkce se `__fastcall` atribut.  
  
 Při použití `__asm` zapisovat jazyk sestavení v funkcí jazyka C/C++, nemusíte zachovat EAX, EBX, ECX, EDX, ESI nebo EDI Registry. Například v POWER2. Příklad C v [zápis funkcí s vloženým sestavením](../../assembler/inline/writing-functions-with-inline-assembly.md), `power2` funkce nepodporuje zachovat hodnotu v registru EAX. Však pomocí těchto registrů ovlivní kvality kódu protože allocator registrace nelze použít k ukládání hodnot v rámci `__asm` bloky. Kromě toho pomocí EBX, ESI nebo EDI v kódu vnořeného sestavení vynutíte kompilátoru k uložení a obnovení těchto registrů v funkce prologu a epilogu.  
  
 Ostatní registry používáte (například DS, SS, SP, BP a zaregistruje se příznaky) by měl zachovat rozsahu `__asm` bloku. Zaregistruje ESP a EBP musí zachovat, pokud máte z nějakého důvodu je změnit (třeba přepínače zásobníky,). Viz také [optimalizace vloženého sestavení](../../assembler/inline/optimizing-inline-assembly.md).  
  
 Některé typy SSE vyžadují osm bajtů zásobníku zarovnání vynucení kompilátoru pro generování kódu dynamické zásobníku zarovnání. Abyste mohli získat přístup k místní proměnné a parametry funkce po zarovnání, kompilátor udržuje dva ukazatele na rámec.  Pokud kompilátor provádí vynechání ukazatele rámce (FPO), použije EBP a ESP.  Pokud kompilátor neprovede FPO, použije EBX a EBP. Aby se zajistilo kód běží správně, neměňte EBX v kódu asm Pokud funkce vyžaduje dynamické zásobníku zarovnání, jak se může změnit ukazatel na rámec. Přesuňte zarovnaný typy osm bajtů mimo funkci, nebo nepoužívejte EBX.  
  
> [!NOTE]
>  Pokud se váš kód vnořeného sestavení změní příznak směru podle pokynů – STD nebo CLD, je nutné obnovit příznak na původní hodnotu.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vkládaný assembler](../../assembler/inline/inline-assembler.md)