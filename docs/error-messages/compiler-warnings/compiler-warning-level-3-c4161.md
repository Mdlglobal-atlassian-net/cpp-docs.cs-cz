---
title: Kompilátor upozornění (úroveň 3) C4161
ms.date: 08/27/2018
f1_keywords:
- C4161
helpviewer_keywords:
- C4161
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
ms.openlocfilehash: e1bbc949c298a7cfb6c3a3a061616db3dc4730f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555830"
---
# <a name="compiler-warning-level-3-c4161"></a>Kompilátor upozornění (úroveň 3) C4161

> #<a name="pragma-pragmapop--more-pops-than-pushes"></a>direktivy pragma *– Direktiva pragma*(protokolem POP služby služby..): Další POP než push

## <a name="remarks"></a>Poznámky

Protože váš zdrojový kód obsahuje jeden další pop než push pro direktivu pragma *– Direktiva pragma*, zásobníku nemusí fungovat podle očekávání. Vyhněte se upozornění, ujistěte se, že počet bodů POP, nesmí překročit počet nabízených oznámení.

## <a name="example"></a>Příklad

Následující příklad generuje C4161:

```cpp
// C4161.cpp
// compile with: /W3 /LD
#pragma pack(push, id)
#pragma pack(pop, id)
#pragma pack(pop, id)   // C4161, an extra pop

#pragma bss_seg(".my_data1")
int j;

#pragma bss_seg(push, stack1, ".my_data2")
int l;

#pragma bss_seg(pop, stack1)
int m;

#pragma bss_seg(pop, stack1)   // C4161
```