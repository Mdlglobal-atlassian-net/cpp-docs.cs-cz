---
title: Chyba kompilátoru C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: 534be9e3873276313335ca921264be92c9259b93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165740"
---
# <a name="compiler-error-c3768"></a>Chyba kompilátoru C3768

> nejde převzít adresu virtuální funkce vararg v čistě spravovaném kódu.

## <a name="remarks"></a>Poznámky

Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

Při kompilaci s možností **/clr: Pure**nelze přebírat adresu funkce Virtual `vararg`.

## <a name="example"></a>Příklad

Následující ukázka generuje C3768:

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```
