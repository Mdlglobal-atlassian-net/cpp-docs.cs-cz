---
title: Upozornění kompilátoru (úroveň 4) C4220
ms.date: 11/04/2016
f1_keywords:
- C4220
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
ms.openlocfilehash: 90b66a9d819d3014c1e1437b691766ade420bd4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161253"
---
# <a name="compiler-warning-level-4-c4220"></a>Upozornění kompilátoru (úroveň 4) C4220

VarArgs odpovídají zbývajícím parametrům

Ve výchozím rozšíření Microsoft Extensions (/ze) je ukazatel na funkci shodný s ukazatelem na funkci s podobným argumentem, ale proměnnou.

## <a name="example"></a>Příklad

```c
// C4220.c
// compile with: /W4

int ( *pFunc1) ( int a, ... );
int ( *pFunc2) ( int a, int b);

int main()
{
   if ( pFunc1 != pFunc2 ) {};  // C4220
}
```

Tyto ukazatele se neshodují v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
