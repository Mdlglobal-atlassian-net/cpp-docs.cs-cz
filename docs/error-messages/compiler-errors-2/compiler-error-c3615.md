---
title: C3615 Chyba kompilátoru | Microsoft Docs
ms.date: 10/24/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3615
dev_langs:
- C++
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1ab43f8e15535614cedf43dba42fef882bf87a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253390"
---
# <a name="compiler-error-c3615"></a>C3615 chyby kompilátoru

> Funkce constexpr '*funkce*' nemůže mít za následek konstantní výraz

Funkce *funkce* nebylo možné vyhodnotit jako `constexpr` v době kompilace. Chcete-li být `constexpr`, funkce můžete volat jenom jiné `constexpr` funkce.

## <a name="example"></a>Příklad

Visual Studio 2017 vyvolá chybu správně, je-li levé operand podmíněně vyhodnocování operace není platná v `constexpr` kontextu. Následující kód zkompiluje v sadě Visual Studio 2015, ale není v Visual Studio 2017.

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

Chcete-li tento problém vyřešit, buď deklarujte `array::size()` fungovat jako `constexpr` nebo odebrat `constexpr` kvalifikátor z `f`.