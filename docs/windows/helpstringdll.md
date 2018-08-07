---
title: helpstringdll – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringdll
dev_langs:
- C++
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 27303f294f2414e2ea3f15de0c5bbfb1723628aa
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570077"
---
# <a name="helpstringdll"></a>helpstringdll
Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ helpstringdll(  
   "string"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *string*  
 Knihovny DLL použít k provádění vyhledání řetězce dokumentu.  
  
## <a name="remarks"></a>Poznámky  
 **Helpstringdll –** C++ atribut má stejné funkce jako [helpstringdll –](http://msdn.microsoft.com/library/windows/desktop/aa366860) atribut MIDL.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cpp_attr_ref_helpstringdll.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib", helpstringdll="xx.dll")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI   
{  
   HRESULT xxx();  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, **rozhraní**, rozhraní – metoda|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   