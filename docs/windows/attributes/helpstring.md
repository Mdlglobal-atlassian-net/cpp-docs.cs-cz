---
title: helpstring (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 623b2c7fb4ce7c3e5de87d21f012d008720fdee2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022202"
---
# <a name="helpstring"></a>helpstring

Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>Parametry

*string*<br/>
Textový řetězec nápovědy.

## <a name="remarks"></a>Poznámky

**Helpstring** C++ atribut má stejné funkce jako [helpstring](/windows/desktop/Midl/helpstring) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [defaultvalue](defaultvalue.md) příklad, jak používat **helpstring**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**, **typedef**, **třída**, metoda, vlastnost|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádný|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)