---
title: Použití a zachování registrů v sestavení inline assemblerem
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 97db09ac7652c00e9599a6938f4114de080906c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318031"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Použití a zachování registrů v sestavení inline assemblerem

**Specifické pro Microsoft**

Obecně byste neměli předpokládat, že registr bude `__asm` mít danou hodnotu při zahájení bloku. Hodnoty registru není zaručeno, že `__asm` budou zachovány v samostatných blocích. Pokud ukončíte blok včleněného kódu a začnete jiný, nemůžete spoléhat na registry v druhém bloku zachovat jejich hodnoty z prvního bloku. Blok `__asm` zdědí všechny hodnoty registru vyplývající z normální tok řízení.

Pokud používáte `__fastcall` konvence volání, kompilátor předá argumenty funkce v registrech namísto v zásobníku. To může způsobit problémy ve funkcích s `__asm` bloky, protože funkce nemá žádný způsob, jak zjistit, který parametr je ve kterém registru. Pokud se stane, že funkce obdrží parametr v EAX a okamžitě uloží něco jiného v EAXu, původní parametr se ztratí. Kromě toho je nutné zachovat registr ECX `__fastcall`v jakékoli funkci deklarované s .

Chcete-li se vyhnout takové konflikty `__fastcall` registru, nepoužívejte `__asm` konvence pro funkce, které obsahují blok. Pokud zadáte `__fastcall` konvence globálně s parametrem /Gr kompilátoru, `__asm` deklarovat všechny funkce obsahující blok s `__cdecl` nebo `__stdcall`. (Atribut `__cdecl` říká kompilátoru použít konvence volání Jazyka C pro tuto funkci.) Pokud nejste kompilaci s /Gr, vyhněte `__fastcall` se deklarování funkce s atributem.

Při `__asm` použití jazyka sestavení ve funkcích C/C++ není nutné uchovávat registry EAX, EBX, ECX, EDX, ESI nebo EDI. Například v POWER2. C příklad [v zápisu funkce s inline sestavení](../../assembler/inline/writing-functions-with-inline-assembly.md), `power2` funkce nezachová hodnotu v registru EAX. Použití těchto registrů však ovlivní kvalitu kódu, protože alokátor `__asm` registru je nemůže použít k ukládání hodnot mezi bloky. Kromě toho pomocí EBX, ESI nebo EDI v kódu inline sestavení vynutíte kompilátor ukládat a obnovovat tyto registry v prologu funkce a epilogu.

Měli byste zachovat další registry, které používáte (například DS, SS, SP, `__asm` BP a příznaky registry) pro rozsah bloku. Měli byste zachovat registry ESP a EBP, pokud nemáte nějaký důvod je změnit (například pro přepínání zásobníků). Viz také [optimalizace inline sestavení](../../assembler/inline/optimizing-inline-assembly.md).

Některé typy SSE vyžadují zarovnání zásobníku o osm bajtů, což kompilátoru vynucuje dynamický kód zarovnání zásobníku. Aby měl kompilátor přístup k místním proměnným i parametrům funkce po zarovnání, zachová dva ukazatele rámce.  Pokud kompilátor provede vynechání ukazatele rámce (FPO), použije EBP a ESP.  Pokud kompilátor neprovádí FPO, použije EBX a EBP. Chcete-li zajistit, aby kód fungoval správně, neupravujte EBX v kódu asm, pokud funkce vyžaduje dynamické zarovnání zásobníku, protože by mohla změnit ukazatel rámce. Buď přesuňte osmibajtové zarovnané typy z funkce nebo se vyhněte použití EBX.

> [!NOTE]
> Pokud kód vrozené sestavení změní příznak směru pomocí pokynů STD nebo CLD, je nutné obnovit příznak na původní hodnotu.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[Inline Assembler](../../assembler/inline/inline-assembler.md)<br/>
