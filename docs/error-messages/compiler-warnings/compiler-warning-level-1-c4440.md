---
title: Upozornění kompilátoru (úroveň 1) C4440
ms.date: 11/04/2016
f1_keywords:
- C4440
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
ms.openlocfilehash: a2d4bf160cbbabacc1dc3d747a8e4ddb37c6ad46
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966045"
---
# <a name="compiler-warning-level-1-c4440"></a>Upozornění kompilátoru (úroveň 1) C4440

předefinování konvence volání z ' calling_convention1 ' na ' calling_convention2 ' se ignoruje.

Pokus o změnu konvence volání byl ignorován.

Následující ukázka generuje C4440:

```cpp
// C4440.cpp
// compile with: /W1 /LD /clr
typedef void __clrcall F();
typedef F __cdecl *PFV;   // C4440
```