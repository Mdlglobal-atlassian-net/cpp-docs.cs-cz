---
title: Chyba kompilátoru C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: 3d290bd2288f76d0ddefa2057e3e01c9edc3cbc7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205319"
---
# <a name="compiler-error-c2461"></a>Chyba kompilátoru C2461

> '*Class*': v syntaxi konstruktoru chybí formální parametry

Konstruktor třídy neurčuje žádné formální parametry. Deklarace konstruktoru musí určovat formální seznam parametrů. Seznam může být prázdný.

Chcete-li tento problém vyřešit, přidejte dvojici závorek za deklaraci *třídy*::**Class*.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak opravit C2461:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```
