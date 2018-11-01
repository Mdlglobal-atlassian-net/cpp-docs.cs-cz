---
title: size_is (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: 95b0e16e5f5d085e526f45e8e98898474fc5a17f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449436"
---
# <a name="sizeis"></a>size_is

Zadejte velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.

## <a name="syntax"></a>Syntaxe

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Parametry

*Výraz*<br/>
Velikost paměti přidělené pro velikosti ukazatele.

## <a name="remarks"></a>Poznámky

**Size_is** C++ atribut má stejné funkce jako [size_is](/windows/desktop/Midl/size-is) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [first_is –](first-is.md) ukázku toho, jak zadat část pole.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Pole v **struktura** nebo **sjednocení**, rozhraní parametr, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|`max_is`|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)