---
title: Chyba kompilátoru C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: e966295b5ab63350828ddb73d6791a9e30bb5c59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404101"
---
# <a name="compiler-error-c3615"></a>Chyba kompilátoru C3615

> Funkce constexpr '*funkce*' nemůže mít v konstantním výrazu

Funkce *funkce* nemůže být vyhodnocena jako `constexpr` v době kompilace. Chcete-li být `constexpr`, funkce může volat pouze jiné `constexpr` funkce.

## <a name="example"></a>Příklad

Visual Studio 2017 správně vyvolá chybu, pokud operand na levé straně podmíněně vyhodnocování operace není platná v `constexpr` kontextu. Následující kód se zkompiluje ve Visual Studiu 2015 ale není v sadě Visual Studio 2017.

```cpp
// C3615.cpp
// Compile with: /c

template<int N>
struct myarray
{
    int size() const { return N; }
};

constexpr bool f(const myarray<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615 starting in Visual Studio 2017
}
```

Chcete-li tento problém vyřešit, buď deklarovat `array::size()` fungovat jako `constexpr` nebo odebrat `constexpr` kvalifikátor z `f`.