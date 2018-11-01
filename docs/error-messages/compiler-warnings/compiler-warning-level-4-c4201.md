---
title: Kompilátor upozornění (úroveň 4) C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: c7c10273e06ec35528dbd9d51c02bb844d275638
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445796"
---
# <a name="compiler-warning-level-4-c4201"></a>Kompilátor upozornění (úroveň 4) C4201

používá se nestandardní rozšíření: struktura/sjednocení nameless

Pod rozšíření společnosti Microsoft (/Ze) můžete určit strukturu bez deklarátorem jako členy z jiné struktury nebo sjednocení. Tyto struktury vygenerují chybu podle kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Příklad

```
// C4201.cpp
// compile with: /W4
struct S
{
   float y;
   struct
   {
      int a, b, c;  // C4201
   };
} *p_s;

int main()
{
}
```