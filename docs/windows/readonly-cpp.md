---
title: "jen pro čtení (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.readonly
dev_langs: C++
helpviewer_keywords: readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 52ee0c600cf12a9709072a8c1cb502dada70f708
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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