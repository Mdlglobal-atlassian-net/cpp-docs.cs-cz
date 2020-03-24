---
title: Upozornění kompilátoru (úroveň 1) C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: 27e7765c68b0bb6fb8c289260b16af1f3fe27054
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175802"
---
# <a name="compiler-warning-level-1-c4286"></a>Upozornění kompilátoru (úroveň 1) C4286

' typ1 ': je zachyceno základní třídou (' typ2 ') na řádku číslo

Zadaný typ výjimky je zpracován předchozí obslužnou rutinou. Typ pro druhý catch je odvozen od typu prvního. Výjimky pro zachytávání výjimek základní třídy pro odvozenou třídu.

## <a name="example"></a>Příklad

```cpp
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
