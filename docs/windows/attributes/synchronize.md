---
title: Synchronize (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: a0f4702de4cfde8586cc573f9ff5a6195984d207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214510"
---
# <a name="synchronize"></a>synchronize

Synchronizuje přístup k cílové metodě.

## <a name="syntax"></a>Syntaxe

```cpp
[synchronize]
```

## <a name="remarks"></a>Poznámky

Atribut **Synchronize** C++ implementuje podporu pro synchronizaci cílové metody objektu. Synchronizace umožňuje více objektům použít společný prostředek (například metodu třídy) řízením přístupu k cílové metodě.

Kód vložený tímto atributem volá správnou metodu `Lock` (určenou modelem vláken) na začátku cílové metody. Když je metoda ukončena, `Unlock` je automaticky volána. Další informace o těchto funkcích naleznete v tématu [CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

Tento atribut vyžaduje, aby atribut [Coclass](coclass.md), [ProgID](progid.md)nebo [vi_progid](vi-progid.md) (nebo jiný atribut, který implikuje jednu z nich) byl také použit pro stejný prvek. Je-li použit libovolný atribut, budou automaticky použity ostatní dva. Například pokud je použita `progid`, jsou použita také `vi_progid` a `coclass`.

## <a name="example"></a>Příklad

Následující kód poskytuje synchronizaci pro metodu `UpdateBalance` objektu `CMyClass`.

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
threading(both),
vi_progid("MyProject.MyClass"),
progid("MyProject.MyClass.1"),
uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Třída – metoda|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Jednu nebo více následujících možností: `coclass`, `progid`nebo `vi_progid`.|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[COM – atributy](com-attributes.md)
