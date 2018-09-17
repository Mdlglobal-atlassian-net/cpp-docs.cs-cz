---
title: Syntaxe částí názvu souboru | Dokumentace Microsoftu
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
ms.openlocfilehash: 5bf7a9685face739059c4b947a5796cc0a28950a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703167"
---
# <a name="filename-parts-syntax"></a>Syntaxe částí názvu souboru

Syntaxe částí názvu souboru v příkazech představuje komponenty první závislý název souboru (který může být implicitní závislé). Název souboru komponenty jsou jednotky, cesty, základním názvem a rozšíření, jak je uvedeno, v souboru nejsou, protože existuje na disku. Použití **%s** představovat úplný název souboru. Použití **%&#124;**[*částí*]**F** (svislá čára znak následuje symbol procenta) představující částí názvu souboru, kde *částí*může být nula nebo více z následujících písmen v libovolném pořadí.

|Písmeno|Popis|
|------------|-----------------|
|Žádné písmeno|Úplný název (stejné jako **%s**)|
|**d**|Jednotky|
|**p**|Cesta|
|**f**|Základní název souboru|
|**e**|Přípona souboru|

Například, pokud je název souboru c:\prog.exe:

- %s se c:\prog.exe

- %&#124;F bude c:\prog.exe

- %&#124;dF bude c

- %&#124;pF bude c:\

- %&#124;fF bude GID

- %&#124;eF bude exe

## <a name="see-also"></a>Viz také

[Příkazy v souboru pravidel](../build/commands-in-a-makefile.md)