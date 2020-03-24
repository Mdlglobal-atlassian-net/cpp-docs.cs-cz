---
title: Upozornění kompilátoru (úroveň 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: a556fbffad41d04b3eb0ea1acfd5e8739ddd5b68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186800"
---
# <a name="compiler-warning-level-1-c4399"></a>Upozornění kompilátoru (úroveň 1) C4399

> '*symbol*': symbol na základě procesu by neměl být označen pomocí __declspec (dllimport) při kompilaci s možností/CLR: Pure

## <a name="remarks"></a>Poznámky

Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

Data z nativní bitové kopie nebo image s nativním konstruktorem a konstrukcemi CLR není možné importovat do čistě image. Chcete-li vyřešit toto upozornění, zkompilujte pomocí **/CLR** (not **/clr: Pure**) nebo odstraňte `__declspec(dllimport)`.

## <a name="example"></a>Příklad

Následující ukázka generuje C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```
