---
title: Cesty hledání závislých prvků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1fd407f99abb98fb949b6d5bcc45b10c6ff9121
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706293"
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