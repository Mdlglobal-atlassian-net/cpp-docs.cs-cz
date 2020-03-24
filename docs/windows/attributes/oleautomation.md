---
title: oleautomation (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 201916eeb235d48473d21188da42d19cafb93bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214655"
---
# <a name="oleautomation"></a>oleautomation

Označuje, že rozhraní je kompatibilní s automatizací.

## <a name="syntax"></a>Syntaxe

```cpp
[oleautomation]
```

## <a name="remarks"></a>Poznámky

Atribut **oleautomation** C++ má stejné funkce jako atribut [oleautomation](/windows/win32/Midl/oleautomation) MIDL.

## <a name="example"></a>Příklad

Ukázkové použití **oleautomation**najdete v příkladech pro [DefaultValue](defaultvalue.md) a [nerozšiřitelné](nonextensible.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**interface**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|**dispinterface**|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)
