---
title: "Direktivy předběžného zpracování souboru pravidel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1bc73a86b0772b13731aaf7ac4e2ef0760caa8a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="makefile-preprocessing-directives"></a>Předběžné zpracování direktiv souboru pravidel
Direktivy předběžného zpracování se nerozlišují malá a velká písmena. Počáteční vykřičníkem (!) musí být uvedena na začátku řádku. Po vykřičník k odsazení může zobrazit nula nebo více mezery ani karty.  
  
 **! CMDSWITCHES –**  
 {**+**&#124;  **-** }*možnost*... Změní každou *možnost* uvedené zapnout nebo vypnout. Mezery nebo karty musí být před + nebo - operátor; žádné může vyskytovat mezi operátor a [možnost písmena](../build/nmake-options.md). Písmena se nerozlišují malá a jsou zadána bez lomítko (/). Chcete-li některé možnosti na a jiné vypnout, použijte samostatné specifikace z **! Cmdswitches –**.  
  
 Pouze /D / I/n a /S lze použít v souboru pravidel. V Tools.ini, jsou povoleny všechny možnosti s výjimkou /F, / help, / nologo, / X, a /?. Zadaný v bloku popis změny se projeví až další blok popis. Tato direktiva aktualizace **MAKEFLAGS**; zděděny změny během rekurze Pokud **MAKEFLAGS** je zadán.  
  
 **! Chyba***textu*   
 Zobrazí *text* v chybě nástroje U1050 pak zdržovalo NMAKE, i když /K, nebo I, **. Ignorovat**, **! Cmdswitches –**, nebo se používá modifikátor příkaz pomlčky (-). Prostory nebo karty před *text* jsou ignorovány.  
  
 **! ZPRÁVA***textu*   
 Zobrazí *text* standardním výstupu. Prostory nebo karty před *text* jsou ignorovány.  
  
 **! ZAHRNOUT**[  **\<** ] *filename*[  **>** ]  
 Přečte *filename* jako souboru pravidel, pak bude pokračovat s aktuální souboru pravidel. Vyhledá NMAKE *filename* nejprve v adresáři zadané nebo aktuální pak rekurzivně prostřednictvím adresáře všech nadřazených soubory pravidel, pak pokud *filename* je ohraničená lomené závorky (\<>), do adresáře určeného **zahrnout** makro, který původně nastavení proměnné prostředí zahrnout. Umožňuje předat **. PŘÍPONY** nastavení **. DRAHOCENNÝ**a odvozená pravidla pro soubory rekurzivní pravidel.  
  
 **! POKUD**  `constantexpression`  
 Zpracovává příkazy mezi **! Pokud** a další **! ELSE** nebo `!ENDIF` Pokud `constantexpression` vyhodnotí nenulovou hodnotu.  
  
 **! Ifdef –***makra*   
 Zpracovává příkazy mezi `!IFDEF` a další **! ELSE** nebo `!ENDIF` Pokud *makro* je definována. Makro s hodnotou null je považován za být definován.  
  
 **! Ifndef –***makra*   
 Zpracovává příkazy mezi **! Ifndef –** a další **! ELSE** nebo `!ENDIF` Pokud *makro* není definován.  
  
 **! ELSE**[**Pokud** *constantexpression* &#124; **Ifdef –** *makro*&#124; **Ifndef –** *makro*]  
 Zpracovává příkazy mezi **! ELSE** a další `!ENDIF` Pokud předchozího **! Pokud**, `!IFDEF`, nebo **! Ifndef –** příkaz vyhodnotit na hodnotu nula. Volitelné klíčová slova poskytnout další kontrolu nad předběžného zpracování.  
  
 **! ELSEIF –**  
 Synonymum pro **! Pokud jiný**.  
  
 **! ELSEIFDEF –**  
 Synonymum pro **! Ifdef – ELSE**.  
  
 **! ELSEIFNDEF –**  
 Synonymum pro **! Ifndef – ELSE**.  
  
 `!ENDIF`  
 Označuje konec **! Pokud**, `!IFDEF`, nebo **! Ifndef –** bloku. Jakýkoli text po `!ENDIF` na stejném řádku je ignorováno.  
  
 **! UNDEF***makra*   
 Undefines *makro*.  
  
## <a name="see-also"></a>Viz také  
 [Předběžné zpracování souboru pravidel](../build/makefile-preprocessing.md)