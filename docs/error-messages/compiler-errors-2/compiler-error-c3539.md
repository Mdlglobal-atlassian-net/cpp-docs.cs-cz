---
title: Chyba kompilátoru C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 85381b237480b86b59c33f02601a1b9dc644a5a4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761527"
---
# <a name="compiler-error-c3539"></a>Chyba kompilátoru C3539

' type ': argument šablony nemůže být typ, který obsahuje ' auto '

Zadaný typ argumentu šablony nemůže obsahovat použití klíčového slova `auto`.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Nezadávejte argument šablony s klíčovým slovem `auto`.

## <a name="example"></a>Příklad

Následující příklad vrací C3539.

```cpp
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)
