---
title: řetězec (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.string
dev_langs:
- C++
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6bdcdc6557253f8be9c6ecb20300f2338ab35d07
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889017"
---
# <a name="string-c"></a>string (C++)
Určuje, že jednorozměrná `char`, `wchar_t`, **bajtů** (nebo ekvivalentního) má ukazatel na takové pole nebo pole musí být považované za řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[string]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Řetězec** atribut C++ má stejné funkce jako [řetězec](http://msdn.microsoft.com/library/windows/desktop/aa367270) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak používat **řetězec** na rozhraní a definice typu:  
  
```  
// cpp_attr_ref_string.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export, string] typedef char a[21];  
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1)] HRESULT Method3([in, string] char *pC);  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Pole nebo odkazy pole, parametr rozhraní, rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy pole](../windows/array-attributes.md)   
 [export](../windows/export.md)   
