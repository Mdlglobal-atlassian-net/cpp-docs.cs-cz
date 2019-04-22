---
title: __interface
ms.date: 11/04/2016
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 1ec3a1d2cddbf8dbbb248a7366d5d56dd95ad074
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768312"
---
# <a name="interface"></a>__interface

**Microsoft Specific**

Rozhraní jazyka Visual C++ lze definovat takto:

- Může dědit z žádného nebo z více základních rozhraní.

- Nemůže dědit ze základní třídy.

- Může obsahovat pouze čistě virtuální veřejné metody.

- Nemůže obsahovat operátory, konstruktory a destruktory.

- Nemůže obsahovat statické metody.

- Nemůže obsahovat datové členy. Vlastnosti jsou povoleny.

## <a name="syntax"></a>Syntaxe

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>Poznámky

A C++ [třídy](../cpp/class-cpp.md) nebo [struktura](../cpp/struct-cpp.md) možná implementace s Tato pravidla, ale **__interface** je vynucuje.

Následuje příklad ukázkové definice rozhraní:

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

Informace o spravovaných rozhraních naleznete v tématu [třída rozhraní](../extensions/interface-class-cpp-component-extensions.md).

Není nutné explicitně určit funkce `CommitX` a `get_X` jako čistě virtuální. Ekvivalentní deklarace první funkce by byla:

```cpp
virtual HRESULT CommitX() = 0;
```

**__interface** znamená, [novtable](../cpp/novtable.md) **__declspec** modifikátor.

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití vlastností deklarovaných v rozhraní.

```cpp
// deriv_interface.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <string.h>
#include <comdef.h>
#include <stdio.h>

[module(name="test")];

[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]
__interface IFace {
   [ id(0) ] int int_data;
   [ id(5) ] BSTR bstr_data;
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class MyClass : public IFace {
private:
    int m_i;
    BSTR m_bstr;

public:
    MyClass()
    {
        m_i = 0;
        m_bstr = 0;
    }

    ~MyClass()
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
    }

    int get_int_data()
    {
        return m_i;
    }

    void put_int_data(int _i)
    {
        m_i = _i;
    }

    BSTR get_bstr_data()
    {
        BSTR bstr = ::SysAllocString(m_bstr);
        return bstr;
    }

    void put_bstr_data(BSTR bstr)
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
        m_bstr = ::SysAllocString(bstr);
    }
};

int main()
{
    _bstr_t bstr("Testing");
    CoInitialize(NULL);
    CComObject<MyClass>* p;
    CComObject<MyClass>::CreateInstance(&p);
    p->int_data = 100;
    printf_s("p->int_data = %d\n", p->int_data);
    p->bstr_data = bstr;
    printf_s("bstr_data = %S\n", p->bstr_data);
}
```

```Output
p->int_data = 100
bstr_data = Testing
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Atributy rozhraní](../windows/attributes/interface-attributes.md)