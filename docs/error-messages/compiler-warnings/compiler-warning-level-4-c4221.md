---
title: Kompilátor upozornění (úroveň 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: f552a5d76d1a778cdf72cbe079138f609350ffb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401095"
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