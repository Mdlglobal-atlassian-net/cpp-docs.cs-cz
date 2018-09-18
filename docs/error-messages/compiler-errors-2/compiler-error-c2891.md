---
title: Chyba kompilátoru C2891 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86d81662cb02fa3c8f6af75009daf4dab9b70196
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016556"
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