---
title: Chyba kompilátoru C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: c1a5b6edbc87e14de267cf962dc2b1a71dd6be12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200535"
---
# <a name="compiler-error-c3615"></a>Chyba kompilátoru C3615

> výsledkem funkce constexpr '*Function*' nemůže být konstantní výraz.

*Funkce Function nemohla být* vyhodnocena jako `constexpr` v době kompilace. Aby bylo možné `constexpr`, funkce může volat pouze jiné funkce `constexpr`.

## <a name="example"></a>Příklad

Pokud je levý operand podmíněného vyhodnocení operace v kontextu `constexpr` neplatný, Visual Studio 2017 správně vyvolá chybu. Následující kód je zkompilován v aplikaci Visual Studio 2015, ale ne v aplikaci Visual Studio 2017.

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

Chcete-li tento problém vyřešit, buď Deklarujte funkci `array::size()` jako `constexpr` nebo odeberte kvalifikátor `constexpr` ze `f`.
