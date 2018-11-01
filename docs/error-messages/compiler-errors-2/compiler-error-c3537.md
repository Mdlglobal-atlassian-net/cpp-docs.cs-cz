---
title: Chyba kompilátoru C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: 22387470019b0118d06b4cacd82a1df5c3e505fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576121"
---
# <a name="compiler-error-c3537"></a>Chyba kompilátoru C3537

'type': nelze přetypovat na typ, který obsahuje nastavení auto.

Nelze převést proměnnou pro zadaný typ, protože obsahuje typ `auto` – klíčové slovo a ve výchozím nastavení [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) – možnost kompilátoru je v platnosti.

## <a name="example"></a>Příklad

Následující kód provede C3537, protože proměnné jsou přetypovat na typ, který obsahuje `auto` – klíčové slovo.

```
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

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../../cpp/auto-keyword.md)