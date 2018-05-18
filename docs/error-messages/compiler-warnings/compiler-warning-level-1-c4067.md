---
title: Kompilátoru (úroveň 1) upozornění C4067 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4067
dev_langs:
- C++
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee6b48327e8754f9388e0df8f43009a5be70c97
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="compiler-warning-level-1-c4067"></a>C4067 kompilátoru upozornění (úroveň 1)

> neočekávané tokeny následující direktivy preprocesoru - očekává nový řádek

## <a name="remarks"></a>Poznámky

Kompilátor najít a další znaky následující direktivy preprocesoru ignorovány. Když obvyklou příčinou je stray středníkem po direktiva to může být způsobeno znaky neočekávané. Komentáře nezpůsobí toto upozornění. **/Za** – možnost kompilátoru umožňuje toto upozornění pro další preprocesor – direktivy než výchozí nastavení.

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

Toto upozornění vyřešit, odstraňte stray znaky nebo přesuňte je do blok komentáře. Některé C4067 upozornění mohou být zakázány odebráním **/Za** – možnost kompilátoru.

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