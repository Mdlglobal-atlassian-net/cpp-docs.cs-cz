---
title: Použití _Analysis_assume pro tipy pro analýzu kódu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
ms.openlocfilehash: 00577e6cc5ebd30e38e4fb7204b93c3ecf3fe112
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77418737"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Postupy: určení dalších informací o kódu pomocí _Analysis_assume

Můžete poskytnout nápovědu nástroji pro analýzu kódu pro C/C++ kód, který pomůže procesu analýzy a omezit upozornění. Chcete-li zadat další informace, použijte následující funkci:

`_Analysis_assume(`  `expr`  `)`

`expr` – libovolný výraz, který se předpokládá pro vyhodnocení na hodnotu true.

Nástroj Analýza kódu předpokládá, že podmínka reprezentovaná výrazem je pravdivá v místě, kde je funkce zobrazena a zůstává true, dokud není výraz změněn, například přiřazením proměnné.

> [!NOTE]
> `_Analysis_assume` nemá vliv na optimalizaci kódu. Mimo nástroj pro analýzu kódu je `_Analysis_assume` definováno jako No-op.

## <a name="example"></a>Příklad

Následující kód používá `_Analysis_assume` k opravě upozornění analýzy kódu [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Viz také

- [__assume](/cpp/intrinsics/assume)
