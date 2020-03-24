---
title: Public (C++ atributy) (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.public
helpviewer_keywords:
- public attribute
ms.assetid: c42e1fd5-6cb1-48fe-8a03-95f2a2e0137c
ms.openlocfilehash: 6912117ad05d6b608c45425ebec27cd49c0e5dc4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214704"
---
# <a name="public-c-attributes"></a>public (atributy C++)

Zajistí, že definice typedef přejde do knihovny typů i v případě, že není odkazována ze souboru. idl.

## <a name="syntax"></a>Syntaxe

```cpp
[public]
```

## <a name="remarks"></a>Poznámky

Atribut **Public** C++ má stejné funkce jako [veřejný](/windows/win32/Midl/public) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak použít atribut **Public** :

```cpp
// cpp_attr_ref_public.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, public] typedef long MEMBERID;

[dispinterface, uuid(99999999-9999-9999-9999-000000000000)]
__interface IFireTabCtrl : IDispatch
{
   [id(2)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**definic**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)
