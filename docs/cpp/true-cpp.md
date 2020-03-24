---
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: b497c3c9eb1b30074c9b7286c438d0077525e05b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188035"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>Syntaxe

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>Poznámky

Toto klíčové slovo je jednou ze dvou hodnot proměnné typu [bool](../cpp/bool-cpp.md) nebo podmíněného výrazu (podmíněný výraz je nyní logický výraz true). Pokud `i` je typu **bool**, pak příkaz `i = true;` přiřadí **hodnotu true** pro `i`.

## <a name="example"></a>Příklad

```cpp
// bool_true.cpp
#include <stdio.h>
int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
