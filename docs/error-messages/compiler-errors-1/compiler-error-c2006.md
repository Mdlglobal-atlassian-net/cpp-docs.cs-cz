---
title: Chyba kompilátoru C2006 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9468be17584a54047563bace2b35f5cb4888b41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031200"
---
# <a name="compiler-error-c2006"></a>Chyba kompilátoru C2006

"direktiva" očekával se název souboru, nalezeno "token"

Direktivy, jako [#include](../../preprocessor/hash-include-directive-c-cpp.md) nebo [#import](../../preprocessor/hash-import-directive-cpp.md) vyžaduje název souboru. Chcete-li chybu vyřešit, ujistěte se, že *token* je platný název souboru. Název souboru, umístěte do dvojitých uvozovek či ostrých závorek.

Následující ukázka generuje C2006:

```
// C2006.cpp
#include stdio.h   // C2006
```

Možná řešení:

```
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```