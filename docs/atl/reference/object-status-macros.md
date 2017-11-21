---
title: Objekt stavu makra | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs: C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc74d545388199eab2aca63ecdea1fdd62a9ef23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="object-status-macros"></a>Makra stav objektu
Toto makro nastaví příznaky, které patří do ovládacích prvků ActiveX.  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Používá se k nastavení v ovládacích prvcích ActiveX knihovny ATL **OLEMISC** příznaky.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  

##  <a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS  
 Používá se v ovládacích prvcích ActiveX knihovny ATL nastavení OLEMISC příznaků.  
  
```
DECLARE_OLEMISC_STATUS( miscstatus )
```  
  
### <a name="parameters"></a>Parametry  
 *miscStatus*  
 Všechny použitelné OLEMISC příznaky.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se používá k nastavení OLEMISC příznaků pro ovládací prvek ActiveX. Odkazovat na [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) další podrobnosti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
