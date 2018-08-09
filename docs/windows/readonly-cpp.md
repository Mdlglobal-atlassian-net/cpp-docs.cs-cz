---
title: jen pro čtení (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 05a46e099643602867aaa807e915e419054a8d60
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016002"
---
# <a name="readonly-c"></a>readonly (C++)
Zakáže přiřazení na datový člen.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[readonly]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Jen pro čtení** C++ atribut má stejné funkce jako [jen pro čtení](http://msdn.microsoft.com/library/windows/desktop/aa367152) atribut MIDL.  
  
 Pokud chcete zakázat úpravy parametru metody, použijte [v](../windows/in-cpp.md) atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje použití **jen pro čtení** atribut:  
  
```cpp  
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
|**Platí pro**|Metoda rozhraní|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy datového členu](../windows/data-member-attributes.md)   