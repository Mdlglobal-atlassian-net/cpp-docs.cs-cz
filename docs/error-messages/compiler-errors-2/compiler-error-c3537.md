---
title: Chyba kompilátoru C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: ef3e954987b84ea128342b38307769903df4b346
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740478"
---
# <a name="compiler-error-c3537"></a>Chyba kompilátoru C3537

Typ: nejde přetypovat na typ, který obsahuje auto.

Proměnnou nelze přetypovat na zadaný typ, protože typ obsahuje klíčové slovo `auto` a výchozí hodnota parametru [/Zc: auto](../../build/reference/zc-auto-deduce-variable-type.md) je platná.

## <a name="example"></a>Příklad

Následující kód poskytuje C3537, protože proměnné jsou přetypování na typ, který obsahuje klíčové slovo `auto`.

```cpp
// C3537.cpp
// Compile with /Zc:auto
int main()
{
   int value = 123;
   auto(value);                        // C3537
   (auto)value;                        // C3537
   auto x1 = auto(value);              // C3537
   auto x2 = (auto)value;              // C3537
   auto x3 = static_cast<auto>(value); // C3537
   return 0;
}
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)
