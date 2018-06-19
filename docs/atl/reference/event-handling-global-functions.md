---
title: Globální funkce zpracování událostí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
dev_langs:
- C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb2c7834e7d5475810973a42ef179ea4f5f0079f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358335"
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

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop  
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
