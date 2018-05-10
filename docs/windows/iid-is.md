---
title: iid_is – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.iid_is
dev_langs:
- C++
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9ef3a14211e223b9902dc9843639d217ceaf1b3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="iidis"></a>iid_is
Určuje identifikátory IID rozhraní modelu COM, na kterou ukazatele rozhraní odkazuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ iid_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *výraz*  
 Výraz jazyka C, který určuje identifikátory IID rozhraní modelu COM ukazuje ukazatele rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 **Iid_is –** atribut C++ má stejné funkce jako [iid_is –](http://msdn.microsoft.com/library/windows/desktop/aa367044) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje použití **iid_is –**:  
  
```  
// cpp_attr_ref_iid_is.cpp  
// compile with: /LD  
#include "wtypes.h"  
#include "unknwn.h"  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]   
   IUnknown ** ppvObject);  
};  
  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Parametr rozhraní, – datový člen|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
