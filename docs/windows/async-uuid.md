---
title: async_uuid – | Microsoft Docs
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
ms.openlocfilehash: 857b10e206e5a4a3208086e5b7b1455f58bc40a8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856902"
---
# <a name="asyncuuid"></a>async_uuid
Určuje identifikátor UUID, který přesměruje MIDL kompilátoru k definování synchronní a asynchronní verzích rozhraní modelu COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [async_uuid (  
   uuid  
)]  
```  
  
#### <a name="parameters"></a>Parametry  
 *uuid*  
 UUID, který určuje verzi rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 **Async_uuid –** atribut C++ má stejné funkce jako [async_uuid –](http://msdn.microsoft.com/library/windows/desktop/aa366735) MIDL atribut.  
  
## <a name="example"></a>Příklad  
  
```  
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
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|**duální**, **dispinterface**|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
