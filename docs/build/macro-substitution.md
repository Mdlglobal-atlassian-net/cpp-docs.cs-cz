---
title: Nahrazení makra
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
ms.openlocfilehash: d82aed5a34b7cafad0e40146470972dc6ff02424
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414678"
---
# <a name="macro-substitution"></a>Nahrazení makra

Když *makro* je vyvolána, každý výskyt *řetězec1* do její definice je nahrazen řetězec *řetězec2*.

## <a name="syntax"></a>Syntaxe

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>Poznámky

Nahrazení makra je velká a malá písmena a je literál; *řetězec1* a *řetězec2* nejde vyvolat makra. Nahrazení neupravuje původní definice. Můžete nahradit text v žádné předdefinované makro s výjimkou [ $$@ ](../build/filename-macros.md).

Mezery ani tabulátory před dvojtečkou; Některé za dvojtečku jsou interpretovány jako literál. Pokud *řetězec2* je null, použije všechny výskyty *řetězec1* budou odstraněny z řetězce definici makra.

## <a name="see-also"></a>Viz také:

[Použití makra NMAKE](../build/using-an-nmake-macro.md)
