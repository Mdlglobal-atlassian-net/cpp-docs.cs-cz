---
title: Kompilátor upozornění (úroveň 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 012866e328433ec9511782c26a39265481ff4940
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541181"
---
# <a name="compiler-warning-level-1-c4067"></a>Kompilátor upozornění (úroveň 1) C4067

> neočekávané tokeny direktivě preprocesoru – očekával se nový řádek

## <a name="remarks"></a>Poznámky

Kompilátor najít a ignoruje znaky navíc direktivě preprocesoru. To může způsobovat žádné neočekávané znaky, i když běžných příčin je zapomenutý středník za direktivou. Komentáře nezpůsobí toto upozornění. **/Za** – možnost kompilátoru umožňuje toto upozornění pro další direktivy preprocesoru než výchozí hodnotu.

## <a name="example"></a>Příklad

```cpp
// C4067a.cpp
// compile with: cl /EHsc /DX /W1 /Za C4067a.cpp
#include <iostream>
#include <string> s     // C4067
#if defined(X);         // C4067
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif;                 // C4067 only under /Za
int main()
{
    std::cout << s << std::endl;
}
```

Pokud chcete vyřešit toto upozornění, odstranění zapomenutý znaků nebo jejich přesunutím do blok komentáře. Některé C4067 upozornění, může se zakáže odebráním **/Za** – možnost kompilátoru.

```cpp
// C4067b.cpp
// compile with: cl /EHsc /DX /W1 C4067b.cpp
#include <iostream>
#include <string>
#if defined(X)
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif
int main()
{
    std::cout << s << std::endl;
}
```