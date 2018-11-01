---
title: Syntaxe částí názvu souboru
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
ms.openlocfilehash: 89869ccaea2a9a5c3d16762fe49b72efc462e0ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552045"
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