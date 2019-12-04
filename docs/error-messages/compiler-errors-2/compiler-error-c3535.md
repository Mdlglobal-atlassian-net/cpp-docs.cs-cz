---
title: Chyba kompilátoru C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 6b487c0f94a00ec64e0c2178265c5a8c27544a51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761553"
---
# <a name="compiler-error-c3535"></a>Chyba kompilátoru C3535

nejde odvodit typ pro typ1 z: typ2.

Typ proměnné deklarované klíčovým slovem `auto` nelze odvodit z typu inicializačního výrazu. Například k této chybě dochází, pokud je inicializační výraz vyhodnocen jako `void`, což není typ.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ujistěte se, že typ inicializačního výrazu není `void`.

1. Ujistěte se, že deklarace není ukazatel na základní typ. Další informace najdete v tématu [základní typy](../../cpp/fundamental-types-cpp.md).

1. Ujistěte se, že pokud je deklarace ukazatelem na typ, je inicializační výraz typem ukazatele.

## <a name="example"></a>Příklad

Následující příklad vrátí C3535, protože inicializační výraz je vyhodnocen jako `void`.

```cpp
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>Příklad

Následující příklad vrací C3535, protože příkaz deklaruje proměnnou `x` jako ukazatel na odvozený typ, ale typ výrazu inicializátoru je Double. V důsledku toho kompilátor nemůže odvodit typ proměnné.

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>Příklad

Následující příklad vrátí C3535, protože proměnná `p` deklaruje ukazatel na odvozený typ, ale inicializační výraz není typu ukazatele.

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)<br/>
[Základní typy](../../cpp/fundamental-types-cpp.md)
