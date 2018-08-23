---
title: hdrstop | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
dev_langs:
- C++
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10365b4cbe43863f72b721665ae8ea518e3fdc5f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465094"
---
# <a name="hdrstop"></a>hdrstop
Poskytuje větší kontrolu nad názvy souborů předkompilace a nad umístěním, ve kterém je uložen stav kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma hdrstop [( "filename" )]    
```  
  
## <a name="remarks"></a>Poznámky  
 
*Filename* je název předkompilovaného souboru hlaviček použít nebo vytvořit (podle toho, jestli [/Yu](../build/reference/yu-use-precompiled-header-file.md) nebo [/Yc](../build/reference/yc-create-precompiled-header-file.md) je zadána). Pokud *filename* neobsahuje specifikaci cesty, předpokládá se soubor předkompilované hlavičky ve stejném adresáři jako zdrojový soubor.  
  
Obsahuje-li soubor jazyka C nebo C++ **hdrstop** – Direktiva pragma při kompilaci s `/Yc`, kompilátor uloží stav kompilace do umístění direktivy pragma. Zkompilovaný stav jakéhokoli kódu, který následuje direktivu pragma, není uložen.  
  
Použití *filename* pojmenovat soubor předkompilované hlavičky, ve kterém je uložen zkompilovaný stav. Mezera mezi **hdrstop** a *filename* je volitelný. Název souboru zadaný v **hdrstop** – Direktiva pragma je řetězec a proto je v souladu s omezeními libovolný řetězec jazyka C nebo C++. Zejména je nutné jej uzavřít do uvozovek a použít řídicí znak (zpětné lomítko) pro zadání názvů adresářů. Příklad:  
  
```  
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )  
```  
  
Název předkompilovaného souboru hlaviček se určuje podle následujících pravidel, v pořadí podle priority:  
  
1. Argument `/Fp` – možnost kompilátoru  
  
2. *Filename* argument `#pragma hdrstop`  
  
3. Základní název zdrojového souboru s příponou .PCH  
  
Pro `/Yc` a `/Yu` možnosti, pokud ani jeden ze dvou možností kompilace ani **hdrstop** – Direktiva pragma Určuje název souboru, základní název zdrojového souboru se používá jako základní název předkompilovaného souboru hlaviček.  
  
Lze také použít příkazy předzpracování pro provedení nahrazení makra následovně:  
  
```  
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"  
#define PCH_FNAME "PROG.PCH"  
.  
.  
.  
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )  
```  
  
Následující pravidla určují, kde **hdrstop** – Direktiva pragma je možné použít:  
  
- Musí být uvedena mimo jakékoliv deklarace dat, funkce nebo definice.  
  
- Musí být zadána ve zdrojovém souboru, nikoli v souboru hlaviček.  
  
## <a name="example"></a>Příklad  
  
```  
#include <windows.h>                 // Include several files  
#include "myhdr.h"  
  
__inline Disp( char *szToDisplay )   // Define an inline function  
{  
    ...                              // Some code to display string  
}  
#pragma hdrstop  
```  
  
V tomto příkladu **hdrstop** – Direktiva pragma se zobrazí po dvou souborů a vložená funkce definována. To se může zpočátku zdát, jako neobvyklé umístění direktivy pragma. Zvažte však, který používá ruční předkompilace, `/Yc` a `/Yu`, se **hdrstop** – Direktiva pragma umožňuje předkompilovat celé zdrojové soubory, dokonce i vložený kód. Kompilátor společnosti Microsoft předkompilaci neomezuje pouze na deklarace dat.  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)