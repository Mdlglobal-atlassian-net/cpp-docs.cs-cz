---
title: implements_category – (C++ atributů COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: beca804fae8d6e82b4664102b39d76a23e66ca59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409405"
---
# <a name="implementscategory"></a>implements_category

Určuje součást kategorie implementované cílové třídy.

## <a name="syntax"></a>Syntaxe

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>Parametry

*implements_category*<br/>
ID kategorie implementovaná.

## <a name="remarks"></a>Poznámky

**Implements_category –** C++ atribut určuje kategorie komponenty implementované cílové třídy. Je to vytváření map kategorie a přidáním samostatných položek, které jsou určené **implements_category –** atribut. Další informace najdete v tématu [co jsou komponenty kategorie a jak provádět jejich práce?](https://msdn.microsoft.com/library/windows/desktop/ms694322).

Tento atribut vyžaduje, aby [coclass](coclass.md), [progid](progid.md), nebo [vi_progid –](vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít u stejného elementu. Pokud se používá jakékoli jeden atribut, další dvě automaticky použity. Například pokud `progid` se použije, `vi_progid` a `coclass` jsou použita také.

## <a name="example"></a>Příklad

Následující kód určuje, že následující objekt implementuje `Control` kategorie.

```cpp
// cpp_attr_ref_implements_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLib")];
[ coclass, implements_category("CATID_Control"),
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]
class CMyClass {};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ano|
|**Vyžadované atributy**|Jeden z následujících: `coclass`, `progid`, nebo `vi_progid`|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[COM – atributy](com-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)