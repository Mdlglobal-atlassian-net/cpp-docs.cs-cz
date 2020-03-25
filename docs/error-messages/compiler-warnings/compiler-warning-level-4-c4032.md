---
title: Upozornění kompilátoru (úroveň 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: 84bfef28de2899a216616a6a5d9fb15422f2afec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185409"
---
# <a name="compiler-warning-level-4-c4032"></a>Upozornění kompilátoru (úroveň 4) C4032

formální parametr number má při zvýšení úrovně jiný typ.

Typ parametru není kompatibilní, a to prostřednictvím výchozích propagačních akcí s typem v předchozí deklaraci.

Jedná se o chybu ve standardu ANSI C ([/za](../../build/reference/za-ze-disable-language-extensions.md)) a upozornění v části rozšíření společnosti Microsoft (/ze).

## <a name="example"></a>Příklad

```c
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```
