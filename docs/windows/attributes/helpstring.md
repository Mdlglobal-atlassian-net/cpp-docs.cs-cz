---
title: HelpString (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 47a07ee94ad774bde46dce00ea46612fae3a4eca
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490878"
---
# <a name="helpstring"></a>helpstring

Určuje řetězec znaků, který se používá k popisu prvku, na který se vztahuje.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>Parametry

*string*<br/>
Text řetězce v nápovědě

## <a name="remarks"></a>Poznámky

Atribut **HelpString** C++ má stejné funkce jako atribut [HelpString](/windows/win32/Midl/helpstring) MIDL.

## <a name="example"></a>Příklad

Příklad použití **HelpString**najdete v příkladu pro [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**rozhraní**, **typedef**, **Třída**, metoda, vlastnost|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)