---
title: support_error_info (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: e61ef2efbdc4039f496d7ffbcccc37cc8d111935
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166143"
---
# <a name="support_error_info"></a>support_error_info

Implementuje podporu pro vracení podrobných chyb.

## <a name="syntax"></a>Syntaxe

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Parametry

*error_interface*<br/>
Identifikátor rozhraní, které implementuje `IErrorInfo`.

## <a name="remarks"></a>Poznámky

Atribut **support_error_info** C++ implementuje podporu pro vracení podrobných kontextových chyb zjištěných cílovým objektem klientovi. Aby objekt podporoval chyby, musí být metody rozhraní `IErrorInfo` implementovány objektem. Další informace najdete v tématu [Podpora rozhraní IDispatch a IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Tento atribut přidá třídu [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) jako základní třídu do cílového objektu. Výsledkem je výchozí implementace `ISupportErrorInfo` a může být použita, pokud jedno rozhraní generuje chyby v objektu.

## <a name="example"></a>Příklad

Následující kód přidá výchozí podporu rozhraní `ISupportErrorInfo` do objektu `CMyClass`.

```cpp
// cpp_attr_ref_support_error_info.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="mymod")];
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]
__interface IMyErrors
{
};

[ coclass, support_error_info("IMyErrors"),
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]
class CMyClass
{
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**class**|
|**REPEATABLE**|Ano|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[COM – atributy](com-attributes.md)<br/>
[Atributy třídy](class-attributes.md)
