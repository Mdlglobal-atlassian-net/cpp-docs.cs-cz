---
title: Vedlejší efekty
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
ms.openlocfilehash: de5e398afd8b95cfe5596f487a36b6a2d27e3287
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147474"
---
# <a name="side-effects"></a>Vedlejší efekty

Pořadí vyhodnocování výrazů je definován konkrétní implementací s výjimkou, kdy jazyk zaručuje určité pořadí vyhodnocování (jak je uvedeno v [přednost a pořadí vyhodnocení](../c-language/precedence-and-order-of-evaluation.md)). V následujících voláních funkce mohou například nastat vedlejší účinky:

```
add( i + 1, i = j + 2 );
myproc( getc(), getc() );
```

Argumenty volání funkce mohou být vyhodnoceny v libovolném pořadí. Výraz `i + 1` může být vyhodnocen před výrazem `i = j + 2` nebo výraz `i = j + 2` může být vyhodnocen před výrazem `i + 1`. Výsledek se v každém případě liší. Stejně tak není možné zaručit, které znaky budou skutečně předány do procedury `myproc`. Jelikož operace unárního zvýšení a snížení zahrnují přiřazení, mohou tyto operace způsobovat vedlejší účinky, jak je znázorněno v následujícím příkladu:

```
x[i] = i++;
```

V tomto příkladu nelze předvídat hodnotu `x`, která je upravena. Hodnota dolního indexu může být novou nebo předešlou hodnotou `i`. Výsledek se může lišit na základě různých kompilátorů nebo různých úrovní optimalizace.

Vzhledem k tomu, že jazyk C nedefinuje pořadí vyhodnocování vedlejších účinků, jsou obě metody vyhodnocení správné a mohou být implementovány. Abyste se ujistili, že je kód přenosný a jasný, je třeba se vyhnout příkazům, které jsou závislé na určitém pořadí vyhodnocení vedlejších účinků.

## <a name="see-also"></a>Viz také:

[Vyhodnocení výrazu](../c-language/expression-evaluation-c.md)
