---
title: výchozí (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: b789f82f4b5a09b86d72dfde5d783665cf2e918a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167183"
---
# <a name="default-c"></a>default (C++)

Indikuje, že vlastní nebo odesílající pole definované v rámci třídy typu coclass představuje výchozí rozhraní programovatelnosti.

## <a name="syntax"></a>Syntaxe

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Parametry

*rozhraní interface1*<br/>
Výchozí rozhraní, které bude zpřístupněno pro skriptovací prostředí, která vytvoří objekt na základě třídy definované s **výchozím** atributem.

Pokud není zadáno žádné výchozí rozhraní, jako výchozí se použije první výskyt nezdrojového rozhraní.

*interface2*<br/>
Volitelné Výchozí zdrojové rozhraní. Musíte také zadat toto rozhraní se [zdrojovým](source-cpp.md) atributem.

Pokud není zadané žádné výchozí zdrojové rozhraní, použije se jako výchozí první zdrojové rozhraní.

## <a name="remarks"></a>Poznámky

**Výchozí** C++ atribut má stejné funkce jako [výchozí](/windows/win32/Midl/default) atribut MIDL. **Výchozí** atribut se používá také s atributem [case](case-cpp.md) .

## <a name="example"></a>Příklad

Následující kód ukazuje, jak se používá **Výchozí hodnota** v definici třídy typu coclass k určení `ICustomDispatch` jako výchozího rozhraní programovatelnosti:

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

[Zdrojový](source-cpp.md) atribut má také příklad, jak použít **výchozí**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**, datový člen|
|**REPEATABLE**|Ne|
|**Požadované atributy**|**Coclass – třída** (při použití pro **třídu** nebo **strukturu**)|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[coclass](coclass.md)
