---
title: max_is (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: b4931962febb1e68701aa3fe271e08f3aa8d9238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166754"
---
# <a name="max_is"></a>max_is

Určuje maximální hodnotu pro platný index pole.

## <a name="syntax"></a>Syntaxe

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>Parametry

*vyjádření*<br/>
Jeden nebo více výrazů jazyka C. Prázdné sloty argumentů jsou povoleny.

## <a name="remarks"></a>Poznámky

Atribut **max_is** C++ má stejné funkce jako atribut [max_is](/windows/win32/Midl/max-is) MIDL.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Pole v **struktuře** nebo **sjednocení**, parametr rozhraní, metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|**size_is**|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Příklad

Příklad určení oddílu pole naleznete v tématu [first_is](first-is.md) .

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
