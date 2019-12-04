---
title: Chyba kompilátoru C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 2bf9bd322812764b2f63493d4b22b58d853a25fa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756835"
---
# <a name="compiler-error-c2001"></a>Chyba kompilátoru C2001

nový řádek v konstantě

Řetězcová konstanta nemůže pokračovat na druhém řádku, Pokud neprovedete následující akce:

- Ukončí první řádek zpětným lomítkem.

- Zavřete řetězec na prvním řádku pomocí dvojité uvozovky a otevřete řetězec na dalším řádku s jiným znakem dvojité uvozovky.

Ukončení prvního řádku s \n není dostatečné.

## <a name="example"></a>Příklad

Následující ukázka generuje C2001:

```cpp
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

Mezery na začátku dalšího řádku po znaku pro pokračování řádku jsou obsaženy v řetězcové konstantě. Žádný z výše uvedených příkladů do řetězcové konstanty nevloží znak nového řádku. Můžete vložit znak nového řádku, jak je znázorněno zde:

```cpp
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
