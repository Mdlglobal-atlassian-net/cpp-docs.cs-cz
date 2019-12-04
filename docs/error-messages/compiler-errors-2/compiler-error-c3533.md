---
title: Chyba kompilátoru C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: ce95bba417e9be3603f15376a0fd65a48f951a2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755639"
---
# <a name="compiler-error-c3533"></a>Chyba kompilátoru C3533

' type ': parametr nemůže mít typ, který obsahuje ' auto '

Metoda nebo parametr šablony nelze deklarovat s klíčovým slovem `auto`, pokud je použita výchozí hodnota [/Zc: auto](../../build/reference/zc-auto-deduce-variable-type.md) .

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Odeberte klíčové slovo `auto` z deklarace parametru.

## <a name="example"></a>Příklad

Následující příklad vrátí C3533, protože deklaruje parametr funkce s klíčovým slovem `auto` a je zkompilován pomocí **/Zc: auto**.

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>Příklad

Následující příklad vrací C3533 v režimu C++ 14, protože deklaruje parametr šablony s klíčovým slovem `auto` a je zkompilován pomocí **/Zc: auto**. (V C++ 17 je to platná definice šablony třídy s jedním netypovým parametrem šablony, jehož typ je odvozený.)

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (odvození typu proměnné)](../../build/reference/zc-auto-deduce-variable-type.md)
