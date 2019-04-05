---
title: max_is – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: dca2a3dc18aa3c3e75bbb682ed0b1b90adcd9236
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041306"
---
# <a name="maxis"></a>max_is

Určuje maximální hodnotu pro pole platný index.

## <a name="syntax"></a>Syntaxe

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>Parametry

*výraz*<br/>
Jeden nebo více výrazů jazyka C. Prázdný argument sloty jsou povoleny.

## <a name="remarks"></a>Poznámky

**Max_is –** C++ atribut má stejné funkce jako [max_is –](/windows/desktop/Midl/max-is) atribut MIDL.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Pole v **struktura** nebo **sjednocení**, rozhraní parametr, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|**size_is**|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Příklad

Zobrazit [first_is –](first-is.md) příklad toho, jak zadat část pole.

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)