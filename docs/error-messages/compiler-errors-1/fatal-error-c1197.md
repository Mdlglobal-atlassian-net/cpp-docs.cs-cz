---
title: Závažná chyba C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: e1c00a001c807b0cc6a5946b61ca4e9d5dc0167a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604149"
---
# <a name="fatal-error-c1197"></a>Závažná chyba C1197

nemůže odkazovat 'mscorlib.dll_1', protože program už odkazuje na "mscorlib.dll_2"

Kompilátor odpovídá verzi modulu common language runtime.  Však byl proveden pokus o tak, aby odkazovaly na verzi common soubor modulu runtime jazyka z předchozí verze.

Chcete-li vyřešit tuto chybu, odkazovat pouze na soubory z verze common language runtime, dodávané s verzí jazyka Visual C++, který je aktuálně kompilován s.

## <a name="example"></a>Příklad

Následující ukázka generuje C1197:

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```