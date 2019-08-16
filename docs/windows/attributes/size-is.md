---
title: size_is (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: 504f1bf72b8ffa15e8df50bb00c86ef909688f1e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514040"
---
# <a name="size_is"></a>size_is

Určete velikost paměti přidělené pro velikosti ukazatelů, nastavte velikosti ukazatelů na velikost ukazatelů a jedno nebo multidimenzionální pole.

## <a name="syntax"></a>Syntaxe

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Parametry

*vyjádření*<br/>
Velikost paměti přidělené pro velikosti ukazatelů.

## <a name="remarks"></a>Poznámky

Atribut **size_is** C++ má stejné funkce jako atribut [size_is](/windows/win32/Midl/size-is) MIDL.

## <a name="example"></a>Příklad

Ukázku, jak určit oddíl pole, najdete v příkladu pro [first_is](first-is.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Pole v **struktuře** nebo **sjednocení**, parametr rozhraní, metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|`max_is`|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)