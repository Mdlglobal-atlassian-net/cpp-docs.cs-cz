---
title: async_uuid (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 537bd6d645532d9d5d20b740125c66f3953239bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168457"
---
# <a name="async_uuid"></a>async_uuid

Určuje identifikátor UUID, který přesměruje kompilátor MIDL tak, aby definoval synchronní i asynchronní verzi rozhraní modelu COM.

## <a name="syntax"></a>Syntaxe

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>Parametry

*uuid*<br/>
Identifikátor UUID, který určuje verzi rozhraní.

## <a name="remarks"></a>Poznámky

Atribut **async_uuid** C++ má stejné funkce jako atribut [async_uuid](/windows/win32/Midl/async-uuid) MIDL.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|`interface`|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|**duální**, **odesílající**|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)
