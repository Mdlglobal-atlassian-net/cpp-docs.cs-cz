---
title: __Func__ | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __func__
dev_langs:
- C++
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
caps.latest.revision: 3
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ddb92e84545de175734550eca8911590fa1d539
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="func"></a>__Func__

**(C ++ 11)**  Identifikátor předdefinované &#95; &#95; func &#95; &#95; je implicitně definováno jako řetězec, který obsahuje název nekvalifikované a prostým nadřazených funkce. &#95; &#95; func &#95; &#95; je vyžadováno ve standardní C++ a není rozšíření Microsoft.

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