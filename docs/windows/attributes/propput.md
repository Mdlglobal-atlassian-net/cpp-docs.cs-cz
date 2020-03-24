---
title: propput (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: 8817d0042c3055b5bbf9b111e6f02b9d9a4c152c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166442"
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

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)
