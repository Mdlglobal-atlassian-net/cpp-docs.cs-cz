---
title: Chyba kompilátoru C3537 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3537
dev_langs:
- C++
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f04500998adf132594b91fc38f82c8bec4b1c5c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107682"
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