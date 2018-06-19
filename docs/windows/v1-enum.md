---
title: v1_enum – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.v1_enum
dev_langs:
- C++
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b3156554f5d2b799a9e1ef5a067d1f2e8e600d38
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890658"
---
# <a name="v1enum"></a>v1_enum
Přesměruje, že zadaného výčtového typu předávají jako 32bitová verze entity místo výchozího 16 bitů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[v1_enum]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **V1_enum –** atribut C++ má stejné funkce jako [v1_enum –](http://msdn.microsoft.com/library/windows/desktop/aa367303) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje k využívání **v1_enum –**:  
  
```  
// cpp_attr_ref_v1_enum.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export, v1_enum]   
enum eList {   
   e1 = 1,   
   e2 = 2  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Výčtový typ|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)   
