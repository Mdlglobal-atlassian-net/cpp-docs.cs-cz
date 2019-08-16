---
title: length_is (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.length_is
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
ms.openlocfilehash: 4f4bfe233e3228c50aee734de4ad979c38a55fda
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514522"
---
# <a name="length_is"></a>length_is

Určuje počet prvků pole, které mají být přeneseny.

## <a name="syntax"></a>Syntaxe

```cpp
[ length_is("expression") ]
```

### <a name="parameters"></a>Parametry

*vyjádření*<br/>
Jeden nebo více výrazů jazyka C. Prázdné sloty argumentů jsou povoleny.

## <a name="remarks"></a>Poznámky

Atribut **length_is** C++ má stejné funkce jako atribut [length_is](/windows/win32/Midl/length-is) MIDL.

## <a name="example"></a>Příklad

Příklad určení oddílu pole naleznete v tématu [first_is](first-is.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Pole v **struktuře** nebo **sjednocení**, parametr rozhraní, metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[last_is](last-is.md)<br/>
[size_is](size-is.md)