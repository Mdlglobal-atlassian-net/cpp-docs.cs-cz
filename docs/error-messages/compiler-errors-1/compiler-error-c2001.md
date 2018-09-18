---
title: Chyba kompilátoru C2001 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71048a706678e4d9e6906972ebf148748927e829
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088239"
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