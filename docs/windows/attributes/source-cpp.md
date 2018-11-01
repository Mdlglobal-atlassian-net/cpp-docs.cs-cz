---
title: zdroj (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: 59ed66acbbd6ef876e6052767dc5a5243d4b8dd6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476524"
---
# <a name="source-c"></a>source (C++)

Třídy určuje rozhraní zdrojového objektu modelu COM pro spojovací body. Na vlastnost nebo metoda označuje, že členu vrátí objekt nebo VARIANTU, která je zdrojem událostí.

## <a name="syntax"></a>Syntaxe

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>Parametry

*Rozhraní*<br/>
Jedno nebo více rozhraní, zadejte, pokud použijete zdrojové atribut třídy. Tento parametr se nepoužívá při použití u zdroj vlastnosti nebo metody.

## <a name="remarks"></a>Poznámky

**Zdroj** C++ atribut má stejné funkce jako [zdroj](/windows/desktop/Midl/source) atribut MIDL.

Můžete použít [výchozí](default-cpp.md) atributy výchozím zdrojovém rozhraní objektu.

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **struktura**, **rozhraní**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|`coclass` (při použití u třídy nebo struktury)|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[coclass](coclass.md)