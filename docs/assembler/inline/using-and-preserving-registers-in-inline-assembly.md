---
title: Použití a zachování registrů v sestavení inline assemblerem
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 51147a217ec56c525fc01e1b36a9381b9356ba4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169152"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Použití a zachování registrů v sestavení inline assemblerem

**Specifické pro společnost Microsoft**

Obecně byste neměli předpokládat, že při zahájení bloku `__asm` bude mít registr zadanou hodnotu. U hodnot registru není zaručeno uchování v různých `__asm`ch blocích. Pokud zadáte blok vloženého kódu a zahájíte jiný, nemůžete spoléhat na Registry ve druhém bloku, abyste zachovali jejich hodnoty z prvního bloku. Blok `__asm` dědí jakékoli hodnoty registru z normálního toku řízení.

Použijete-li konvenci volání `__fastcall`, kompilátor předá do zásobníku argumenty funkce v registrech. To může ve funkcích pomocí `__asm`ch bloků vytvořit problémy, protože funkce nemá žádný způsob, jak určit, který parametr je v němž se nachází. Pokud se funkce stane přijmout parametr v EAX vrátí a okamžitě uloží něco jiného v EAX vrátí, původní parametr se ztratí. Kromě toho je nutné zachovávat ECX registraci v jakékoli funkci deklarované pomocí `__fastcall`.

Aby se zabránilo takovému konfliktu registru, nepoužívejte konvenci `__fastcall` pro funkce, které obsahují blok `__asm`. Pokud zadáte `__fastcall` konvenci globálně s možností kompilátoru/gr, deklarujete všechny funkce obsahující `__asm` blok `__cdecl` nebo `__stdcall`. (Atribut `__cdecl` instruuje kompilátor, aby pro tuto funkci používal konvenci volání jazyka C.) Pokud nekompilujete s/gr, vyhněte se deklaraci funkce s atributem `__fastcall`.

Při použití `__asm` k zápisu jazyka sestavení v C/C++ Functions není nutné uchovávat Registry EAX vrátí, EBX, ECX, EDX, ESI a EDI. Například v POWER2. Příklad: v [zápisu funkcí s vloženým sestavením](../../assembler/inline/writing-functions-with-inline-assembly.md)funkce `power2` nezachovává hodnotu v registru EAX vrátí. Použití těchto registrů však ovlivní kvalitu kódu, protože Alokátor registrace je nemůže použít k ukládání hodnot napříč `__asm`mi bloky. Kromě toho při použití EBX, ESI nebo EDI ve vloženém kódu sestavení vynutíte kompilátor ukládat a obnovovat tyto registry ve funkci prologu a epilogu.

Pro rozsah `__asm` bloku byste měli zachovat další používané Registry (například Registry DS, SS, SP, BP a Flags). Registry ESP a EBP byste měli zachovat, pokud nemáte nějaký důvod na jejich změnu (například na přepínání zásobníků). Viz také [optimalizace vloženého sestavení](../../assembler/inline/optimizing-inline-assembly.md).

Některé typy SSE vyžadují zarovnání zásobníku na osm bajtů, což vynutí kompilátor generovat dynamický kód pro zarovnání zásobníku. Aby bylo možné přistupovat k místním proměnným i k parametrům funkce po zarovnání, kompilátor udržuje dva ukazatele rámců.  Pokud kompilátor provádí vynechání ukazatele na rámec (rpcrt4), bude používat EBP a ESP.  Pokud kompilátor neprovede!!, použije EBX a EBP. Chcete-li zajistit, aby kód běžel správně, neměňte EBX v kódu ASM, pokud funkce vyžaduje dynamické zarovnání zásobníku, protože by mohla změnit ukazatel na rámec. Buď přesuňte typy zarovnané na osm bajtů mimo funkci, nebo nepoužívejte EBX.

> [!NOTE]
>  Pokud váš kód vloženého sestavení změní příznak Direction pomocí instrukcí STD nebo CLD, je nutné obnovit příznak na původní hodnotu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
