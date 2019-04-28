---
title: Chyba kompilátoru C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: d9a1cdafdf7d3a2843aee4a20f71c7e6a4693150
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366365"
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