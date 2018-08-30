---
title: Upozornění (úroveň 3) C4161 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4161
dev_langs:
- C++
helpviewer_keywords:
- C4161
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d279822d823ffb8efcaf08ff3f64cd9d82d0a44
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220555"
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