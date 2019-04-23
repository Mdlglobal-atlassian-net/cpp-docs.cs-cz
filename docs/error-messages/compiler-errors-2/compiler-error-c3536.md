---
title: Chyba kompilátoru C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a16c5bd46d806d09861d5734b637c2c9d9b2f9d0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031892"
---
# <a name="compiler-error-c3536"></a>Chyba kompilátoru C3536

'symbol': nejde použít, dokud není inicializován

Zadaný symbol nejde používat před inicializací. V praxi to znamená, že proměnné nelze inicializovat.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Proměnná se sebou samým, nebyl inicializován.

## <a name="example"></a>Příklad

V následujícím příkladu vrací C3536, protože každá proměnná je inicializována sám se sebou.

```
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)