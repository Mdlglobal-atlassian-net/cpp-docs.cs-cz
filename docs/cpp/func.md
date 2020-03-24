---
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: 8e94caffe120c325478d8b4f24c1915a516d69f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179819"
---
# <a name="__func__"></a>__func__

**(C++ 11)** Předdefinovaný identifikátor &#95; &#95;Func&#95; &#95; je implicitně definovaný jako řetězec, který obsahuje nekvalifikovaný a nezobrazený název uzavírací funkce. &#95;&#95;funkce&#95; &#95; Func je určena C++ standardem a není rozšířením společnosti Microsoft.

## <a name="syntax"></a>Syntaxe

```cpp
__func__
```

## <a name="return-value"></a>Návratová hodnota

Vrátí pole konstanty const zakončené znakem null, které obsahuje název funkce.

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
