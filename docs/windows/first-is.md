---
title: first_is – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.first_is
dev_langs:
- C++
helpviewer_keywords:
- first_is attribute
ms.assetid: 89acbf56-3b38-4d44-83e8-1ce2f6f74ffd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e15897eeaa6a158ae3946202819b697c7372984d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642704"
---
# <a name="firstis"></a>first_is
Určuje index první prvek pole předávají.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ first_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Výraz*  
 Jeden nebo více výrazů jazyka C. Prázdný argument sloty jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 **First_is –** C++ atribut má stejné funkce jako [first_is –](http://msdn.microsoft.com/library/windows/desktop/aa366831) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje různé způsoby, jak zadat oddíl v poli:  
  
```cpp  
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
|**Platí pro**|Pole v **struktura** nebo **sjednocení**, rozhraní parametr, rozhraní – metoda|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [– TypeDef, Enum, Union a struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [last_is –](../windows/last-is.md)   
 [max_is –](../windows/max-is.md)   
 [length_is –](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   