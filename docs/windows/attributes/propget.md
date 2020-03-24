---
title: propget (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: d2c0ebab1630634ddd4fc81e7c9c8364f7fad46f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166456"
---
# <a name="propget"></a>propget

Určuje funkci přistupujícího objektu vlastnosti.

## <a name="syntax"></a>Syntaxe

```cpp
[propget]
```

## <a name="remarks"></a>Poznámky

Atribut **propget** C++ má stejné funkce jako atribut [propget](/windows/win32/Midl/propget) MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [vytvoření vazby](bindable.md) pro ukázkové použití **propget**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Metoda|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|`propput`, `propputref`|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)
