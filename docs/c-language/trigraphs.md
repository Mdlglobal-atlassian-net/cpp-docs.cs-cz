---
title: Trigraph | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ??) trigraph
- ??- trigraph
- question mark, in trigraphs
- ??= trigraph
- ?? trigraph
- ??< trigraph
- ??/ trigraph
- trigraphs
- '? symbol, trigraph'
- ??> trigraph
- ??! trigraph
- ??' trigraph
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a480a38411536266c8cd4c23f8b29190550d3444
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="trigraphs"></a>Trigraphs
Zdroj znakové sady zdrojových programů jazyka C je obsažen v 7bitové znakové sadě ASCII, ale je nadmnožinou invariantní znakové sady standardu ISO 646-1983. Sekvence trigrafů umožňuje, aby programy jazyka C byly zapsány pouze pomocí invariantní znakové sady standardu ISO (International Standards Organization). Trigrafy jsou sekvence tří znaků (uvedené dvěma po sobě jdoucími otazníky), které kompilátor nahradí jejich odpovídajícími znaky interpunkce. Trigrafy lze použít ve zdrojových souborech jazyka C, které používají znakovou sadu, která neobsahuje vhodné grafické reprezentace pro některá interpunkční znaménka.  
  
 C ++ 17 odebere trigraph od jazyka. Implementace může pokračovat v podpoře trigraph jako součást mapování definované implementací z fyzického zdrojový soubor, který *základní zdroj znakovou sadu*, ačkoli podporuje standardní implementace nepoužívat. Prostřednictvím C ++ 14 jsou podporovány trigraph jako C.  
  
 Visual C++ i nadále podporuje nahrazování trigraph, ale ve výchozím nastavení vypnutá. Informace o tom, jak povolit náhrada trigraph najdete v tématu [/Zc: trigraphs (náhrada trigraph)](../build/reference/zc-trigraphs-trigraphs-substitution.md).  
  
 Následující tabulka obsahuje devět sekvencí trigrafů. Všechny výskyty znaků interpunkce v prvním sloupci ve zdrojovém souboru jsou nahrazeny odpovídajícím znakem ve druhém sloupci.  
  
### <a name="trigraph-sequences"></a>Sekvence trigraf  
  
|Trigraf|Znak interpunkce|  
|--------------|---------------------------|  
|??=|#|  
|??(|[|  
|??/|\|  
|??)|]|  
|??'|^|  
|??\<|{|  
|??!|&#124;|  
|??>|}|  
|??-|~|  
  
 Trigraf je vždy považován za jediný zdrojový znak. Překlad trigraph probíhá v prvním [fáze překladu](../preprocessor/phases-of-translation.md), před rozpoznávání řídicí znaky v textové literály a znak konstanty. V tabulce výše je rozpoznáno pouze devět trigrafů. Všechny ostatní sekvence znaků zůstanou nepřevedeny.  
  
 Znak řídicí sekvence  **\\?**, brání špatného sekvencí trigraph jako znaků. (Informace o řídicí sekvence najdete v tématu [řídicí sekvence](../c-language/escape-sequences.md).) Například, pokud se pokusíte vypsat řetězec `What??!` pomocí tohoto příkazu `printf`  
  
```  
printf( "What??!\n" );  
```  
  
 je řetězec vytisknout `What|` protože `??!` je posloupnost trigraph, která je nahrazena `|` znak. Chcete-li tento řetězec vypsat správně, napište příkaz takto:  
  
```  
printf( "What?\?!\n" );  
```  
  
 V tomto příkazu `printf` řídicí znak zpětného lomítka před druhým otazníkem zabraňuje špatnému vyhodnocení `??!` jako trigrafu.  
  
## <a name="see-also"></a>Viz také  
 [/ Zc: trigraphs (náhrada trigraph)](../build/reference/zc-trigraphs-trigraphs-substitution.md)   
 [Identifikátory jazyka C](../c-language/c-identifiers.md)