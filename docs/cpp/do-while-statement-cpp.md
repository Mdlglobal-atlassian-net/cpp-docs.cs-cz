---
title: do-while – příkaz (C++)
ms.date: 11/04/2016
f1_keywords:
- do_cpp
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
ms.openlocfilehash: f52c065210a8861dc065508248a506770b039b1d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189270"
---
# <a name="do-while-statement-c"></a>do-while – příkaz (C++)

Provede *příkaz* opakovaně, dokud není zadaná podmínka ukončení ( *výraz*) vyhodnocena jako nula.

## <a name="syntax"></a>Syntaxe

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Poznámky

Test ukončovací podmínky je proveden po každém spuštění smyčky; Proto smyčka do **-while** se spustí jednou nebo vícekrát v závislosti na hodnotě ukončovacího výrazu. Příkaz **do-while** může také skončit při spuštění příkazu [Break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md)nebo [return](../cpp/return-statement-cpp.md) v těle příkazu.

*Výraz* musí být aritmetického typu nebo typu ukazatele. Provádění pokračuje následujícím způsobem:

1. Tělo příkazu je spuštěno.

1. Dále je vyhodnocen *výraz* . Pokud má *výraz* hodnotu false, příkaz do **-while** se ukončí a řízení projde dalšímu příkazu v programu. Pokud je *výraz* true (nenulový), proces se opakuje, počínaje krokem 1.

## <a name="example"></a>Příklad

Následující příklad znázorňuje příkaz **do-while** :

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>Viz také

[Příkazy iterace](../cpp/iteration-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[while – příkaz (C++)](../cpp/while-statement-cpp.md)<br/>
[for – příkaz (C++)](../cpp/for-statement-cpp.md)<br/>
[Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)
