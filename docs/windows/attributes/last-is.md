---
title: last_is (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.last_is
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
ms.openlocfilehash: 4745d4eb59fd2adb79937b34184081dbbd0814fb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514519"
---
# <a name="last_is"></a>last_is

Určuje index posledního elementu pole, který se má přenést.

## <a name="syntax"></a>Syntaxe

```cpp
[ last_is("expression") ]
```

### <a name="parameters"></a>Parametry

*vyjádření*<br/>
Jeden nebo více výrazů jazyka C. Prázdné sloty argumentů jsou povoleny.

## <a name="remarks"></a>Poznámky

Atribut **last_is** C++ má stejné funkce jako atribut [last_is](/windows/win32/Midl/last-is) MIDL.

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
[length_is](length-is.md)<br/>
[size_is](size-is.md)