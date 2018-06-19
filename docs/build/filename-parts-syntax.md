---
title: Syntaxe částí názvu souboru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d807087be171a2ad63ed37a8b359c3200c812040
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367482"
---
# <a name="filename-parts-syntax"></a>Syntaxe částí názvu souboru
Syntaxe částí názvu souboru v příkazech představuje součástí první závislé název souboru (který může být předpokládané závislé). Název souboru součásti jsou jednotky v souboru, cesta, základní název a příponu jako zadaný, není, protože existuje na disku. Použití **%s** představují úplný název souboru. Použití **%&#124;**[*částí*]**F** (svislá čára znak následuje symbol procenta) představují částí názvu souboru, kde *částí*může být nula nebo více z následujících písmen v libovolném pořadí.  
  
|Písmeno|Popis|  
|------------|-----------------|  
|Žádné písmeno|Úplný název (stejné jako **%s**)|  
|**d**|Jednotka|  
|**p**|Cesta|  
|**f**|Základní název souboru|  
|**e**|Přípona souboru|  
  
 Například, pokud je název souboru c:\prog.exe:  
  
-   %s bude c:\prog.exe  
  
-   %&#124;F bude c:\prog.exe  
  
-   %&#124;dF bude c  
  
-   %&#124;pF bude c:\  
  
-   %&#124;fF bude programové  
  
-   %&#124;eF bude exe  
  
## <a name="see-also"></a>Viz také  
 [Příkazy v souboru pravidel](../build/commands-in-a-makefile.md)