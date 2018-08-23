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
ms.openlocfilehash: 921510a548f638f06953f95abe79f825e57e179b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586855"
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

*Rozhraní*  
Jedno nebo více rozhraní, zadejte, pokud použijete zdrojové atribut třídy. Tento parametr se nepoužívá při použití u zdroj vlastnosti nebo metody.

## <a name="remarks"></a>Poznámky

**Zdroj** C++ atribut má stejné funkce jako [zdroj](http://msdn.microsoft.com/library/windows/desktop/aa367166) atribut MIDL.

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

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy třídy](../windows/class-attributes.md)  
[Atributy metody](../windows/method-attributes.md)  
[coclass](../windows/coclass.md)  