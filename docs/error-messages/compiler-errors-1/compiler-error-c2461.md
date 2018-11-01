---
title: Chyba kompilátoru C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: e8f82ed4ce8ad77a22961a42c8e9a256e6f647db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535132"
---
# <a name="compiler-error-c2461"></a>Chyba kompilátoru C2461

> "*třídy*': syntaxi konstruktoru chybí formální parametry.

Konstruktor pro třídu neurčuje žádné formální parametry. Deklarace konstruktoru musíte zadat seznam formálních parametrů. Seznam může být prázdný.

Chcete tento problém vyřešit, přidejte dvojici závorek za deklaraci *třídy*:: **třídy*.

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