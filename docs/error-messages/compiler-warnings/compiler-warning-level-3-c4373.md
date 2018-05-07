---
title: Kompilátoru (úroveň 3) upozornění C4373 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4373
dev_langs:
- C++
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fda965fe80fc26731cde7be5a71540e6454a7360
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4373"></a>C4373 kompilátoru upozornění (úroveň 3)

> '*funkce*': virtuální funkce přepsání*base_function*', předchozí verze kompilátoru přepsat při parametry pouze podle const nebo volatile kvalifikátory lišil.

## <a name="remarks"></a>Poznámky

Vaše aplikace obsahuje metodu v odvozené třídě, který přepíše virtuální metodu v základní třídě a parametry v metodě přepsání lišit pouze [const](../../cpp/const-cpp.md) nebo [volatile](../../cpp/volatile-cpp.md) kvalifikátor z parametry virtuální metody. To znamená, kompilátor musí vytvořit vazbu funkce odkaz na metodu buď základní nebo odvozené třídy.

Verze kompilátoru před Visual Studio 2008 vazbu funkce metodu v základní třídě a potom zpráva s upozorněním. Další verze kompilátoru Ignorovat `const` nebo `volatile` kvalifikátor, vazbu funkce metodu v odvozené třídě a potom vydat varování **C4373**. Toto chování pozdější splňuje C++ standard.

## <a name="example"></a>Příklad

Následující příklad kódu generuje upozornění C4373. Chcete-li vyřešit tento problém, můžete je nastavit přepsání použít stejné odchylka nákladů kvalifikátory jako funkce základní člen nebo pokud jste nechtěli vytvořte přepsání, které poskytnete funkce v odvozené třídě jiný název.

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