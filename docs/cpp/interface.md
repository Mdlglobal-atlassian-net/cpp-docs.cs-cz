---
title: __interface
ms.date: 05/07/2019
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 9b265dcbaca9f8fa836795cca990804371813647
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178208"
---
# <a name="__interface"></a>__interface

**Specifické pro společnost Microsoft**

Rozhraní společnosti C++ Microsoft lze definovat následujícím způsobem:

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

Pomocí těchto pravidel lze implementovat [třídu](../cpp/class-cpp.md) nebo strukturu, ale **__interface** je vynutila. [struct](../cpp/struct-cpp.md) C++

Následuje příklad ukázkové definice rozhraní:

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

Informace o spravovaných rozhraních naleznete v tématu [Třída rozhraní](../extensions/interface-class-cpp-component-extensions.md).

Není nutné explicitně určit funkce `CommitX` a `get_X` jako čistě virtuální. Ekvivalentní deklarace první funkce by byla:

```cpp
virtual HRESULT CommitX() = 0;
```

**__interface** implikuje modifikátor **__declspecu** [vtable](../cpp/novtable.md) .

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Atributy rozhraní](../windows/attributes/interface-attributes.md)
