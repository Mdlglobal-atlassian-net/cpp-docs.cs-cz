---
title: Chyba kompilátoru C3387 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3387
dev_langs:
- C++
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0dafe972db1b3210e9243e34cc02e7a0366bdd65
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030752"
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