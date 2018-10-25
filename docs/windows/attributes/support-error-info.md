---
title: support_error_info – (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.support_error_info
dev_langs:
- C++
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0d86b31823ec31461f953c7cfc16a5774f215fd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067160"
---
# <a name="supporterrorinfo"></a>support_error_info

Implementuje podporu pro vracení podrobné chyby.

## <a name="syntax"></a>Syntaxe

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Parametry

*error_interface*<br/>
Identifikátor implementace rozhraní `IErrorInfo`.

## <a name="remarks"></a>Poznámky

**Support_error_info –** C++ atribut implementuje podporu pro vracení podrobné, kontextové chyby se tak cílový objekt do klienta. Pro objekt, který má podporovat chyby, metody `IErrorInfo` pomocí objektu musí implementovat rozhraní. Další informace najdete v tématu [podpora IDispatch a IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Přidá tento atribut [isupporterrorinfoimpl –](../../atl/reference/isupporterrorinfoimpl-class.md) třídu jako základní třídu na cílový objekt. Výsledkem je výchozí implementace `ISupportErrorInfo` a slouží k tomu jedno rozhraní generuje chyby na objekt.

## <a name="example"></a>Příklad

Následující kód přidává podporu výchozí `ISupportErrorInfo` rozhraní při `CMyClass` objektu.

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**class**|
|**Opakovatelné**|Ano|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[COM – atributy](com-attributes.md)<br/>
[Atributy třídy](class-attributes.md)