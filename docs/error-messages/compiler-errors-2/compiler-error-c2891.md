---
title: Chyba kompilátoru C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: d9a1cdafdf7d3a2843aee4a20f71c7e6a4693150
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547936"
---
# <a name="compiler-error-c2891"></a>Chyba kompilátoru C2891

"parametr": nejde adresovat parametr šablony

Nelze převzít adresu proměnné parametr šablony, pokud má hodnotu lvalue. Parametry typu nejsou hodnoty lvalue, protože nemají žádnou adresu. Bez typu hodnoty v seznamech parametrů šablony, které nejsou hodnotami lvalues také nemusí adresu. Toto je příklad kódu, který způsobí, že chyba kompilátoru C2891, protože hodnota předána jako parametr šablony je generovaný kompilátorem kopie argumentu šablony.

```
template <int i> int* f() { return &i; }
```

Parametry šablony, které jsou l-hodnoty, jako jsou typy odkazů, můžete jeho adresu trvaly.

```
template <int& r> int* f() { return &r; }
```

Chcete-li opravit tuto chybu, není adresovat parametr šablony není l-hodnota.