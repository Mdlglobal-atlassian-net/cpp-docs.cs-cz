---
title: Kompilátor upozornění (úroveň 1) C4229
ms.date: 11/04/2016
f1_keywords:
- C4229
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
ms.openlocfilehash: 05d11a02d3aea8748a2955dff77a0af750ee0275
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207498"
---
# <a name="compiler-warning-level-1-c4229"></a>Kompilátor upozornění (úroveň 1) C4229

anachronismus: Modifikátory pro data se ignorují.

Pomocí modifikátoru Microsoft, například `__cdecl` na datové deklarace je zastaralý postup.

## <a name="example"></a>Příklad

```
// C4229.cpp
// compile with: /W1 /LD
int __cdecl counter;   // C4229 cdecl ignored
```