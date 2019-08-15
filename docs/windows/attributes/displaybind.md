---
title: displaybind (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.displaybind
helpviewer_keywords:
- displaybind attribute
ms.assetid: b3d70396-78e4-43d9-9583-16ddb8c9bb1f
ms.openlocfilehash: 168db224e7b15656308259f9507e1079744f1a73
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490889"
---
# <a name="displaybind"></a>displaybind

Označuje vlastnost, která se má uživateli zobrazit jako vazba.

## <a name="syntax"></a>Syntaxe

```cpp
[displaybind]
```

## <a name="remarks"></a>Poznámky

Atribut **displaybind** C++ má stejné funkce jako atribut [displaybind](/windows/win32/Midl/displaybind) MIDL.

## <a name="example"></a>Příklad

Příklad použití **displaybind**najdete v příkladu s možností [vazby](bindable.md) .

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
[defaultbind](defaultbind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)