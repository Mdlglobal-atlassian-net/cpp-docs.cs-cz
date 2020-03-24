---
title: Upozornění kompilátoru (úroveň 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: fa948865685af4cbd6a865cfbf1d8546b29ab280
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161136"
---
# <a name="compiler-warning-level-4-c4221"></a>Upozornění kompilátoru (úroveň 4) C4221

používá se nestandardní rozšíření: Identifier: nejde inicializovat pomocí adresy automatické proměnné.

S výchozími rozšířeními společnosti Microsoft (/ze) můžete inicializovat agregovaný typ (**pole**, `struct`nebo **sjednocení**) s adresou místní (automatické) proměnné.

## <a name="example"></a>Příklad

```c
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

Taková inicializace nejsou v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) platná.
