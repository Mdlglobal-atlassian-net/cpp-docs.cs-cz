---
title: jen pro čtení (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.readonly
dev_langs:
- C++
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87933b214dfe91f1c9f7db88127ef83da5b7201c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876563"
---
# <a name="readonly-c"></a>readonly (C++)
Zakáže přiřazení na člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[readonly]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Jen pro čtení** atribut C++ má stejné funkce jako [jen pro čtení](http://msdn.microsoft.com/library/windows/desktop/aa367152) MIDL atribut.  
  
 Pokud chcete zakázat úpravu parametru metody, použijte [v](../windows/in-cpp.md) atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje k využívání **jen pro čtení** atribut:  
  
```  
// cpp_attr_ref_readonly.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
  
[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]  
__interface IFireTabCtrl  
{  
   [readonly, id(1)] int i();  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy datového členu](../windows/data-member-attributes.md)   
