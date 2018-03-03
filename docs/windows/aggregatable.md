---
title: "agregovatelné | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.aggregatable
dev_langs:
- C++
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec044e18fdd8bcd21fbad8d2e46c847c876cc00d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="aggregatable"></a>aggregatable
Označuje, že třída podporuje agregace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ aggregatable(   
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Hodnota* (volitelné)  
 Parametr k označení, když se dají agregovat objekt COM:  
  
-   **Nikdy** objektu COM nelze agregovat.  
  
-   **povolené** objekt COM lze vytvořit přímo, nebo se dají agregovat. Toto nastavení je výchozí.  
  
-   **vždy** objektu COM nelze vytvořit přímo a lze pouze agregovat. Při volání `CoCreateInstance` pro tento objekt, je třeba zadat objekt totožný **IUnknown** rozhraní (řízení **IUnknown**).  
  
## <a name="remarks"></a>Poznámky  
 **Agregovatelné** atribut C++ má stejné funkce jako [agregovatelné](http://msdn.microsoft.com/library/windows/desktop/aa366721) MIDL atribut. To znamená, že bude úspěšné kompilátor **agregovatelné** atribut prostřednictvím generovaného .idl souboru.  
  
 Tento atribut vyžaduje, aby [třída typu coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít stejného elementu. Pokud se používá jakékoli jeden atribut, budou automaticky použita další dvě. Například pokud **progid** se použije, **vi_progid –** a **třída typu coclass** jsou také použít.  
  
 **Projekty knihovny ATL**  
  
 Pokud tento atribut se používá v rámci projekt, který používá ATL chování změny atributů. Kromě popsané chování atribut také přidá jeden z následujících makra k třídě cíle:  
  
|Hodnota parametru|Vložené – makro|  
|---------------------|--------------------|  
|**Nikdy**|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|  
|**Povoleno**|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|  
|**Vždy**|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|  
  
## <a name="example"></a>Příklad  
  
```  
// cpp_attr_ref_aggregatable.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="MyModule")];  
  
[ coclass, aggregatable(allowed),  
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]  
class CMyClass {};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Jeden nebo více z následujících: **třída typu coclass**, **progid**, nebo **vi_progid –**.|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Agregace](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
