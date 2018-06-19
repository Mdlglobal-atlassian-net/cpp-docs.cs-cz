---
title: Objekt stavu makra | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eddfc28c659d0c1eb54794d8fc76a9f3a4f9e73b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360871"
---
# <a name="object-status-macros"></a>Makra stav objektu
Toto makro nastaví příznaky, které patří do ovládacích prvků ActiveX.  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Používá se k nastavení v ovládacích prvcích ActiveX knihovny ATL **OLEMISC** příznaky.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS  
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
