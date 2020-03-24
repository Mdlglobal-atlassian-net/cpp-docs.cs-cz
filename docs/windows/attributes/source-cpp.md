---
title: Source (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: 5f961513b948c3195aea864d97313ac09e97344e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166221"
---
# <a name="source-c"></a>source (C++)

U třídy určuje zdrojové rozhraní objektu COM pro body připojení. U vlastnosti nebo metody označuje, že člen vrací objekt nebo VARIANTu, který je zdrojem událostí.

## <a name="syntax"></a>Syntaxe

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>Parametry

*Interfaces*<br/>
Jedno nebo více rozhraní, které zadáte při použití atributu source na třídu. Tento parametr se nepoužívá, pokud je zdroj aplikován na vlastnost nebo metodu.

## <a name="remarks"></a>Poznámky

**Zdrojový** C++ atribut má stejné funkce jako [zdrojový](/windows/win32/Midl/source) atribut MIDL.

[Výchozí](default-cpp.md) atribut můžete použít k určení výchozího zdrojového rozhraní objektu.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**, **rozhraní**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|`coclass` (při použití u třídy nebo struktury)|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[coclass](coclass.md)
