---
title: bad_weak_ptr – třída
ms.date: 11/04/2016
f1_keywords:
- memory/std::bad_weak_ptr
helpviewer_keywords:
- bad_weak_ptr
- bad_weak_ptr class
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
ms.openlocfilehash: e1d536eed6727a5d1e828d358aa6b64521d748b8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454270"
---
# <a name="badweakptr-class"></a>bad_weak_ptr – třída

Nahlásí chybnou výjimku weak_ptr.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_weak_ptr : public std::exception
{
    bad_weak_ptr();
    const char *what() throw();
};
```

## <a name="remarks"></a>Poznámky

Třída popisuje výjimku, kterou lze vyvolat z konstruktoru [třídy shared_ptr](../standard-library/shared-ptr-class.md) , který přebírá argument typu [třídy weak_ptr](../standard-library/weak-ptr-class.md). `what` Vrátí`"bad_weak_ptr"`členské funkce.

## <a name="example"></a>Příklad

```cpp
// std__memory__bad_weak_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int);
        wp = sp;
    }

    try
    {
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired
    }
    catch (const std::bad_weak_ptr&)
    {
        std::cout << "bad weak pointer" << std::endl;
    }
    catch (...)
    {
        std::cout << "unknown exception" << std::endl;
    }

    return (0);
}
```

```Output
bad weak pointer
```

## <a name="see-also"></a>Viz také:

[weak_ptr – třída](../standard-library/weak-ptr-class.md)
