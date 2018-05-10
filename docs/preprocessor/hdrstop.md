---
title: hdrstop – | Microsoft Docs
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
ms.openlocfilehash: f1c628efaf45be87dcfc046cf1774c762c157f4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="hdrstop"></a>hdrstop
Poskytuje větší kontrolu nad názvy souborů předkompilace a nad umístěním, ve kterém je uložen stav kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma hdrstop [( "filename" )]    
```  
  
## <a name="remarks"></a>Poznámky  
 *Filename* je název předkompilovaný hlavičkový soubor použít nebo vytvořit (v závislosti na tom, jestli se [/Yu](../build/reference/yu-use-precompiled-header-file.md) nebo [/Yc](../build/reference/yc-create-precompiled-header-file.md) je zadána). Pokud *filename* neobsahuje specifikaci cesta předkompilovaný hlavičkový soubor předpokládá se, že ve stejném adresáři jako zdrojový soubor.  
  
 Pokud obsahuje soubor jazyka C nebo C++ **hdrstop –** – Direktiva pragma, když kompilujete s /Yc, kompilátor uloží stav kompilace až umístění – Direktiva pragma. Zkompilovaný stav jakéhokoli kódu, který následuje direktivu pragma, není uložen.  
  
 Použití *filename* pro pojmenování předkompilovaný hlavičkový soubor, ve kterém je uložen kompilované stav. Mezery mezi **hdrstop –** a *filename* je volitelný. Název souboru zadaný v **hdrstop –** – Direktiva pragma je řetězec a proto podléhá omezení libovolný řetězec jazyka C nebo C++. Zejména je nutné jej uzavřít do uvozovek a použít řídicí znak (zpětné lomítko) pro zadání názvů adresářů. Příklad:  
  
```  
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )  
```  
  
 Název předkompilovaného souboru hlaviček se určuje podle následujících pravidel, v pořadí podle priority:  
  
1.  Argument možnosti kompilátoru /Fp  
  
2.  *Filename* argument #**hdrstop – Direktiva pragma**  
  
3.  Základní název zdrojového souboru s příponou .PCH  
  
 Pro /Yc a /Yu možnosti, pokud žádná z možností dvě kompilace ani **hdrstop –** – Direktiva pragma Určuje název souboru, základní název zdrojového souboru se používá jako základní název předkompilovaný hlavičkový soubor.  
  
 Lze také použít příkazy předzpracování pro provedení nahrazení makra následovně:  
  
```  
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"  
#define PCH_FNAME "PROG.PCH"  
.  
.  
.  
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )  
```  
  
 Kde platí následující pravidla **hdrstop –** – Direktiva pragma se může:  
  
-   Musí být uvedena mimo jakékoliv deklarace dat, funkce nebo definice.  
  
-   Musí být zadána ve zdrojovém souboru, nikoli v souboru hlaviček.  
  
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
  
 V tomto příkladu **hdrstop –** – Direktiva pragma se zobrazí po dva soubory byly zahrnuty a byla definována vložené funkce. To se může zpočátku zdát, jako neobvyklé umístění direktivy pragma. Zvažte ale, že pomocí ruční možnosti předkompilace, /Yc a /Yu, **hdrstop –** – Direktiva pragma umožňuje předkompilovat celý zdrojové soubory – dokonce i vloženého kódu. Kompilátor společnosti Microsoft předkompilaci neomezuje pouze na deklarace dat.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)