---
title: "Globální funkce zpracování událostí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlbase/ATL::AtlWaitWithMessageLoop
dev_langs: C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6670ef283d24f57b407ad70693421feae427855f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="event-handling-global-functions"></a>Globální funkce zpracování událostí
Tato funkce poskytuje obslužné rutiny události.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Čeká na objekt signál, mezitím odeslání zprávy oken podle potřeby.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  

##  <a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop  
 Počká na objekt, který má být signalizován, a mezitím podle potřeby odbaví zprávy okna.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```  
  
### <a name="parameters"></a>Parametry  
 `hEvent`  
 [v] Popisovač objektu pro čekání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** Pokud nesignalizuje objektu.  
  
### <a name="remarks"></a>Poznámky  
 To je užitečné, pokud chcete čekat na událost objektu dojít a informováni o se děje, ale povolit okno zpráv k odeslání při čekání.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)
