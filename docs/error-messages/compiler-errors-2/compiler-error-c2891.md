---
title: Chyba kompilátoru C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: 2544cfc9e8cff283a7c3e0ace499408bb84cd046
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201631"
---
# <a name="compiler-error-c2891"></a>Chyba kompilátoru C2891

parametr: nejde adresovat parametr šablony.

Adresu parametru šablony nelze převzít, pokud se nejedná o lvalue. Parametry typu nejsou hodnoty lvalue, protože nemají žádnou adresu. Hodnoty, které nejsou typu v seznamech parametrů šablony, které nejsou hodnoty lvalue také nemají adresu. Toto je příklad kódu, který způsobí chybu kompilátoru C2891, protože hodnota předaná jako parametr šablony je kopie argumentu šablony vygenerovaná kompilátorem.

```
template <int i> int* f() { return &i; }
```

V parametrech šablony, které jsou hodnoty lvalue, jako jsou typy odkazů, může být zabraná adresa.

```
template <int& r> int* f() { return &r; }
```

Chcete-li opravit tuto chybu, nepoužívejte adresu parametru šablony, pokud se nejedná o lvalue.
