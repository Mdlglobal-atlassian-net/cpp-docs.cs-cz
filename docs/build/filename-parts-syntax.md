---
title: Syntaxe částí názvu souboru
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
ms.openlocfilehash: 159558081fd9884f969ddc66833d927b8569a79b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417473"
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

[Příkazy v souboru pravidel](../build/commands-in-a-makefile.md)
