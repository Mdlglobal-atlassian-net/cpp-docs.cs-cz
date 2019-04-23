---
title: Chyba kompilátoru C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 7a627ce28e60f42dabcf0a257464a8bfbd58b9a4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028616"
---
# <a name="compiler-error-c2483"></a>Chyba kompilátoru C2483

>"*identifikátor*': nelze použít deklaraci objektu se konstruktor nebo destruktor"vlákno"

Tato chybová zpráva je zastaralé v sadě Visual Studio 2015 a novější verze. V předchozích verzích, jsou proměnné deklarovány s `thread` atribut se nedá inicializovat pomocí konstruktoru nebo jiný výraz, který se vyžaduje vyhodnocení za běhu. Statický výraz je potřeba inicializovat `thread` data.

## <a name="example"></a>Příklad

Následující ukázka generuje C2483 v sadě Visual Studio 2013 a dřívějších verzích.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Viz také:

[thread](../../cpp/thread.md)