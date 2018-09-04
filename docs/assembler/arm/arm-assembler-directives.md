---
title: Direktivy assembleru ARM | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 282d8bbd55bec8053961c709eb3733a65972b187
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693110"
---
# <a name="arm-assembler-directives"></a>Direktivy assembleru ARM

Ve většině případů assembler Microsoft ARM používá assembleru ARM, která je popsána v [kompilátoru ARM armasm referenční příručka](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html). Implementace Microsoft některé direktivy sestavení se však liší od direktivy sestavení ARM. Tento článek vysvětluje rozdíly.

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implementace Microsoft direktivy sestavení ARM

`AREA`<br/>
Assembler Microsoft ARM podporuje tyto `AREA` atributy: `ALIGN`, `CODE`, `CODEALIGN`, `DATA`, `NOINIT`, `READONLY`, `READWRITE`, `THUMB`, `ARM`.

Všechny s výjimkou `THUMB` a `ARM` fungovat, jak je uvedeno v [kompilátoru ARM armasm referenční příručka](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

V assembler Microsoft ARM `THUMB` znamená, že `CODE` oddíl obsahuje kód pro Thumb a je pro výchozí `CODE` oddíly.  `ARM` Označuje, že oddíl obsahuje kód pro ARM.

`ATTR`<br/>
Není podporováno.

`CODE16`<br/>
Není podporována, protože zahrnuje pre-UAL Thumb syntaxi, což není povoleno assembler Microsoft ARM.  Použití `THUMB` direktiv místo toho spolu s syntaxe protokolování přístupu uživatele.

`COMMON`<br/>
Specifikace zarovnání pro běžné oblasti nepodporuje.

`DCDO`<br/>
Není podporováno.

`DN`, `QN`, `SN`<br/>
Specifikace typu nebo lane na register alias není podporována.

`ENTRY`<br/>
Není podporováno.

`EQU`<br/>
Specifikace typu pro definovaný symbol není podporována.

`EXPORT` a `GLOBAL`

> **EXPORT** <em>sym</em>{**[**<em>typ</em>**]**}

*Sym* je symbol, nelze exportovat.  [*typ*], je-li zadána, může být buď `[DATA]` k označení, že symbol odkazuje na data nebo `[FUNC]` k označení, že symbol odkazuje na kód.

`GLOBAL` je synonymum pro `EXPORT`.

`EXPORTAS`<br/>
Není podporováno.

`FRAME`<br/>
Není podporováno.

`FUNCTION` a `PROC`<br/>
I když syntaxe sestavení podporuje specifikaci vlastní konvence volání na postupech uvedením registrů, které jsou volající uložit a ty, které jsou volaný ukládání, assembler Microsoft ARM přijímá syntaxi ale ignoruje seznamy registru.  Informace o ladění, který je vytvořen assembler podporuje pouze výchozí konvenci volání.

`IMPORT` a `EXTERN`

> **IMPORT** *sym*{**, SLABÉ** *alias*{**, typ** *t*}}

*Sym* je název symbolu, které se mají naimportovat.

Pokud `WEAK` *alias* není zadán, znamená, že *sym* je slabý externí. Pokud je nalezena žádná definice pro něj v době spojení, pak všechny odkazy na něj svázat místo toho *alias*.

Pokud `TYPE` *t* není zadán, pak *t* Určuje, jak by měl pokusit vyřešit linker *sym*.  Tyto hodnoty pro *t* jsou možné:<br/>
1 – nebude provádět vyhledávání knihovny *symbolů*<br/>
2 – hledání knihovny pro *symbolů*<br/>
3 –*sym* je alias pro *alias* (výchozí)

`EXTERN` je synonymum pro `IMPORT`, s tím rozdílem, že *sym* je importován pouze v případě, že existují odkazy na něj v aktuálním sestavení.

`MACRO`<br/>
Použití proměnnou pro uchování stavu kódu makra není podporováno. Výchozí hodnoty pro makra, které parametry nejsou podporovány.

`NOFP`<br/>
Není podporováno.

`OPT`, `TTL`, `SUBT`<br/>
Není podporována, protože výsledkem assembler Microsoft ARM není výpisy.

`PRESERVE8`<br/>
Není podporováno.

`RELOC`<br/>
`RELOC n` může následovat pouze instrukce nebo direktivě definice data. Neexistuje žádná "anonymní symbol", který může být přemístění.

`REQUIRE`<br/>
Není podporováno.

`REQUIRE8`<br/>
Není podporováno.

`THUMBX`<br/>
Není podporováno, protože assembler Microsoft ARM nepodporuje instrukční sadu Thumb-2EE.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace pro použití nástroje assembleru ARM v příkazovém řádku](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Diagnostické zprávy assembleru ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
