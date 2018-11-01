---
title: Chyba kompilátoru C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: bd783d9510b1699b33f108a4ce8d8c491028b758
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541895"
---
# <a name="compiler-error-c3387"></a>Chyba kompilátoru C3387

'member': __declspec(dllexport) /\__declspec(dllimport) nelze použít pro spravované člen nebo typ WinRT

`dllimport` a [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` modifikátory nejsou platné pro spravované členy nebo typ prostředí Windows Runtime.

Následující ukázka generuje C3387 a ukazuje, jak ho opravit:

```
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```