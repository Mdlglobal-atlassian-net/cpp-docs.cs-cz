---
title: Upozornění kompilátoru (úroveň 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 0788824dd4180476d81d9682f99fb95883b8c4f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198338"
---
# <a name="compiler-warning-level-4-c4559"></a>Upozornění kompilátoru (úroveň 4) C4559

> '*Function*': předefinování; funkce získává __declspec (*Modifikátor*).

## <a name="remarks"></a>Poznámky

Funkce byla předefinována nebo znovu deklarována a druhá definice nebo deklarace přidala modifikátor **__declspec** (*Modifikátor*). Toto upozornění je informativní. Chcete-li toto upozornění opravit, odstraňte jednu z definic.

## <a name="example"></a>Příklad

Následující ukázka generuje C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
