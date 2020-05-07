---
title: Definice a konvence
ms.date: 11/04/2016
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
ms.openlocfilehash: 0ff3f8b447e29f0da59405a7c0286d7a696b4613
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234429"
---
# <a name="definitions-and-conventions"></a>Definice a konvence

Terminály jsou koncové body v definici syntaxe. Žádné jiné řešení není možné. Terminály obsahují sadu vyhrazených slov a uživatelské identifikátory.

Neterminály jsou zástupné symboly v syntaxi a jsou definovány jinde v tomto souhrnu syntaxe. Definice mohou být rekurzivní.

Volitelná součást je označena jako volitelná. <sub>opt</sub> Například:

> **{** *Expression*<sub>opt</sub> **}**

označuje volitelný výraz uzavřený do složených závorek.

Konvence syntaxe používá jiné atributy písma pro různé součásti syntaxe. Symboly a písma jsou následující:

|Atribut|Popis|
|---------------|-----------------|
|*neterminálu*|Kurzíva označuje neterminály.|
|**const**|Terminály tučného typu jsou slova a symboly vyhrazená literály, které je nutné zadat tak, jak je znázorněno. Znaky v tomto kontextu vždy rozlišují velká a malá písmena.|
|<sub>opt</sub>|Neterminály následované <sub>výslovným souhlasem</sub> jsou vždycky volitelné.|
|výchozí písmo|Znaky v sadě popsané nebo uvedené v tomto řezu písma lze použít jako terminály v příkazech jazyka C.|

Dvojtečka (**:**) po neterminálu zavádí svou definici. Alternativní definice jsou uvedeny na samostatných řádcích, s výjimkou případů, kdy jsou uvozeny slovy "One z".

## <a name="see-also"></a>Viz také

[Souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md)
