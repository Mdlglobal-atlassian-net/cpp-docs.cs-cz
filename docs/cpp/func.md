---
title: __Func__ | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __func__
dev_langs:
- C++
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d78a249fe5b111c17c29895edcdc3fa5ba2f27a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="func"></a>__Func__

**(C ++ 11)**  Identifikátor předdefinované &#95; &#95;func&#95; &#95; je implicitně definováno jako řetězec, který obsahuje název nekvalifikované a prostým nadřazených funkce. &#95;&#95;Func&#95; &#95; je vyžadováno ve standardní C++ a není rozšíření Microsoft.

## <a name="syntax"></a>Syntaxe

```cpp
__func__
```

## <a name="return-value"></a>Návratová hodnota

Vrátí ukončené hodnotou null const char pole znaků obsahující název funkce.

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

C ++ 11