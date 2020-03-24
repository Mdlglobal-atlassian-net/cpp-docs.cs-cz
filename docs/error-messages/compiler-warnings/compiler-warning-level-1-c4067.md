---
title: Upozornění kompilátoru (úroveň 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 8bdd16f5c3182e4217e195475bdb4a9a0f60fa6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164115"
---
# <a name="compiler-warning-level-1-c4067"></a>Upozornění kompilátoru (úroveň 1) C4067

> neočekávané tokeny po direktivě preprocesoru – očekával se nový řádek.

## <a name="remarks"></a>Poznámky

Kompilátor nalezl a ignoroval nadbytečné znaky po direktivě preprocesoru. To může být způsobeno jakýmkoli neočekávaným znakem, i když běžnou příčinou je osamocený středník za direktivou. Komentáře nezpůsobují toto upozornění. Možnost kompilátoru **/za** umožňuje toto upozornění pro více direktiv preprocesoru, než je výchozí nastavení.

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

Chcete-li vyřešit toto upozornění, odstraňte osamocené znaky nebo je přesuňte do bloku komentáře. Některá upozornění C4067 mohou být zakázána odebráním možnosti kompilátoru **/za** .

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
