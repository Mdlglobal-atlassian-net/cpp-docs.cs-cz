---
title: Výchozí (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: c6448b00fef50a7654816a2c39af2943db12d314
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148078"
---
# <a name="default-c"></a>default (C++)

Označuje, že vlastní nebo dispinterface definované v rámci coclass představuje výchozí programovatelnosti rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Parametry

*interface1*<br/>
Výchozí rozhraní, která bude k dispozici pro vytvoření objektu skriptovací prostředí na základě třídy definované **výchozí** atribut.

Pokud není zadána žádná výchozí rozhraní, první výskyt nonsource rozhraní se používá jako výchozí.

*interface2*<br/>
(Volitelné) Výchozím zdrojovém rozhraní. Toto rozhraní se musíte zadat také [zdroj](source-cpp.md) atribut.

Pokud není zadána žádná výchozí zdrojové rozhraní, první zdrojové rozhraní se používá jako výchozí.

## <a name="remarks"></a>Poznámky

**Výchozí** C++ atribut má stejné funkce jako [výchozí](/windows/desktop/Midl/default) atribut MIDL. **Výchozí** atribut je použit také s [případ](case-cpp.md) atribut.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak **výchozí** na definici třídy coclass slouží k určení `ICustomDispatch` jako výchozí programovatelnosti rozhraní:

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

[Zdroj](source-cpp.md) atribut obsahuje také příklad, jak používat **výchozí**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **struktura**, datový člen|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|**coclass** (při použití u **třídy** nebo **struktura**)|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[coclass](coclass.md)