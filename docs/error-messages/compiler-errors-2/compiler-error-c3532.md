---
title: Chyba kompilátoru C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: 2ef5eb3c2bedd9defbd0b80e6d8c5c8912fcf16d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761930"
---
# <a name="compiler-error-c3532"></a>Chyba kompilátoru C3532

Type: nesprávné použití auto.

Zadaný typ nelze deklarovat s klíčovým slovem `auto`. Například nelze použít klíčové slovo `auto` k deklaraci pole nebo návratového typu metody.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ujistěte se, že inicializační výraz vrací platný typ.

1. Ujistěte se, že nedeklarujete pole nebo návratový typ metody.

## <a name="example"></a>Příklad

Následující příklad vrací C3532, protože klíčové slovo `auto` nemůže deklarovat návratový typ metody.

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>Příklad

Následující příklad vrací C3532, protože klíčové slovo `auto` nemůže deklarovat pole.

```cpp
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)
