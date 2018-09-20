---
title: zdroj (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.source
dev_langs:
- C++
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d3f4cacd380a86138095b0f8b3bf67f860d45cda
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390536"
---
# <a name="source-c"></a>source (C++)

Třídy určuje rozhraní zdrojového objektu modelu COM pro spojovací body. Na vlastnost nebo metoda označuje, že členu vrátí objekt nebo VARIANTU, která je zdrojem událostí.

## <a name="syntax"></a>Syntaxe

```cpp
[ source(
   interfaces
) ]
```

### <a name="parameters"></a>Parametry

*Rozhraní*<br/>
Jedno nebo více rozhraní, zadejte, pokud použijete zdrojové atribut třídy. Tento parametr se nepoužívá při použití u zdroj vlastnosti nebo metody.

## <a name="remarks"></a>Poznámky

**Zdroj** C++ atribut má stejné funkce jako [zdroj](/windows/desktop/Midl/source) atribut MIDL.

Můžete použít [výchozí](../windows/default-cpp.md) atributy výchozím zdrojovém rozhraní objektu.

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

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Atributy třídy](../windows/class-attributes.md)<br/>
[Atributy metody](../windows/method-attributes.md)<br/>
[coclass](../windows/coclass.md)  