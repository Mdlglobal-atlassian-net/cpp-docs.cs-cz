---
title: Upozornění kompilátoru (úroveň 4) C4125
ms.date: 11/04/2016
f1_keywords:
- C4125
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
ms.openlocfilehash: f194f0efc8012bf027e4785c2f398a0a7027b368
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991578"
---
# <a name="compiler-warning-level-4-c4125"></a>Upozornění kompilátoru (úroveň 4) C4125

desítková číslice končí osmičkovou řídicí sekvencí.

Kompilátor vyhodnocuje osmičkové číslo bez desítkové číslice a předpokládá, že desítková číslice je znak.

## <a name="example"></a>Příklad

```cpp
// C4125a.cpp
// compile with: /W4
char array1[] = "\709"; // C4125
int main()
{
}
```

Pokud je číslice 9 určena jako znak, opravte příklad následujícím způsobem:

```cpp
// C4125b.cpp
// compile with: /W4
char array[] = "\0709";  // C4125 String containing "89"
int main()
{
}
```
