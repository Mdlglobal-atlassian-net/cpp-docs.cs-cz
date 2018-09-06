---
title: Nahrazení makra | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f71ef2e1a8f337a4cd415169b6f9d817042f19a
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894392"
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

## <a name="see-also"></a>Viz také

[Použití makra NMAKE](../build/using-an-nmake-macro.md)