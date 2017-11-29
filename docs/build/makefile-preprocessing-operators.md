---
title: "Operátory předzpracování souboru pravidel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d2d8aa3d428b45da81b2f9256988e089f121dd0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="makefile-preprocessing-operators"></a>Operátory předběžného zpracování souboru pravidel
Výrazy předběžné zpracování souboru pravidel můžete použít operátory, které fungují na konstantní hodnoty, ukončovacích kódů z příkazy, řetězce, makra a cesty k systému souborů. Při vyhodnocování výrazu, preprocesor nejprve rozšíří makra a pak spouští příkazy a pak provádí operace. Operace jsou vyhodnocovány v pořadí explicitní seskupení v závorkách a potom v pořadí podle priority operátorů. Výsledkem je konstantní hodnotu.  
  
 `DEFINED` Operátor je logický operátor, který funguje na název makra. Výraz `DEFINED(` *makro* `)` je hodnota true, pokud *makro* definované, i když nemá přiřazenou hodnotu. `DEFINED`v kombinaci s `!IF` nebo `!ELSE IF` je ekvivalentní `!IFDEF` nebo `!ELSE IFDEF`. Ale na rozdíl od těchto direktivy `DEFINED` mohou být používány složité výrazy.  
  
 `EXIST` Operátor je logický operátor, který funguje na cestu k systému souborů. `EXIST(`*cesta* `)` je hodnota true, pokud *cesta* existuje. Výsledek z `EXIST` lze použít v binární výrazy. Pokud *cesta* obsahuje mezery, uzavřete ji do uvozovek.  
  
 K porovnání dvou řetězců, použijte rovnosti (`==`) operátor nebo nerovnost (`!=`) operátor. Uzavřete řetězce v uvozovkách.  
  
 Konstanty typu integer, můžete použít unární operátory pro číselné negace (`-`), jeden je doplnit (`~`) a Logická negace (`!`).  
  
 Výrazy můžete použít následující operátory. Operátory stejnou přednost jsou seskupeny dohromady a skupiny jsou uvedeny v sestupném pořadí podle priority. Unární operátory přidružit operand vpravo. Binární operátory stejnou přednost přidružit operandy zleva doprava.  
  
|Operátor|Popis|  
|--------------|-----------------|  
|`DEFINED(`*makro*`)`|Vytvoří logickou hodnotu pro aktuální stav definice *makro*.|  
|`EXIST(`*cesta*`)`|Vytvoří logickou hodnotu existenci souboru v *cestu*.|  
|||  
|`!`|Unární logický operátor NOT.|  
|`~`|Unární, jednu pro doplňku.|  
|`-`|Unární negace.|  
|||  
|`*`|Násobení.|  
|`/`|Dělení.|  
|`%`|Numerického zbytku (zbývající část).|  
|||  
|`+`|Přidání.|  
|`-`|Odčítání.|  
|||  
|`<<`|Bitové posunutí doleva.|  
|`>>`|Bitové posunutí doprava.|  
|||  
|`<=`|Menší než nebo rovno.|  
|`>=`|Větší než nebo rovno.|  
|`<`|Menší než.|  
|`>`|Větší než.|  
|||  
|`==`|Rovnosti.|  
|`!=`|Nerovnosti.|  
|||  
|`&`|Bitové operace AND.|  
|`^`|Bitové operace XOR.|  
|`&#124;`|Bitový operátor OR.|  
|||  
|`&&`|Logickým operátorem a.|  
|||  
|`&#124;&#124;`|Logické OR.|  
  
> [!NOTE]
>  Bitový operátor XOR (`^`) je stejný jako řídicí znak a je nutné uvést (jako `^^`) při použití ve výrazu.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy v předběžném zpracování souboru pravidel](../build/expressions-in-makefile-preprocessing.md)