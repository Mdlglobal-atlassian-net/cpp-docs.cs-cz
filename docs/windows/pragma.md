---
title: Direktiva pragma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pragma
dev_langs:
- C++
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cab41277a7e5560fd842bf720fd776961d918d99
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="pragma"></a>pragma
Zadaný řetězec vysílá do souboru generovaného .idl bez použití uvozovek. .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ pragma(  
   pragma_statement  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *pragma_statement*  
 Direktiva pragma, kterou chcete přejít do generovaného .idl souboru.  
  
## <a name="remarks"></a>Poznámky  
 **– Direktiva pragma** atribut C++ má stejné funkce jako [– Direktiva pragma](http://msdn.microsoft.com/library/windows/desktop/aa367143) MIDL atribut.  
  
## <a name="example"></a>Příklad  
  
```  
// cpp_attr_ref_pragma.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[pragma(pack(4))];  
  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A  
{  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Odkudkoli|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [pack](../preprocessor/pack.md)   
