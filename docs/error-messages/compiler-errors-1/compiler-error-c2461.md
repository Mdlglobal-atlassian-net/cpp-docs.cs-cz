---
title: Chyba kompilátoru C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: e8f82ed4ce8ad77a22961a42c8e9a256e6f647db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368029"
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