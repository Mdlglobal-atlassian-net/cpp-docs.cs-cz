---
title: requires_category (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: 19a454a8bfc959d7d97959d765dbf68d0f766ca1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214549"
---
# <a name="requires_category"></a>requires_category

Určuje požadované kategorie součásti cílové třídy.

## <a name="syntax"></a>Syntaxe

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>Parametry

*requires_category*<br/>
ID požadované kategorie

## <a name="remarks"></a>Poznámky

Atribut **requires_category** C++ určuje kategorie komponent vyžadované cílovou třídou. Další informace najdete v tématu [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category).

Tento atribut vyžaduje, aby atribut [Coclass](coclass.md), [ProgID](progid.md)nebo [vi_progid](vi-progid.md) (nebo jiný atribut, který implikuje jednu z nich) byl také použit pro stejný prvek.

## <a name="example"></a>Příklad

Následující kód vyžaduje, aby objekt implementoval kategorii ovládacího prvku.

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
class CMyClass {};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Jednu nebo více následujících možností: `coclass`, `progid`nebo `vi_progid`.|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[COM – atributy](com-attributes.md)<br/>
[implements_category](implements-category.md)
