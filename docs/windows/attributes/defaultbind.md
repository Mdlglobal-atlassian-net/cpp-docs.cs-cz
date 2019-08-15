---
title: defaultbind (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultbind
helpviewer_keywords:
- defaultbind attribute
ms.assetid: b20a8437-24e6-4b6d-a2df-09fe5e1006e0
ms.openlocfilehash: a2f612c4869a62a84a6a2af99057ced365f875f2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490994"
---
# <a name="defaultbind"></a>defaultbind

Označuje jedinou vlastnost s možností vazby, která nejlépe představuje objekt.

## <a name="syntax"></a>Syntaxe

```cpp
[defaultbind]
```

## <a name="remarks"></a>Poznámky

Atribut **defaultbind** C++ má stejné funkce jako atribut [defaultbind](/windows/win32/Midl/defaultbind) MIDL.

## <a name="example"></a>Příklad

Příklad použití **defaultbind**najdete v příkladu s možností [vazby](bindable.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy datového členu](data-member-attributes.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)