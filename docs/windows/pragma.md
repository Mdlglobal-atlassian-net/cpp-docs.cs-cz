---
title: direktivy pragma | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pragma
dev_langs:
- C++
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2e6d5d832cd051c8e527b1d161158483d8fcaed1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428750"
---
# <a name="pragma"></a>pragma

Zadaný řetězec vysílá do generovaného souboru bez použití uvozovek.

## <a name="syntax"></a>Syntaxe

```cpp
[ pragma(
   pragma_statement
) ];
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
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Samostatné atributy](../windows/stand-alone-attributes.md)<br/>
[pack](../preprocessor/pack.md)  