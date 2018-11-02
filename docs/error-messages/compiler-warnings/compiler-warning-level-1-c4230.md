---
title: Kompilátor upozornění (úroveň 1) C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: c8d223a286b8d42ca404fbfe7cbc51b67b3dd497
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529653"
---
# <a name="compiler-warning-level-1-c4230"></a>Kompilátor upozornění (úroveň 1) C4230

anachronismus: Modifikátory/kvalifikátory promíchaný; kvalifikátor se ignoruje.

Použití kvalifikátoru před modifikátor Microsoft, jako `__cdecl` je zastaralý postup.

## <a name="example"></a>Příklad

```
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```