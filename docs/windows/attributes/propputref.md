---
title: propputref (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: a9c4413e9bb8c7faa332bb842700dfcf84d6666a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166429"
---
# <a name="propputref"></a>propputref

Určuje funkci nastavení vlastnosti, která používá odkaz namísto hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
[propputref]
```

## <a name="remarks"></a>Poznámky

Atribut **propputref** C++ má stejné funkce jako atribut [propputref](/windows/win32/Midl/propputref) MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [vytvoření vazby](bindable.md) pro ukázkové použití **propputref**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Metoda|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|`propget`, `propput`|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)
