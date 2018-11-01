---
title: Direktivy assembleru ARM
ms.date: 08/30/2018
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
ms.openlocfilehash: 9124f893b3334e0893073332c9d5f5a1388373d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592449"
---
# <a name="arm-assembler-directives"></a>Direktivy assembleru ARM

Ve většině případů assembler Microsoft ARM používá assembleru ARM, která je popsána v [kompilátoru ARM armasm referenční příručka](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html). Implementace Microsoft některé direktivy sestavení se však liší od direktivy sestavení ARM. Tento článek vysvětluje rozdíly.

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implementace Microsoft direktivy sestavení ARM

- OBLAST

   Assembler Microsoft ARM podporuje tyto `AREA` atributy: `ALIGN`, `CODE`, `CODEALIGN`, `DATA`, `NOINIT`, `READONLY`, `READWRITE`, `THUMB`, `ARM`.

   Všechny s výjimkou `THUMB` a `ARM` fungovat, jak je uvedeno v [kompilátoru ARM armasm referenční příručka](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

   V assembler Microsoft ARM `THUMB` znamená, že `CODE` oddíl obsahuje kód pro Thumb a je pro výchozí `CODE` oddíly.  `ARM` Označuje, že oddíl obsahuje kód pro ARM.

- ATTR

   Není podporováno.

- CODE16

   Není podporována, protože zahrnuje pre-UAL Thumb syntaxi, což není povoleno assembler Microsoft ARM.  Použití `THUMB` direktiv místo toho spolu s syntaxe protokolování přístupu uživatele.

- BĚŽNÉ

   Specifikace zarovnání pro běžné oblasti nepodporuje.

- DCDO

   Není podporováno.

- `DN`, `QN`, `SN`

   Specifikace typu nebo lane na register alias není podporována.

- POLOŽKA

   Není podporováno.

- EQU

   Specifikace typu pro definovaný symbol není podporována.

- `EXPORT` a `GLOBAL`

   Určuje exporty pomocí této syntaxe:

   > **EXPORT**|**globální** <em>sym</em>{**[**<em>typ</em>**]**}

   *Sym* je symbol, nelze exportovat.  [*typ*], je-li zadána, může být buď `[DATA]` k označení, že symbol odkazuje na data nebo `[FUNC]` k označení, že symbol odkazuje na kód. `GLOBAL` je synonymum pro `EXPORT`.

- EXPORTAS

   Není podporováno.

- RÁMCE

   Není podporováno.

- `FUNCTION` a `PROC`

   I když syntaxe sestavení podporuje specifikaci vlastní konvence volání na postupech uvedením registrů, které jsou volající uložit a ty, které jsou volaný ukládání, assembler Microsoft ARM přijímá syntaxi ale ignoruje seznamy registru.  Informace o ladění, který je vytvořen assembler podporuje pouze výchozí konvenci volání.

- `IMPORT` a `EXTERN`

   Určuje importy pomocí této syntaxe:

   > **IMPORT**|**EXTERN** *sym*{**, SLABÉ** *alias*{**, typ** *t*}}

   *Sym* je název symbolu, které se mají naimportovat.

   Pokud `WEAK` *alias* není zadán, znamená, že *sym* je slabý externí. Pokud je nalezena žádná definice pro něj v době spojení, pak všechny odkazy na něj svázat místo toho *alias*.

   Pokud `TYPE` *t* není zadán, pak *t* Určuje, jak by měl pokusit vyřešit linker *sym*.  Tyto hodnoty pro *t* jsou možné:

   |Hodnota|Popis|
   |-|-|
   |1|Neprovádějte hledání knihovny *symbolů*|
   |2|Hledání knihovny pro *symbolů*|
   |3|*Sym* je alias pro *alias* (výchozí)|

   `EXTERN` je synonymum pro `IMPORT`, s tím rozdílem, že *sym* je importován pouze v případě, že existují odkazy na něj v aktuálním sestavení.

- MACRO

   Použití proměnnou pro uchování stavu kódu makra není podporováno. Výchozí hodnoty pro makra, které parametry nejsou podporovány.

- NOFP

   Není podporováno.

- `OPT`, `TTL`, `SUBT`

   Není podporována, protože výsledkem assembler Microsoft ARM není výpisy.

- PRESERVE8

   Není podporováno.

- RELOC

   `RELOC n` může následovat pouze instrukce nebo direktivě definice data. Neexistuje žádná "anonymní symbol", který může být přemístění.

- VYŽADOVAT

   Není podporováno.

- REQUIRE8

   Není podporováno.

- THUMBX

   Není podporováno, protože assembler Microsoft ARM nepodporuje instrukční sadu Thumb-2EE.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace pro použití nástroje assembleru ARM v příkazovém řádku](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Diagnostické zprávy assembleru ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
