---
title: ID (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 6f1d1d2b9d147e8b33b3b5fae629e0805971bb71
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501407"
---
# <a name="id"></a>id

Určuje parametr *DISPID* pro členskou funkci (buď vlastnost nebo metodu, v rozhraní nebo odesílajícím rozhraní).

## <a name="syntax"></a>Syntaxe

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Parametry

*dispid*<br/>
ID odeslání pro metodu rozhraní.

## <a name="remarks"></a>Poznámky

Atribut **ID** C++ má stejné funkce jako atribut [ID](/windows/win32/Midl/id) MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad, jak [vytvořit vazby](bindable.md) pro příklad použití **ID**.

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
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)