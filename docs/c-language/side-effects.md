---
title: Vedlejší efekty
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
ms.openlocfilehash: 97fbb2bc382216e27139a01d1e803a15bd16160b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582559"
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

## <a name="see-also"></a>Viz také

[Vyhodnocení výrazu](../c-language/expression-evaluation-c.md)