---
title: Syntaxe částí názvu souboru
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
ms.openlocfilehash: d5e815dcb8a424d309362e004d1de4c039dc968b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823443"
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

- %&#124;F will be c:\prog.exe

- %&#124;dF bude c

- %&#124;pF bude c:\

- %&#124;fF bude GID

- %&#124;eF bude exe

## <a name="see-also"></a>Viz také:

[Příkazy v souboru pravidel](commands-in-a-makefile.md)
