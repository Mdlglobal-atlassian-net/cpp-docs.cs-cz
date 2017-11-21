---
title: "Zprávy Windows makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlbase/ATL::WM_FORWARDMSG
dev_langs: C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 66e212b1f8bd2e749bc87fec92b935aa466522b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="windows-messages-macros"></a>Zprávy Windows makra
Toto makro předává zprávy oken.  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|Slouží k předání přijatých okno do jiného okna pro zpracování zprávy.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h 
   
##  <a name="wm_forwardmsg"></a>WM_FORWARDMSG  
 Toto makro předá zprávu přijme a údržbu za účelem další okno zpracování.  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zpráva byla zpracována, hodnotu není.  
  
### <a name="remarks"></a>Poznámky  
 Použití `WM_FORWARDMSG` přeposílat přijatých okno do jiného okna pro zpracování zprávy. Parametry LPARAM a WPARAM používají následujícím způsobem:  
  
|Parametr|Použití|  
|---------------|-----------|  
|WPARAM|Data definovaná uživatelem|  
|LPARAM|Ukazatel na `MSG` struktura, která obsahuje informace o zprávu|  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu `m_hWndOther` představuje okna, která obdrží tuto zprávu.  
  
 [!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
