---
title: Nahrazení makra
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
ms.openlocfilehash: 43dc9133c53b1c436c0df8c3db66ae8f18604222
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321816"
---
# <a name="macro-substitution"></a>Nahrazení makra

Když *makro* je vyvolána, každý výskyt *řetězec1* do její definice je nahrazen řetězec *řetězec2*.

## <a name="syntax"></a>Syntaxe

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>Poznámky

Nahrazení makra je velká a malá písmena a je literál; *řetězec1* a *řetězec2* nejde vyvolat makra. Nahrazení neupravuje původní definice. Můžete nahradit text v žádné předdefinované makro s výjimkou [ $$@ ](filename-macros.md).

Mezery ani tabulátory před dvojtečkou; Některé za dvojtečku jsou interpretovány jako literál. Pokud *řetězec2* je null, použije všechny výskyty *řetězec1* budou odstraněny z řetězce definici makra.

## <a name="see-also"></a>Viz také:

[Použití makra NMAKE](using-an-nmake-macro.md)
