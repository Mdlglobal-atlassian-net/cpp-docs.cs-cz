---
title: __Func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: eecd3efea6239c92a8bc81c0ed13a9563e5b87d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154292"
---
# <a name="func"></a>__Func__

**(C ++ 11)**  Předdefinovaný identifikátor &#95; &#95;func&#95; &#95; je implicitně definovaný jako řetězec, který obsahuje nekvalifikovaný, prostý název nadřazené funkce. &#95;&#95;Func&#95; &#95; je vyžadováno podle standardu jazyka C++ a není rozšířením společnosti Microsoft.

## <a name="syntax"></a>Syntaxe

```cpp
__func__
```

## <a name="return-value"></a>Návratová hodnota

Vrátí zakončený hodnotou null const char pole znaků, který obsahuje název funkce.

## <a name="example"></a>Příklad

```cpp
#include <string>
#include <iostream>

namespace Test
{
    struct Foo
    {
        static void DoSomething(int i, std::string s)
        {
           std::cout << __func__ << std::endl; // Output: DoSomething
        }
    };
}

int main()
{
    Test::Foo::DoSomething(42, "Hello");

    return 0;
}
```

## <a name="requirements"></a>Požadavky

C++11