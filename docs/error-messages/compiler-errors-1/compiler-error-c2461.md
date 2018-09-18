---
title: Chyba kompilátoru C2461 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39d58b315fdd7e3c4e1899041cebf8400813ed40
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029296"
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