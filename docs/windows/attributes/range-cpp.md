---
title: Range (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: d1221192eb1813d759f293fe5555d7aaa5b367ab
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514138"
---
# <a name="range-c"></a>range (C++)

Určuje rozsah přípustných hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastaveny v době běhu.

## <a name="syntax"></a>Syntaxe

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>Parametry

*slab*<br/>
Nízká hodnota rozsahu.

*maximální*<br/>
Vysoká hodnota rozsahu.

## <a name="remarks"></a>Poznámky

Atribut **Range** C++ má stejné funkce jako atribut [Range](/windows/win32/Midl/range) MIDL.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_range.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Interface – metoda, parametr rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[Atributy datového členu](data-member-attributes.md)