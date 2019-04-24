---
title: Cesty hledání pro závislosti
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: bc2c430c43f408065234c9df50977003eafd3cb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318300"
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

[Závislé prvky](dependents.md)
