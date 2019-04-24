---
title: Kompilátor upozornění (úroveň 1) C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: be02d330678eaab7f538ed092641f957bdcb01b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207066"
---
# <a name="compiler-warning-level-1-c4286"></a>Kompilátor upozornění (úroveň 1) C4286

'type1': se zachycuje prostřednictvím základní třídy ('type2') na číslo řádku

Typ Zadaná výjimka je zpracována předchozí obslužnou rutinou. Typ pro druhý catch je odvozen z typu prvního. Výjimky pro základní třídu zachytit výjimky pro odvozenou třídu.

## <a name="example"></a>Příklad

```
//C4286.cpp
// compile with: /W1
#include <eh.h>
class C {};
class D : public  C {};
int main()
{
    try
    {
        throw "ooops!";
    }
    catch( C ) {}
    catch( D ) {}  // warning C4286, D is derived from C
}
```