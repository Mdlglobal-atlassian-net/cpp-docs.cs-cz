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
ms.openlocfilehash: 0596b15daff5567e2572bf8c1f2b401cdf300a49
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642409"
---
# <a name="asyncuuid"></a>async_uuid
Určuje UUID, který nasměruje definovat synchronní a asynchronní verze rozhraní modelu COM kompilátoru MIDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[async_uuid (  
   uuid  
)]  
```  
  
### <a name="parameters"></a>Parametry  
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