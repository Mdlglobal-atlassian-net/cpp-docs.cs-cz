---
title: Chyba kompilátoru C2594 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2594
dev_langs:
- C++
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9be22544930bb94c36ec5906cbf60d5caac143fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058006"
---
# <a name="compiler-error-c2594"></a>Chyba kompilátoru C2594

'operator': nejednoznačné převody z 'type1' na 'type2'

Žádný převod z *type1* k *type2* byl přímější než kterýkoli jiný. Doporučujeme dvě možná řešení pro převod z *type1* k *type2*. První možností je definování přímý převod z *type1* k *type2*, a druhou možností je k určení posloupnost převody z *type1* k  *Type2*.

Následující ukázka generuje C2594. Navržené řešení na chybu je posloupnost převody:

```
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```