---
title: "Jímky událostí mapy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 309474220f081a0eca67d0f83ead21c59eb649e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="event-sink-maps"></a>Mapy jímek událostí
V případě, že vloženému ovládacímu prvku OLE aktivuje událost, obdrží kontejneru ovládacího prvku událost pomocí mechanismus, nazývá "události podřízený mapa," poskytl MFC. Mapy jímek událostí označí funkce obslužných rutin pro každou konkrétní události, stejně jako parametry těchto událostí. Další informace o mapy jímek událostí najdete v článku [– kontejnery ovládacích prvků ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="event-sink-maps"></a>Mapy jímek událostí  
  
|||  
|-|-|  
|[BEGIN_EVENTSINK_MAP –](#begin_eventsink_map)|Spustí definici mapy jímek událostí.|  
|[DECLARE_EVENTSINK_MAP –](#declare_eventsink_map)|Deklaruje mapy jímek událostí.|  
|[END_EVENTSINK_MAP –](#end_eventsink_map)|Ukončí definici mapy jímek událostí.|  
|[ON_EVENT –](#on_event)|Definuje obslužnou rutinu události pro konkrétní události.|  
|[ON_EVENT_RANGE –](#on_event_range)|Definuje obslužnou rutinu události pro určitou událost je aktivována z sadu ovládacích prvků OLE.|  
|[ON_EVENT_REFLECT –](#on_event_reflect)|Přijímá události aktivována ovládacím prvkem, než jsou zpracovávány kontejneru ovládacího prvku.|  
|[ON_PROPNOTIFY –](#on_propnotify)|Definuje obslužnou rutinu pro zpracování vlastnost oznámení z ovládacího prvku OLE.|  
|[ON_PROPNOTIFY_RANGE –](#on_propnotify_range)|Definuje obslužnou rutinu pro zpracování vlastnost oznámení z sadu ovládacích prvků OLE.|  
|[ON_PROPNOTIFY_REFLECT –](#on_propnotify_reflect)|Obdrží vlastnost oznámení zaslaná z ovládacího prvku, než jsou zpracovávány kontejneru ovládacího prvku.|  
  
##  <a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP –  
 Zahájí definici mapy jímek událostí.  
  
```   
BEGIN_EVENTSINK_MAP(theClass, baseClass)  
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Určuje, že je název třídy ovládacího prvku, jehož jímek událostí mapování těchto.  
  
 `baseClass`  
 Určuje název základní třídu `theClass`.  
  
### <a name="remarks"></a>Poznámky  
 V souboru implementace (sada), který definuje členské funkce pro třídu, spusťte mapy jímek událostí s `BEGIN_EVENTSINK_MAP` makro, pak přidejte makro položky pro všechny události upozornit a dokončete mapy jímek událostí s `END_EVENTSINK_MAP` makro.  
  
 Další informace o mapy jímek událostí a kontejnery ovládacích prvků OLE, najdete v článku [– kontejnery ovládacích prvků ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP –  
 Kontejner OLE může poskytnout mapování jímky událostí k určení událostem, které vaše kontejneru budou informováni o.  
  
```   
DECLARE_EVENTSINK_MAP()   
```  
  
### <a name="remarks"></a>Poznámky  
 Použití `DECLARE_EVENTSINK_MAP` makro na konci deklarace třídy. Pak na. Funkce CPP souboru, který definuje člena pro třídu, použijte `BEGIN_EVENTSINK_MAP` makro, makro položky pro všechny události, které mají být upozorněni a `END_EVENTSINK_MAP` makro deklarovat konce seznamu jímky událostí.  
  
 Další informace o mapy jímek událostí najdete v článku [– kontejnery ovládacích prvků ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="end_eventsink_map"></a>END_EVENTSINK_MAP –  
 Ukončí definici mapy jímek událostí.  
  
```   
END_EVENTSINK_MAP()   
```  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="on_event"></a>ON_EVENT –  
 Použití `ON_EVENT` aktivováno makra definovat funkci zpracování událostí pro událost pomocí ovládacího prvku OLE.  
  
```   
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Třídy, do které patří mapy jímek událostí.  
  
 `id`  
 ID ovládacího prvku OLE.  
  
 `dispid`  
 Odesílání ID události aktivováno pomocí ovládacího prvku.  
  
 `pfnHandler`  
 Ukazatel na funkci člena, která zpracovává událost. Tato funkce by měly mít **BOOL** návratový typ a typy parametrů, které odpovídají parametry události (najdete v části `vtsParams`). Funkce by měla vrátit **TRUE** k označení událost byla zpracovávaný jinak **FALSE**.  
  
 `vtsParams`  
 Posloupnost **VTS_** konstanty, které určuje typy parametrů pro událost. Toto jsou stejné konstanty, které se používají v odesílání položek mapování například `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Poznámky  
 `vtsParams` Argument je seznam hodnot oddělených mezerami **VTS_** konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárkami) určuje seznam parametrů funkce. Příklad:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Určuje seznam obsahující krátké celé číslo, za nímž následuje **BOOL**.  
  
 Seznam **VTS_** konstanty, najdete v části [event_custom –](event-maps.md#event_custom).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="on_event_range"></a>ON_EVENT_RANGE –  
 Použití `ON_EVENT_RANGE` makro definovat funkci zpracování událostí pro událost aktivováno žádné řízení OLE s ID ovládacího prvku v rámci souvislý rozsah ID.  
  
```   
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Třídy, do které patří mapy jímek událostí.  
  
 `idFirst`  
 ID ovládacího prvku první OLE v rozsahu.  
  
 `idLast`  
 ID ovládacího prvku poslední OLE v rozsahu.  
  
 `dispid`  
 Odesílání ID události aktivováno pomocí ovládacího prvku.  
  
 `pfnHandler`  
 Ukazatel na funkci člena, která zpracovává událost. Tato funkce by měly mít **BOOL** návratový typ, první parametr typu **Celé_číslo** (pro ID ovládacího prvku) a typy dalších parametrů, které odpovídají parametry události (najdete v části `vtsParams`). Funkce by měla vrátit **TRUE** k označení událost byla zpracovávaný jinak **FALSE**.  
  
 `vtsParams`  
 Posloupnost **VTS_** konstanty, které určuje typy parametrů pro událost. První konstanta by měla být typu **VTS_I4**, pro ID ovládacího prvku. Toto jsou stejné konstanty, které se používají v odesílání položek mapování například `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Poznámky  
 `vtsParams` Argument je seznam hodnot oddělených mezerami **VTS_** konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárkami) určuje seznam parametrů funkce. Příklad:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Určuje seznam obsahující krátké celé číslo, za nímž následuje **BOOL**.  
  
 Seznam **VTS_** konstanty, najdete v části [event_custom –](event-maps.md#event_custom).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje obslužnou rutinu, pro MouseDown – událost, implementována pro tři ovládací prvky ( `IDC_MYCTRL1` prostřednictvím `IDC_MYCTRL3`). Funkce obslužných rutin událostí, `OnRangeMouseDown`, je deklarován v záhlaví souboru třídy dialogového okna ( `CMyDlg`) jako:  
  
 [!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]  
  
 Následující kód je definována v souboru implementace třídy dialogového okna.  
  
 [!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="on_event_reflect"></a>ON_EVENT_REFLECT –  
 `ON_EVENT_REFLECT` Makro, při použití události podřízený mapy ovládacího prvku OLE obálkové třídy, obdrží události aktivována ovládacím prvkem, než jsou zpracovávány kontejneru ovládacího prvku.  
  
```   
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Třídy, do které patří mapy jímek událostí.  
  
 dispID  
 Odesílání ID události aktivováno pomocí ovládacího prvku.  
  
 `pfnHandler`  
 Ukazatel na funkci člena, která zpracovává událost. Tato funkce by měly mít **BOOL** návratový typ a typy parametrů, které odpovídají parametry události (najdete v části `vtsParams`). Funkce by měla vrátit **TRUE** k označení událost byla zpracovávaný jinak **FALSE**.  
  
 `vtsParams`  
 Posloupnost **VTS_** konstanty, které určuje typy parametrů pro událost. Toto jsou stejné konstanty, které se používají v odesílání položek mapování například `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Poznámky  
 `vtsParams` Argument je seznam hodnot oddělených mezerami **VTS_** konstanty.  
  
 Jeden nebo více z těchto hodnot oddělených mezerami (ne čárkami) určuje seznam parametrů funkce. Příklad:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Určuje seznam obsahující krátké celé číslo, za nímž následuje **BOOL**.  
  
 Seznam **VTS_** konstanty, najdete v části [event_custom –](event-maps.md#event_custom).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="on_propnotify"></a>ON_PROPNOTIFY –  
 Použití `ON_PROPNOTIFY` makro k definování položky mapy jímek událostí pro zpracování vlastnost oznámení z ovládacího prvku OLE.  
  
```   
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Třídy, do které patří mapy jímek událostí.  
  
 `id`  
 ID ovládacího prvku OLE.  
  
 `dispid`  
 Odesílání ID vlastnosti zahrnutých v oznámení.  
  
 `pfnRequest`  
 Ukazatel na člena funkce, která zpracovává **OnRequestEdit, viz** oznámení pro tuto vlastnost. Tato funkce by měly mít **BOOL** návratový typ a **BOOL\***  parametr. Tato funkce má Nastaví parametr na **TRUE** umožňuje změnit vlastnosti a **FALSE** tak, aby zakázala. Funkce by měla vrátit **TRUE** indikující oznámení byla zpracovávaný jinak **FALSE**.  
  
 `pfnChanged`  
 Ukazatel na člena funkce, která zpracovává **OnChanged** oznámení pro tuto vlastnost. Funkce by měly mít **BOOL** návratový typ a **Celé_číslo** parametr. Funkce by měla vrátit **TRUE** k označení, že byla oznámení zpracovávaný; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 `vtsParams` Argument je seznam hodnot oddělených mezerami **VTS_** konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárkami) určuje seznam parametrů funkce. Příklad:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Určuje seznam obsahující krátké celé číslo, za nímž následuje **BOOL**.  
  
 Seznam **VTS_** konstanty, najdete v části [event_custom –](event-maps.md#event_custom).  
  
##  <a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE –  
 Použití `ON_PROPNOTIFY_RANGE` makro k definování položky mapy jímek událostí pro zpracování vlastnost oznámení z ovládacích prvků OLE s ID ovládacího prvku v rámci souvislý rozsah ID.  
  
```  
 
ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Třídy, do které patří mapy jímek událostí.  
  
 `idFirst`  
 ID ovládacího prvku první OLE v rozsahu.  
  
 `idLast`  
 ID ovládacího prvku poslední OLE v rozsahu.  
  
 `dispid`  
 Odesílání ID vlastnosti zahrnutých v oznámení.  
  
 `pfnRequest`  
 Ukazatel na člena funkce, která zpracovává **OnRequestEdit, viz** oznámení pro tuto vlastnost. Tato funkce by měly mít **BOOL** návratový typ a **Celé_číslo** a **BOOL\***  parametry. Funkce měli Nastaví parametr na **TRUE** umožňuje změnit vlastnosti a **FALSE** tak, aby zakázala. Funkce by měla vrátit **TRUE** k označení, že byla oznámení zpracovávaný; jinak hodnota **FALSE**.  
  
 `pfnChanged`  
 Ukazatel na člena funkce, která zpracovává **OnChanged** oznámení pro tuto vlastnost. Funkce by měly mít **BOOL** návratový typ a **Celé_číslo** parametr. Funkce by měla vrátit **TRUE** k označení, že byla oznámení zpracovávaný; jinak hodnota **FALSE**.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT –  
 `ON_PROPNOTIFY_REFLECT` Makro, při použití události podřízený mapy ovládacího prvku OLE obálkové třídy, obdrží vlastnost oznámení zaslaná z ovládacího prvku, než jsou zpracovávány kontejneru ovládacího prvku.  
  
```  
 
ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Třídy, do které patří mapy jímek událostí.  
  
 `dispid`  
 Odesílání ID vlastnosti zahrnutých v oznámení.  
  
 `pfnRequest`  
 Ukazatel na člena funkce, která zpracovává **OnRequestEdit, viz** oznámení pro tuto vlastnost. Tato funkce by měly mít **BOOL** návratový typ a **BOOL\***  parametr. Tato funkce má Nastaví parametr na **TRUE** umožňuje změnit vlastnosti a **FALSE** tak, aby zakázala. Funkce by měla vrátit **TRUE** indikující oznámení byla zpracovávaný jinak **FALSE**.  
  
 `pfnChanged`  
 Ukazatel na člena funkce, která zpracovává **OnChanged** oznámení pro tuto vlastnost. Funkce by měly mít **BOOL** návratový typ a žádné parametry. Funkce by měla vrátit **TRUE** indikující oznámení byla zpracovávaný jinak **FALSE**.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
    
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
