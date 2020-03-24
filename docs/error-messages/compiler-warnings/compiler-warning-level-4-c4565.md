---
title: Upozornění kompilátoru (úroveň 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: 5eccb3c29da612a39f7fcdf4ef25dedb898c8d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198325"
---
# <a name="compiler-warning-level-4-c4565"></a>Upozornění kompilátoru (úroveň 4) C4565

> '*Function*': předefinování; symbol byl dřív deklarovaný pomocí __declspec (*Modifikátor*).

## <a name="remarks"></a>Poznámky

Symbol byl předefinován nebo znovu deklarován a druhá definice nebo deklarace na rozdíl od první definice nebo deklarace neobsahovala modifikátor `__declspec` (*Modifikátor*). Toto upozornění je informativní. Chcete-li toto upozornění opravit, odstraňte jednu z definic.

## <a name="example"></a>Příklad

Následující ukázka generuje C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
