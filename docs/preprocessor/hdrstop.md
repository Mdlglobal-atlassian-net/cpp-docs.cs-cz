---
title: hdrstop – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: f540f0f01fe654213af15afa8fbf5cbd94e4b7e2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221018"
---
# <a name="hdrstop-pragma"></a>hdrstop – direktiva pragma

Poskytuje další kontrolu nad názvy souborů předkompilace a v umístění, ve kterém je stav kompilace uložen.

## <a name="syntax"></a>Syntaxe

> **#pragma hdrstop** [("*filename*")]

## <a name="remarks"></a>Poznámky

Název *souboru* je název předkompilovaného hlavičkového souboru, který se má použít nebo vytvořit (v závislosti na tom, jestli je zadaný [/Yu](../build/reference/yu-use-precompiled-header-file.md) nebo [/YC](../build/reference/yc-create-precompiled-header-file.md) ). Pokud *název souboru* neobsahuje specifikaci cesty, předpokládá se, že soubor předkompilované hlavičky je ve stejném adresáři jako zdrojový soubor.

Pokud soubor C nebo C++ obsahuje direktivu pragma **hdrstop** při kompilování `/Yc`s, kompilátor uloží stav kompilace až do umístění direktivy pragma. Zkompilovaný stav jakéhokoli kódu, který následuje po direktivě pragma, není uložen.

Použijte *filename* pro pojmenování souboru předkompilované hlavičky, ve kterém je uložen kompilovaný stav. Mezera mezi **hdrstop** a *filename* je nepovinná. Název souboru zadaný v direktivě pragma **hdrstop** je řetězec, a proto podléhá omezením řetězce C nebo C++ . Zejména je nutné jej uzavřít do uvozovek a použít řídicí znak (zpětné lomítko) pro zadání názvů adresářů. Příklad:

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

Název předkompilovaného souboru hlaviček se určuje podle následujících pravidel, v pořadí podle priority:

1. Argument pro `/Fp` možnost kompilátoru

2. Argument *filename* pro`#pragma hdrstop`

3. Základní název zdrojového souboru s příponou .PCH

Pro možnosti `/Yu` a, pokud žádná ze dvou možností kompilace ani direktiva pragma hdrstop neurčuje název souboru, použije se základní název zdrojového souboru jako základní název souboru předkompilované hlavičky. `/Yc`

Lze také použít příkazy předzpracování pro provedení nahrazení makra následovně:

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

Následující pravidla určují, kde lze umístit direktivu pragma **hdrstop** :

- Musí být uvedena mimo jakékoliv deklarace dat, funkce nebo definice.

- Musí být zadána ve zdrojovém souboru, nikoli v souboru hlaviček.

## <a name="example"></a>Příklad

```C
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    // ...                           // Some code to display string
}
#pragma hdrstop
```

V tomto příkladu se direktiva pragma **hdrstop** zobrazí po zahrnutí dvou souborů a definování vložené funkce. Toto umístění může zpočátku vypadat jako liché umístění direktivy pragma. Vezměte ale v úvahu, že použití možností `/Yc` ručního předkompilace a `/Yu`, s direktivou pragma **hdrstop** umožňuje předkompilovat celé zdrojové soubory – dokonce i vložený kód. Kompilátor společnosti Microsoft předkompilaci neomezuje pouze na deklarace dat.

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
