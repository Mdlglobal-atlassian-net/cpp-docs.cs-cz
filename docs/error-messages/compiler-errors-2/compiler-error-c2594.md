---
title: Chyba kompilátoru C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: 75e3b438dd69f8879fdc2273a8f0357229941340
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386899"
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