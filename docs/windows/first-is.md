---
title: "first_is – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.first_is
dev_langs:
- C++
helpviewer_keywords:
- first_is attribute
ms.assetid: 89acbf56-3b38-4d44-83e8-1ce2f6f74ffd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13637f9381e233f5bcffe4dbacc9a86765b40b84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="firstis"></a>first_is
Určuje index první prvek pole má být přenesen.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ first_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *výraz*  
 Jeden nebo více výrazů jazyka C. Prázdný argument sloty jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 **First_is –** atribut C++ má stejné funkce jako [first_is –](http://msdn.microsoft.com/library/windows/desktop/aa366831) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje různé způsoby, kterými chcete zadat část do pole:  
  
```  
// cpp_attr_ref_first_is.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
  
[module(name="MyLib")];  
  
[object, uuid(11111111-1111-1111-1111-111111111111)]  
__interface b   
{  
   [id(0), propget, bindable, displaybind, defaultbind,   
requestedit] HRESULT get_I([out, retval]long *i);  
   HRESULT Proc1([in] short First, [in] short Last,   
[first_is(First), last_is(Last), size_is(Last-First)] char Arr1[]);   
   HRESULT Proc2([in] short First, [in] short Last,   
[last_is(First), size_is(Last)] char Arr2[]);  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Pole v `struct` nebo **– typ union**, rozhraní parametr, rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [last_is –](../windows/last-is.md)   
 [max_is –](../windows/max-is.md)   
 [length_is –](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   
