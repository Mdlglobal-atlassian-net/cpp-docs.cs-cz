---
title: Předběžné zpracování direktiv souboru pravidel
ms.date: 06/14/2018
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
ms.openlocfilehash: 0945d0e1c149b7e1ab31b0dbbd5003f8b15a1e4d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823074"
---
# <a name="makefile-preprocessing-directives"></a>Předběžné zpracování direktiv souboru pravidel

Direktivy předběžného zpracování se nerozlišují malá a velká písmena. Počáteční vykřičník (!) musí být uvedena na začátku řádku. Nula nebo více mezerami či tabulátory se mohou objevit za vykřičník pro odsazení.

- **! CMDSWITCHES** {**+** &#124; **-**}*možnost* ...

   Změní každou *možnost* uvedené zapnutí nebo vypnutí. Mezery ani tabulátory musí být uvedena před + nebo - – operátor; žádný mohou objevit mezi operátor a [možnost písmena](nmake-options.md). Písmena se nerozlišují malá a jsou zadána bez lomítka (/). Chcete-li některé možnosti na a dalších vypnout, použijte samostatné specifikace **! CMDSWITCHES**.

   Pouze /D / můžu /N a /S lze použít v souboru pravidel. V Tools.ini, jsou povoleny všechny možnosti kromě /F, / help, / nologo, / X, a /?. Zadaný v bloku popis změny se projeví až do další blok popis. Tato direktiva aktualizuje **MAKEFLAGS**; změny jsou zděděny během rekurze, pokud **MAKEFLAGS** určena.

- **! Chyba***text*

   Zobrazí *text* v chybě nástroje U1050 a zastaví NMAKE, i když /K, /, můžu **. Ignorovat**, **! CMDSWITCHES**, nebo se používá příkaz modifikátor pomlčky (-). Mezery nebo tabulátory před *text* jsou ignorovány.

- **! ZPRÁVA***text*

   Zobrazí *text* do standardního výstupu. Mezery nebo tabulátory před *text* jsou ignorovány.

- **! ZAHRNOUT** [ **\<** ] *filename* [ **>** ]

   Přečte *filename* jako souboru pravidel, pak bude pokračovat s aktuální soubor pravidel. Vyhledá v NMAKE *filename* nejprve v adresáři zadané nebo aktuální pak rekurzivně prostřednictvím libovolného adresáře nadřazených souborů pravidel, potom, pokud *filename* je uzavřen do lomených závorek (\<>), v adresářích určených **zahrnout** makro, které je zpočátku nastaven proměnná prostředí INCLUDE. Užitečné k předání **. PŘÍPONY** nastavení **. CENNÝ**a odvozená pravidla pro soubory pravidel rekurzivní.

- **! Pokud** *constant_expression*

   Zpracovává příkazy mezi **! Pokud** a dalších **! OSTATNÍ** nebo **! ENDIF** Pokud *constant_expression* vyhodnocen na nenulovou hodnotu.

- **! IFDEF***makro*

   Zpracovává příkazy mezi **! IFDEF** a dalších **! OSTATNÍ** nebo **! ENDIF** Pokud *makro* je definována. Makro s hodnotou null se považuje za definovat.

- **! IFNDEF***makro*

   Zpracovává příkazy mezi **! IFNDEF** a dalších **! OSTATNÍ** nebo **! ENDIF** Pokud *makro* není definován.

- **! OSTATNÍ** [**IF** *constant_expression* &#124; **IFDEF** *makro* &#124; **IFNDEF**  *makro*]

   Zpracovává příkazy mezi **! OSTATNÍ** a dalších **! ENDIF** Pokud předchozího **! Pokud**, **! IFDEF**, nebo **! IFNDEF** příkaz vyhodnocen na hodnotu nula. Volitelné klíčová slova poskytnout další kontrolu nad předběžného zpracování.

- **!ELSEIF**

   Synonymum pro **! ELSE IF**.

- **! ELSEIFDEF**

   Synonymum pro **! OSTATNÍ IFDEF**.

- **!ELSEIFNDEF**

   Synonymum pro **! OSTATNÍ IFNDEF**.

- **! ENDIF**

   Označuje konec **! Pokud**, **! IFDEF**, nebo **! IFNDEF** bloku. Žádný text po **! ENDIF** na stejném řádku se ignoruje.

- **! UNDEF***makro*

   Nedefinovaných hodnot *makro*.

## <a name="see-also"></a>Viz také:

- [Předběžné zpracování souboru pravidel](makefile-preprocessing.md)