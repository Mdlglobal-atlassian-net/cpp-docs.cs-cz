---
title: pragma (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: 56b1aa4bf445095b86a1ea6792bfc78f45266e9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166481"
---
# <a name="pragma"></a>pragma

Vygeneruje zadaný řetězec do generovaného souboru IDL bez použití uvozovek.

## <a name="syntax"></a>Syntaxe

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>Parametry

*pragma_statement*<br/>
Direktiva pragma, kterou chcete přejít do generovaného souboru IDL.

## <a name="remarks"></a>Poznámky

Atribut **pragma** C++ má stejné funkce jako atribut [pragma](/windows/win32/Midl/pragma) MIDL.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Jakékoli|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[pack](../../preprocessor/pack.md)
