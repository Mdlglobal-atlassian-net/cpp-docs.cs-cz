---
title: call_as (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.call_as
dev_langs:
- C++
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c8769b542fccd512c1c32b418ffc9f1ad5758628
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061544"
---
# <a name="callas"></a>call_as

Umožňuje [místní](local-cpp.md) funkce mají být namapovány na vzdálenou funkci tak, aby při vzdálené funkce je volána, je vyvolána lokální funkce.

## <a name="syntax"></a>Syntaxe

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Parametry

*– funkce*<br/>
Lokální funkce, kterou chcete volat při vyvolání vzdálenou funkci.

## <a name="remarks"></a>Poznámky

**Call_as** C++ atribut má stejné funkce jako [call_as](/windows/desktop/Midl/call-as) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak můžete **call_as** mapovat funkci nonremotable (`f1`) na funkci lze používat vzdáleně (`Remf1`):

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[local](local-cpp.md)