---
title: Chyba kompilátoru C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: 9c9772052b690ad87de1d408c06478d82d48e724
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464802"
---
# <a name="compiler-error-c2652"></a>Chyba kompilátoru C2652

'identifier': neplatné kopírovací konstuktor: první parametr nesmí být 'identifier'

První parametr v konstruktoru kopie má stejný typ jako třídy, struktury nebo sjednocení, pro který je definován. První parametr může být odkaz na typ, ale není typu.

Následující ukázka generuje C2651:

```
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```