---
title: Definice a konvence
ms.date: 11/04/2016
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
ms.openlocfilehash: 60806286ff8bbe64440c8b2f3e7af57b4390e2cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571441"
---
# <a name="definitions-and-conventions"></a>Definice a konvence

Terminály jsou koncové body v definici syntaxe. Žádné jiné řešení není možné. Terminály obsahují sadu vyhrazených slov a uživatelské identifikátory.

Neterminály jsou zástupné symboly v syntaxi a je definována jinde v tomto souhrnu syntaxe. Definice mohou být rekurzivní.

Volitelná součást je označena pomocí indexovaný <sub>optimalizované</sub>. Například

> **{** *výraz*<sub>optimalizované</sub> **}**

Určuje volitelný výraz uzavřený do složených závorek.

Syntaxe úmluvy používají odlišné atributy písma pro různé součásti syntaxe. Symboly a písma jsou následující:

|Atribut|Popis|
|---------------|-----------------|
|*neterminálu*|Kurzíva označuje neterminály.|
|**const**|Terminály tučného typu jsou slova a symboly vyhrazená literály, které je nutné zadat tak, jak je znázorněno. Znaky v tomto kontextu vždy rozlišují velká a malá písmena.|
|<sub>Odhlásit se</sub>|Neterminály následované <sub>optimalizované</sub> jsou vždy volitelné.|
|výchozí písmo|Znaky v sadě jsou popsány nebo uvedeny v tomto písmu, lze použít jako terminály v příkazech jazyka C.|

Dvojtečka (**:**) která následuje neterminál, zavádí jeho definici. Alternativní definice jsou uvedeny na samostatných řádcích, s výjimkou při začíná slova "jeden z."

## <a name="see-also"></a>Viz také

[Souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md)