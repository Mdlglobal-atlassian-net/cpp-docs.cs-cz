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
ms.openlocfilehash: d930c1884975288ff11f4d4e5cf2728e717e17d5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326664"
---
# <a name="do-while-statement-c"></a>do-while – příkaz (C++)

Spustí *příkaz* opakovaně, dokud není zadaná ukončovací podmínka ( *výraz*) vyhodnocen jako nula.

## <a name="syntax"></a>Syntaxe

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Poznámky

Podmínka ukončení zkoušky se provádí po každém spuštění smyčky; Proto **proveďte – zatímco** cyklus se opakuje, jednou nebo vícekrát, v závislosti na hodnotě výrazu ukončení. **Proveďte-při** příkaz může také skončit při [přerušení](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), nebo [vrátit](../cpp/return-statement-cpp.md) je proveden příkaz v rámci těla příkazu.

*Výraz* musí mít aritmetický typ nebo typ ukazatele. Spuštění probíhá následujícím způsobem:

1. Provede se tělo příkazu.

1. Dále *výraz* vyhodnocena. Pokud *výraz* má hodnotu false, **proveďte-při** příkaz skončí a předá řízení dalšímu příkazu v programu. Pokud *výraz* má hodnotu true (nenulový), proces se opakuje, počínaje krokem 1.

## <a name="example"></a>Příklad

Následující příklad ukazuje **proveďte – zatímco** – příkaz:

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

## <a name="see-also"></a>Viz také:

[Příkazy iterace](../cpp/iteration-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[while – příkaz (C++)](../cpp/while-statement-cpp.md)<br/>
[for – příkaz (C++)](../cpp/for-statement-cpp.md)<br/>
[Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)