---
title: Kompilátor upozornění (úroveň 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 031b32a03d93a51f6fa00041a5b0bdf99e6eacf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456053"
---
# <a name="compiler-warning-level-3-c4373"></a>Kompilátor upozornění (úroveň 3) C4373

> "*funkce*': virtuální funkce přepíše*base_function*", předchozí verze kompilátoru nepřepsala, když se parametry lišily jenom podle kvalifikátory const/volatile

## <a name="remarks"></a>Poznámky

Vaše aplikace obsahuje metodu v odvozené třídě, která přepíše virtuální metodu v základní třídě a parametry v přepsání metody liší pouze [const](../../cpp/const-cpp.md) nebo [volatile](../../cpp/volatile-cpp.md) kvalifikátor z parametry virtuální metody. To znamená, že kompilátor musí mít vazbu funkce odkaz na metodu v některém základní nebo odvozené třídy.

Verze kompilátoru před Visual Studio 2008 vytvořit vazbu funkce na metodu v základní třídě a potom vydat upozornění. Další verze kompilátor Ignorovat `const` nebo `volatile` kvalifikátor, vytvořit vazbu funkce na metodu v odvozené třídě a potom vydat upozornění **C4373**. Toto chování druhá možnost vyhovuje standardu jazyka C++.

## <a name="example"></a>Příklad

Následující příklad kódu vygeneruje upozornění C4373. Chcete-li vyřešit tento problém, můžete provést buď přepsat, použijte stejný kvalifikátory CV jako základní členská funkce, nebo pokud jste nechtěli vytvoříte přepsání, je můžete přidělit funkce v odvozené třídě jiný název.

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

void main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```