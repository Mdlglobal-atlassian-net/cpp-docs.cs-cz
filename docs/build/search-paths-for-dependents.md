---
title: Cesty hledání pro závislosti
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: 8856d845d51072d205c84278978c7fbb447aed9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448799"
---
# <a name="search-paths-for-dependents"></a>Cesty hledání pro závislosti

Každé závislé byla cesta volitelné vyhledávání, zadaný následujícím způsobem:

## <a name="syntax"></a>Syntaxe

```
{directory[;directory...]}dependent
```

## <a name="remarks"></a>Poznámky

NMAKE hledá závislé nejprve v aktuálním adresáři a poté v adresářích v uvedeném pořadí. Makra můžete zadat část nebo všechny cesty pro hledání. Uzavřete názvy adresářů ve složených závorkách ({}); několik adresářů oddělujte středníkem (;). Jsou povoleny mezery ani tabulátory.

## <a name="see-also"></a>Viz také

[Závislé prvky](../build/dependents.md)