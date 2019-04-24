---
title: Chyba kompilátoru C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: c23f17483925f25468214165fb459db577e576fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209000"
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