---
title: "Syntaxe částí názvu souboru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: be9a3cf9c91fecedd596ae7db74158f376ffc00c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="filename-parts-syntax"></a>Syntaxe částí názvu souboru
Syntaxe částí názvu souboru v příkazech představuje součástí první závislé název souboru (který může být předpokládané závislé). Název souboru součásti jsou jednotky v souboru, cesta, základní název a příponu jako zadaný, není, protože existuje na disku. Použití **%s** představují úplný název souboru. Použití **% &#124;** [*částí*]**F** (svislá čára znak následuje symbol procenta) představují částí názvu souboru, kde *částí* může být nula nebo více z následujících písmen v libovolném pořadí.  
  
|Písmeno|Popis|  
|------------|-----------------|  
|Žádné písmeno|Úplný název (stejné jako **%s**)|  
|**d**|Jednotka|  
|**p**|Cesta|  
|**f**|Základní název souboru|  
|**e**|Přípona souboru|  
  
 Například, pokud je název souboru c:\prog.exe:  
  
-   %s bude c:\prog.exe  
  
-   % &#124; F bude c:\prog.exe  
  
-   % &#124; dF bude c  
  
-   % &#124; pF bude c:\  
  
-   % &#124; fF bude programové  
  
-   % &#124; eF bude exe  
  
## <a name="see-also"></a>Viz také  
 [Příkazy v souboru pravidel](../build/commands-in-a-makefile.md)