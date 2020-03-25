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
ms.openlocfilehash: 1dd30c8e338343626d8a8cc3157d118e44f0ea18
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170485"
---
# <a name="makefile-preprocessing-directives"></a>Předběžné zpracování direktiv souboru pravidel

Direktivy předběžného zpracování nerozlišují velká a malá písmena. Počáteční vykřičník (!) musí být na začátku řádku. Za vykřičníkem se může zobrazit nula nebo více mezer nebo karet pro odsazení.

- `!CMDSWITCHES` {`+` &#124; `-`}*možnost* ...

   Zapíná nebo vypíná jednotlivé *Možnosti* . Mezery nebo karty se musí vyskytovat před `+` nebo operátorem `-`; mezi operátorem a [písmeny možností](running-nmake.md#nmake-options)se nic nemůže vyskytovat. U písmen nejsou rozlišována velká a malá písmena a jsou zadána bez lomítka (`/`). Pokud chcete zapnout některé možnosti a vypnout jiné, použijte samostatné specifikace `!CMDSWITCHES`.

   V souboru pravidel se dá použít jenom/D,/I,/N a/S. V souboru Tools. ini jsou povoleny všechny možnosti s výjimkou/F,/HELP,/NOLOGO,/X a/?. Změny zadané v rámci bloku Description se projeví až po bloku Next Description. Tato direktiva aktualizuje **MAKEFLAGS**; změny jsou zděděny během rekurze, pokud je zadán parametr **MAKEFLAGS** .

- `!ERROR` *text*

   Zobrazí *text* ve U1050 Error a pak zablokuje NMAKE, i když se používá modifikátor příkazu/K,/i, `.IGNORE`, `!CMDSWITCHES`nebo pomlčka (`-`). Mezery nebo tabulátory před *textem* budou ignorovány.

- `!MESSAGE` *text*

   Zobrazí *text* do standardního výstupu. Mezery nebo tabulátory před *textem* budou ignorovány.

- `!INCLUDE` [`<`] *filename* [`>`]

   Přečte *soubor filename* jako soubor pravidel a pak pokračuje s aktuálním souborem pravidel. NMAKE vyhledává *název souboru* nejprve v zadaném nebo aktuálním adresáři a pak rekurzivně prostřednictvím adresářů všech nadřazených souborů pravidel a potom, pokud je *název souboru* uzavřený pomocí lomených závorek (`< >`), v adresářích určených makrem **include** , které je zpočátku nastaveno na proměnnou prostředí include. Užitečné pro předání `.SUFFIXES` nastavení, `.PRECIOUS`a odvození pravidel do rekurzivních souborů pravidel.

- `!IF` *constant_expression*

   Zpracovává příkazy mezi `!IF` a další `!ELSE` nebo `!ENDIF`, pokud *constant_expression* vyhodnocuje na nenulovou hodnotu.

- `!IFDEF` *název_makra*

   Zpracovává příkazy mezi `!IFDEF` a další `!ELSE` nebo `!ENDIF`, pokud je zadán parametr *název_makra* . Je považováno za definováno makro s hodnotou null.

- `!IFNDEF` *název_makra*

   Zpracovává příkazy mezi `!IFNDEF` a další `!ELSE` nebo `!ENDIF`, pokud není definován parametr *název_makra* .

- `!ELSE` [`IF` *constant_expression* &#124; `IFDEF` *název_makra* &#124; `IFNDEF` *název_makra*]

   Zpracovává příkazy mezi `!ELSE` a další `!ENDIF`, pokud je příkaz předchozí `!IF`, `!IFDEF`nebo `!IFNDEF` vyhodnocen jako nula. Volitelná klíčová slova poskytují další kontrolu před předzpracováním.

- `!ELSEIF`

   Synonyma pro `!ELSE IF`.

- `!ELSEIFDEF`

   Synonyma pro `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Synonyma pro `!ELSE IFNDEF`.

- `!ENDIF`

   Označuje konec `!IF`, `!IFDEF`nebo `!IFNDEF` bloku. Jakýkoli text po `!ENDIF` na stejném řádku je ignorován.

- `!UNDEF` *název_makra*

   Zruší definici *makra*.

## <a name="see-also"></a>Viz také

- [Předběžné zpracování souboru pravidel](makefile-preprocessing.md)
