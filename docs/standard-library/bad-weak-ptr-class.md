---
title: bad_weak_ptr – třída
ms.date: 11/04/2016
f1_keywords:
- memory/std::bad_weak_ptr
helpviewer_keywords:
- bad_weak_ptr
- bad_weak_ptr class
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
ms.openlocfilehash: 78438ef3378e5002396eecb32b9b7a76d5b50325
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492909"
---
# <a name="badweakptr-class"></a>bad_weak_ptr – třída

Nahlásí chybnou výjimku weak_ptr.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_weak_ptr : public std::exception
{
public:
    bad_weak_ptr();
    const char *what() throw();
};
```

## <a name="remarks"></a>Poznámky

Tato třída popisuje výjimku, která mohou být vyvolány z [shared_ptr – třída](../standard-library/shared-ptr-class.md) konstruktor, který přebírá argument typu [weak_ptr – třída](../standard-library/weak-ptr-class.md). Členská funkce `what` vrátí `"bad_weak_ptr"`.

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

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[weak_ptr – třída](../standard-library/weak-ptr-class.md)<br/>
