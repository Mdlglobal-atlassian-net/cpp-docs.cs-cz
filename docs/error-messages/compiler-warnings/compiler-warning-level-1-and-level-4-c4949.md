---
title: Upozornění (úrovně 1 a 4) C4949 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f806912188ada3a4f97f0b1500e811d1271f40fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077305"
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