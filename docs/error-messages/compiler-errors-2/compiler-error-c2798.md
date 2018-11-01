---
title: Chyba kompilátoru C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: f3e8f0ac260e49866d1c654f89d34bf57a8ffbc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463050"
---
# <a name="compiler-error-c2798"></a>Chyba kompilátoru C2798

'super::member' je nejednoznačný

Více zděděných struktury obsahují člen odkazovaný adresou [mimořádně](../../cpp/super.md). Buď může oprava chyby:

- B1 a B2 se odebírá ze seznamu dědičnosti d.

- Změna názvu datového člena v B1 a B2.

Následující ukázka generuje C2798:

```
// C2798.cpp
struct B1 {
   int i;
};

struct B2 {
   int i;
};

struct D : B1, B2 {
   void g() {
      __super::i = 4; // C2798
   }
};
```