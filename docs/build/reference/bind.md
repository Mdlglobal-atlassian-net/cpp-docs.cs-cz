---
title: -BIND | Dokumentace Microsoftu
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
ms.openlocfilehash: a47004ce41d6bae3d91a81c4a61a712bc31dfbdb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725891"
---
# <a name="bind"></a>/BIND

```
/BIND[:PATH=path]
```

## <a name="remarks"></a>Poznámky

Tato možnost nastaví adresy ze vstupních bodů v tabulky importních adres pro spustitelný soubor nebo knihovny DLL. Tuto možnost použijte, zkrátit čas načtení programu.

Určete spustitelný soubor a knihovny DLL v programu *soubory* argumentů na příkazový řádek EDITBIN. Volitelný *cesta* argument/BIND Určuje umístění knihovny DLL používané zadané soubory. Několik adresářů oddělujte středníkem (**;**). Pokud *cesta* není zadaný, hledá EDITBIN adresáře určené v proměnné prostředí PATH. Pokud *cesta* určena EDITBIN ignoruje proměnné PATH.

Ve výchozím nastavení nastaví zavaděč program adresy vstupní body při načtení programu. Množství času, které tento proces trvá se liší v závislosti na řadě knihoven DLL a počet vstupních bodů odkazovat v programu. Pokud program byl upraven, s/BIND a základní adresy pro spustitelný soubor a jeho knihoven DLL nejsou v konfliktu s knihovny DLL, které jsou již načtena, není nutné nastavovat tyto adresy operačního systému. V situaci, kdy jsou soubory správně založené operační systém přemístí knihovny DLL programu a přepočítá adresy vstupního bodu, který přidá do okamžiku načtení programu.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](../../build/reference/editbin-options.md)