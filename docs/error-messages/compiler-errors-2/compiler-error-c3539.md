---
title: Chyba kompilátoru C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 7cba9e0271d16420c5cfe4adbed2c7121d139d8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523914"
---
# <a name="compiler-error-c3539"></a>Chyba kompilátoru C3539

'type': argument šablony nemůže být typ, který obsahuje nastavení auto.

Typ argumentu uvedené šabloně nemůže obsahovat využití nástroje `auto` – klíčové slovo.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Nezadávejte argument šablony se `auto` – klíčové slovo.

## <a name="example"></a>Příklad

Následující příklad provede C3539.

```
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../../cpp/auto-keyword.md)