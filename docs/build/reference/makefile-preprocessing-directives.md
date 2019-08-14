---
title: Předběžné zpracování direktiv souboru pravidel
ms.date: 08/11/2019
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 4825ca180cb1b419a9ffa5232575ba1a24f8805d
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980513"
---
# <a name="makefile-preprocessing-directives"></a>Předběžné zpracování direktiv souboru pravidel

Direktivy předběžného zpracování nerozlišují velká a malá písmena. Počáteční vykřičník (!) musí být na začátku řádku. Za vykřičníkem se může zobrazit nula nebo více mezer nebo karet pro odsazení.

- `!CMDSWITCHES`{`+` &#124; } možnost... `-`

   Zapíná nebo vypíná jednotlivé *Možnosti* . Mezery nebo tabulátory se musí vyskytovat `+` před `-` operátorem OR; žádná se může vyskytovat mezi operátorem a [písmeny možností](running-nmake.md#nmake-options). U písmen nejsou rozlišována velká a malá písmena a jsou zadána`/`bez lomítka (). Pokud chcete zapnout některé možnosti a vypnout jiné, použijte samostatné specifikace `!CMDSWITCHES`.

   V souboru pravidel se dá použít jenom/D,/I,/N a/S. V souboru Tools. ini jsou povoleny všechny možnosti s výjimkou/F,/HELP,/NOLOGO,/X a/?. Změny zadané v rámci bloku Description se projeví až po bloku Next Description. Tato direktiva aktualizuje **MAKEFLAGS**; změny jsou zděděny během rekurze, pokud je zadán parametr **MAKEFLAGS** .

- `!ERROR`*text*

   Zobrazí *text* ve U1050 Error a pak zablokuje NMAKE, i když se používá modifikátor `.IGNORE`příkazu `!CMDSWITCHES`/k,/i,,`-`nebo pomlčka (). Mezery nebo tabulátory před *textem* budou ignorovány.

- `!MESSAGE`*text*

   Zobrazí *text* do standardního výstupu. Mezery nebo tabulátory před *textem* budou ignorovány.

- `!INCLUDE`[ `<` ] *filename* [ `>` ]

   Přečte *soubor filename* jako soubor pravidel a pak pokračuje s aktuálním souborem pravidel. NMAKE vyhledává *název souboru* nejprve v zadaném nebo aktuálním adresáři a pak rekurzivně prostřednictvím adresářů všech nadřazených souborů pravidel a potom, pokud je *název souboru* uzavřený pomocí lomených`< >`závorek (), v adresářích určených  **Přidejte** makro, které je zpočátku nastaveno na proměnnou prostředí include. Užitečné pro předání `.SUFFIXES` nastavení, `.PRECIOUS`a odvození pravidel do rekurzivních souborů pravidel.

- `!IF`*constant_expression*

   Příkazy procesů mezi `!IF` a Next `!ELSE` nebo `!ENDIF` IF *constant_expression* se vyhodnotí jako nenulová hodnota.

- `!IFDEF`*název_makra*

   Zpracuje příkazy mezi `!IFDEF` a další `!ELSE` nebo `!ENDIF` , pokud je definován *název_makra* . Je považováno za definováno makro s hodnotou null.

- `!IFNDEF`*název_makra*

   Zpracovává příkazy `!IFNDEF` a další `!ELSE` nebo `!ENDIF` , pokud není definován parametr *název_makra* .

- `!ELSE`[`IF` &#124; &#124; constant_expression makro`IFDEF` ] `IFNDEF`

   Zpracuje příkazy mezi `!ELSE` a další `!ENDIF` , pokud je předchozí `!IF`příkaz `!IFDEF`, nebo `!IFNDEF` , vyhodnocen jako nula. Volitelná klíčová slova poskytují další kontrolu před předzpracováním.

- `!ELSEIF`

   Synonyma pro `!ELSE IF`.

- `!ELSEIFDEF`

   Synonyma pro `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Synonyma pro `!ELSE IFNDEF`.

- `!ENDIF`

   Označuje konec `!IF`bloku, `!IFDEF`nebo `!IFNDEF` . Jakýkoli text, `!ENDIF` který následuje po na stejném řádku, se ignoruje.

- `!UNDEF`*název_makra*

   Zruší definici *makra*.

## <a name="see-also"></a>Viz také:

- [Předběžné zpracování souboru pravidel](makefile-preprocessing.md)