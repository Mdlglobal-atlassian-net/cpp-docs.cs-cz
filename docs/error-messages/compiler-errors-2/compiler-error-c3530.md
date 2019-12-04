---
title: Chyba kompilátoru C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 3766eaa83457ba6cffaf8b1599983a065772911c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750140"
---
# <a name="compiler-error-c3530"></a>Chyba kompilátoru C3530

možnost auto nejde kombinovat s žádným jiným specifikátorem typu.

Specifikátor typu se používá s klíčovým slovem `auto`.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Nepoužívejte specifikátor typu v deklaraci proměnné, která používá klíčové slovo `auto`.

## <a name="example"></a>Příklad

Následující příklad vrátí C3530, protože proměnná `x` je deklarována s klíčovým slovem `auto` a typem `int`a protože je příklad kompilován s parametrem **/Zc: auto**.

```cpp
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)
