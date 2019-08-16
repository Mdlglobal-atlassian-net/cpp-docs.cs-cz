---
title: propput (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: 5e10edba60832112a9023f796be56d88afd52042
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514191"
---
# <a name="propput"></a>propput

Určuje funkci nastavení vlastnosti.

## <a name="syntax"></a>Syntaxe

```cpp
[propput]
```

## <a name="remarks"></a>Poznámky

Atribut **propput** C++ má stejné funkce jako atribut [propput](/windows/win32/Midl/propput) MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [vytvoření vazby](bindable.md) pro ukázkové použití **propput**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Metoda|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|`propget`, `propputref`|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)