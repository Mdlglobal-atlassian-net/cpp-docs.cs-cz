---
title: appobject (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: e02cedff70ac32f7edfdb92b240269c34befee7e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490937"
---
# <a name="appobject"></a>appobject

Identifikuje třídu typu coclass jako objekt aplikace, který je přidružen k úplné aplikaci. exe, a označuje, že funkce a vlastnosti třídy coclass jsou v této [knihovně typů](../../mfc/automation-clients-using-type-libraries.md)globálně k dispozici.

## <a name="syntax"></a>Syntaxe

```cpp
[appobject]
```

## <a name="remarks"></a>Poznámky

Atribut **appobject** C++ má stejné funkce jako atribut [appobject](/windows/win32/Midl/appobject) MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje jednoduchou definici třídy předchází bloku atributů, který zahrnuje **appobject**:

```cpp
// cpp_attr_ref_appobject.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];

[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]
__interface ICustom {};

[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]
class A : public ICustom {
   int i;
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|`coclass`|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)