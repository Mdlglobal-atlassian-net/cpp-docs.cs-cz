---
title: Chyba kompilátoru C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: 64f81929916cd3a4adf38a302ea34d46d9a5c070
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756549"
---
# <a name="compiler-error-c2006"></a>Chyba kompilátoru C2006

u direktivy očekával se název souboru, našlo se: token.

Direktivy jako [#include](../../preprocessor/hash-include-directive-c-cpp.md) nebo [#import](../../preprocessor/hash-import-directive-cpp.md) vyžadují název souboru. Pokud chcete chybu vyřešit, ujistěte se, že *token* je platný název souboru. Také zadejte název souboru do dvojitých uvozovek nebo lomených závorek.

Následující ukázka generuje C2006:

```cpp
// C2006.cpp
#include stdio.h   // C2006
```

Možné řešení:

```cpp
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```
