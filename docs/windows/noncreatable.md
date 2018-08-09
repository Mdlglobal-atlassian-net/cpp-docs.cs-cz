---
title: noncreatable | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.noncreatable
dev_langs:
- C++
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 79791c2bbfd927d26ef70d50d225d8eff95bd674
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014270"
---
# <a name="noncreatable"></a>noncreatable
Definuje objekt, který se nedá vytvořit instance samostatně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[noncreatable]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Noncreatable** C++ atribut má stejné funkce jako [noncreatable –](http://msdn.microsoft.com/library/windows/desktop/aa367118) atribut MIDL a automaticky předána do vytvořeného. Soubor IDL kompilátorem.  
  
 Pokud tento atribut se používá v rámci projektu, který používá knihovny ATL, se změní chování atributu. Kromě výše uvedených chování atribut také vloží [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) – makro. Toto makro označuje s knihovnou ATL objekt nelze vytvořit externě.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cpp_attr_ref_noncreatable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("11111111-1111-1111-1111-111111111111")]  
__interface A   
{  
};  
  
[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]  
class CMyClass : public A   
{  
   HRESULT xx();  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, **– struktura**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|**coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   