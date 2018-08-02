---
title: async_uuid – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.async_uuid
dev_langs:
- C++
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c76aee3ce1e56f60e966094bb2d634269cd5e3a9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466745"
---
# <a name="asyncuuid"></a>async_uuid
Určuje UUID, který nasměruje definovat synchronní a asynchronní verze rozhraní modelu COM kompilátoru MIDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[async_uuid (  
   uuid  
)]  
```  
  
#### <a name="parameters"></a>Parametry  
 *uuid*  
 Identifikátor UUID, který identifikuje verzi rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 **Async_uuid –** C++ atribut má stejné funkce jako [async_uuid –](http://msdn.microsoft.com/library/windows/desktop/aa366735) atribut MIDL.  
  
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
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|**duální**, **dispinterface**|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   