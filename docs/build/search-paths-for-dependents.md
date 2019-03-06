---
title: Cesty hledání pro závislosti
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: 9f2251a5fff9d708a783797d04606572e5ebce62
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426456"
---
# <a name="search-paths-for-dependents"></a>Cesty hledání pro závislosti

Každé závislé byla cesta volitelné vyhledávání, zadaný následujícím způsobem:

## <a name="syntax"></a>Syntaxe

```
{directory[;directory...]}dependent
```

## <a name="remarks"></a>Poznámky

NMAKE hledá závislé nejprve v aktuálním adresáři a poté v adresářích v uvedeném pořadí. Makra můžete zadat část nebo všechny cesty pro hledání. Uzavřete názvy adresářů ve složených závorkách ({}); několik adresářů oddělujte středníkem (;). Jsou povoleny mezery ani tabulátory.

## <a name="see-also"></a>Viz také:

[Závislé prvky](../build/dependents.md)
