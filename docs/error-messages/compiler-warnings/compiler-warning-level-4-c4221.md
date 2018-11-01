---
title: Kompilátor upozornění (úroveň 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: f552a5d76d1a778cdf72cbe079138f609350ffb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511238"
---
# <a name="compiler-warning-level-4-c4221"></a>Kompilátor upozornění (úroveň 4) C4221

používá se nestandardní rozšíření: 'identifier': Nelze inicializovat pomocí adresy automatické proměnné

Pomocí rozšíření výchozí společnosti Microsoft (/Ze), můžete inicializovat požadovaný typ agregace (**pole**, `struct`, nebo **sjednocení**) adresu lokální proměnné (automatické).

## <a name="example"></a>Příklad

```
// C4221.c
// compile with: /W4
struct S
{
   int *i;
};

void func()
{
   int j;
   struct S s1 = { &j };   // C4221
}

int main()
{
}
```

Tyto inicializace jsou neplatné pod kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).