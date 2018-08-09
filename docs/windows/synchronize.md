---
title: Synchronizovat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.synchronize
dev_langs:
- C++
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 583f05e3496ea6308dac8c7fa37c7e350165e74b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020050"
---
# <a name="synchronize"></a>synchronize
Synchronizuje přístup k cílové metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[synchronize]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Synchronizovat** C++ atribut implementuje podporu pro synchronizaci cílové metody objektu. Synchronizace umožňuje řízení přístupu na cílovou metodu více objektů určených k použití běžných prostředků (například pro metodu třídy).  
  
 Vložit tímto atributem nevolá správné `Lock` – metoda (určené model vláken) na začátku cílové metody. Pokud metoda skončí, `Unlock` je automaticky volána. Další informace o těchto funkcích najdete v tématu [CComAutoThreadModule::Lock](../atl/reference/ccomautothreadmodule-class.md#lock)  
  
 Tento atribut vyžaduje, aby [coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít u stejného elementu. Pokud se používá jakékoli jeden atribut, další dvě automaticky použity. Například pokud `progid` se použije, `vi_progid` a `coclass` jsou použita také.  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje synchronizaci pro `UpdateBalance` metodu `CMyClass` objektu.  
  
```cpp  
// cpp_attr_ref_synchronize.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="SYNC")];  
  
[coclass,  
 threading(both),  
 vi_progid("MyProject.MyClass"),  
 progid("MyProject.MyClass.1"),  
 uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")  
]  
class CMyClass {  
   float m_nBalance;  
  
   [synchronize]  
   void UpdateBalance(float nAdjust) {  
      m_nBalance += nAdjust;  
   }  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Metoda třídy, – metoda|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Jeden nebo více z následujících akcí: `coclass`, `progid`, nebo `vi_progid`.|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [COM – atributy](../windows/com-attributes.md)   