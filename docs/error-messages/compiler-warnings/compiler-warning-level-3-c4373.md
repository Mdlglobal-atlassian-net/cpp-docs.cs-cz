---
title: Upozornění kompilátoru (úroveň 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 5891d4679b74695f187fb50bb24fe941882fdcc7
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518345"
---
# <a name="compiler-warning-level-3-c4373"></a>Upozornění kompilátoru (úroveň 3) C4373

> '*Function*': virtuální funkce Přepisuje*base_function*', předchozí verze kompilátoru se nepřepsaly, když se parametry liší pouze kvalifikátory const/volatile.

## <a name="remarks"></a>Poznámky

Vaše aplikace obsahuje metodu v odvozené třídě, která přepisuje virtuální metodu v základní třídě a parametry v přepsání metody se liší pouze kvalifikátorem [const](../../cpp/const-cpp.md) nebo [volatile](../../cpp/volatile-cpp.md) z parametrů virtuální metody. To znamená, že kompilátor musí navazovat odkaz na funkci v základní nebo odvozené třídě.

Verze kompilátoru před verzí sady Visual Studio 2008 sváže funkci s metodou v základní třídě a pak vydá zprávu upozornění. Další verze kompilátoru ignorují kvalifikátor `const` nebo `volatile`, sváže funkci s metodou v odvozené třídě a pak vystaví upozornění **C4373**. Toto druhé chování je v C++ souladu se standardem.

## <a name="example"></a>Příklad

Následující příklad kódu generuje upozornění C4373. Chcete-li vyřešit tento problém, můžete buď přepsání použít stejné kvalifikátory CV jako základní členskou funkci, nebo pokud jste nechtěli vytvořit přepsání, můžete funkci v odvozené třídě poskytnout jiný název.

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

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
