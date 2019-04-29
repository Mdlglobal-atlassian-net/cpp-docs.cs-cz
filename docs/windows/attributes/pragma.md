---
title: direktivy pragma (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: 159e1570c2bde07bb4df8fa904a519e8e0018a6a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407455"
---
# <a name="pragma"></a>pragma

Zadaný řetězec vysílá do generovaného souboru bez použití uvozovek.

## <a name="syntax"></a>Syntaxe

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>Parametry

*pragma_statement*<br/>
Direktivy pragma, který chcete vrátit do generovaného souboru.

## <a name="remarks"></a>Poznámky

**– Direktiva pragma** C++ atribut má stejné funkce jako [– Direktiva pragma](/windows/desktop/Midl/pragma) atribut MIDL.

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[pack](../../preprocessor/pack.md)