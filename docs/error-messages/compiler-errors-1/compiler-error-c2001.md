---
title: Chyba kompilátoru C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 03b54fe2373063c8c0f9905da93822928392998d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596362"
---
# <a name="compiler-error-c2001"></a>Chyba kompilátoru C2001

Obsahuje znak nového řádku – konstanta

Řetězcová konstanta nemůže pokračovat na druhý řádek, pokud nastavíte takto:

- Konec řádku první zpětným lomítkem.

- Zavřete řetězec na prvním řádku s dvojité uvozovky a otevřete řetězec na dalším řádku s jinou dvojité uvozovky.

Končí první řádek s \n není dostatečná.

## <a name="example"></a>Příklad

Následující ukázka generuje C2001:

```
// C2001.cpp
// C2001 expected
#include <stdio.h>

int main()
{
    printf_s("Hello,
             world");
    printf_s("Hello,\n
             world");
}
```

## <a name="example"></a>Příklad

Mezery na začátku dalšího řádku za znakem pokračování řádku jsou součástí řetězcová konstanta. Žádná z příkladů uvedených výše vložit znak nového řádku do řetězcová konstanta. Můžete vložit znak nového řádku, jak je znázorněno zde:

```
// C2001b.cpp
#include <stdio.h>

int main()
{
    printf_s("Hello,\n\
             world");

    printf_s("Hello,\
             \nworld");

    printf_s("Hello,\n"
             "world");

    printf_s("Hello,"
             "\nworld");

    printf_s("Hello,"
             " world");

    printf_s("Hello,\
             world");
}
```