---
title: Kompilátor upozornění (úrovně 1 a 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 8050edbd7a653776d046bc7b4155fd43094d9a5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187519"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Kompilátor upozornění (úrovně 1 a 4) C4949

direktivy pragma "spravované" a 'nespravované' mají smysl jenom při kompilaci s "/ clr [: možnost]"

Kompilátor ignoruje [spravované](../../preprocessor/managed-unmanaged.md) a nespravovaných direktiv pragma, pokud není zdrojový kód zkompilován s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). Toto upozornění je informační.

Následující ukázka generuje C4949:

```
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

Když **#pragma unmanaged** použijete bez **/CLR**, C4949 je upozornění úrovně 4.

Následující ukázka generuje C4949:

```
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```