---
title: -BIND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bind
dev_langs:
- C++
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b77c778017dc78235948e8d23db136c1f63ab12d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372428"
---
# <a name="bind"></a>/BIND
```  
/BIND[:PATH=path]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento parametr nastaví adresy vstupních bodů v tabulce importovaných adres pro spustitelný soubor nebo DLL. Tuto možnost použijte ke snížení zatížení čas programu.  
  
 Určete spustitelný soubor a knihovny DLL v programu *soubory* argumentů na příkazový řádek EDITBIN. Volitelné *cesta* argument/BIND Určuje umístění knihovny DLL používané zadané soubory. Několik adresářů oddělte středníkem (**;**). Pokud *cesta* není zadán, nástroje EDITBIN v adresářích zadaný v proměnné prostředí PATH. Pokud *cesta* není zadaný, nástroje EDITBIN ignoruje proměnné PATH.  
  
 Ve výchozím nastavení program zavaděč nastavuje adresy vstupních bodů, když ho načte program. Množství času, trvá tento proces se liší v závislosti na počtu knihovny DLL a počet vstupních bodů, kterou se odkazuje v programu. Pokud program byl upraven s/BIND a základní adresy pro spustitelného souboru a jeho knihovny DLL nejsou v konfliktu s knihovny DLL, které již byly načteny, není nutné nastavovat tyto adresy operačního systému. V situaci, kde jsou nesprávně na základě souborů operační systém přemístí program knihovny DLL a přepočítá adresy vstupního bodu, který přidá do čas načítání programu.  
  
## <a name="see-also"></a>Viz také  
 [EDITBIN – možnosti](../../build/reference/editbin-options.md)