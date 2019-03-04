---
title: Mapy jímek událostí
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 8e33636253b269692f87f99980b9da0cd60867ee
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285578"
---
# <a name="event-sink-maps"></a>Mapy jímek událostí

Jakmile se vloženému ovládacímu prvku OLE aktivuje událost, kontejneru ovládacího prvku přijímat události pomocí mechanismu, nazývá "událostí jímky mapa," dodávané knihovnou MFC. Toto mapování jímky událostí určuje funkce obslužné rutiny pro každé konkrétní události, stejně jako parametry těchto událostí. Další informace o mapy jímek událostí, najdete v článku [ActiveX – kontejnery ovládacích prvků](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Mapy jímek událostí

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Spustí definice mapu jímky událostí.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Deklaruje mapu jímky událostí.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Ukončí definici mapu jímky událostí.|
|[ON_EVENT](#on_event)|Definuje obslužnou rutinu události pro konkrétní události.|
|[ON_EVENT_RANGE](#on_event_range)|Definuje obslužnou rutinu události pro konkrétní události vyvolané ze sady ovládacích prvků OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Přijímá události vyvolané ovládací prvek předtím, než jsou zpracovávány kontejneru ovládacího prvku.|
|[ON_PROPNOTIFY](#on_propnotify)|Definuje obslužnou rutinu pro zpracování oznámení o vlastnosti z ovládacího prvku OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Definuje obslužnou rutinu pro zpracování oznámení o vlastnost ze sady ovládacích prvků OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Přijímá vlastnost oznámení zaslaná z ovládacího prvku, než jsou zpracovávány kontejneru ovládacího prvku.|

##  <a name="begin_eventsink_map"></a>  BEGIN_EVENTSINK_MAP

Začíná definice mapě událostí jímky.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje, že je název třídy ovládacího prvku, namapujte tento parametr jehož jímky událostí.

*baseClass*<br/>
Určuje název základní třídy *theClass*.

### <a name="remarks"></a>Poznámky

V souboru implementace (.cpp), který definuje členské funkce třídy na mapě událostí jímky začínat BEGIN_EVENTSINK_MAP – makro pak přidat makro položky pro každou událost upozornit a dokončete mapě událostí jímky s END_EVENTSINK_MAP – makro.

Další informace o mapy jímek událostí a kontejnery ovládacích prvků OLE, najdete v článku [ActiveX – kontejnery ovládacích prvků](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="declare_eventsink_map"></a>  DECLARE_EVENTSINK_MAP

Mapu jímky událostí k určení události, které váš kontejner budete informováni o může poskytnout kontejneru OLE.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Poznámky

Použití DECLARE_EVENTSINK_MAP – makro na konec deklarace třídy. Potom v. Soubor CPP, který definuje členské funkce třídy, použijte BEGIN_EVENTSINK_MAP – makro, makro položky pro všechny události, které chcete být upozorněni a END_EVENTSINK_MAP – makro, chcete-li deklarovat konce seznamu událostí jímky.

Další informace o mapy jímek událostí, najdete v článku [ActiveX – kontejnery ovládacích prvků](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="end_eventsink_map"></a>  END_EVENTSINK_MAP

Ukončí definici mapě událostí jímky.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="on_event"></a>  ON_EVENT

ON_EVENT – makro použijte k definování funkci obslužné rutiny události pro události vyvolané ovládacího prvku OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ke kterému patří této mapě událostí jímky.

*id*<br/>
ID ovládacího prvku OLE.

*dispid*<br/>
Identifikátor odeslání události vyvolané ovládacího prvku.

*pfnHandler*<br/>
Ukazatel na členskou funkci, která zpracovává událost. Tato funkce by měla mít BOOL návratový typ a typy parametrů, které odpovídají parametrům události (viz *vtsParams*). Funkce by měla vrátit hodnotu TRUE označuje, že událost byla zpracována; v opačném případě FALSE.

*vtsParams*<br/>
Posloupnost **VTS_** konstanty, které určuje typy parametrů pro událost. Jedná se o stejné konstanty, které se používají v odesílání položek mapování například DISP_FUNCTION.

### <a name="remarks"></a>Poznámky

*VtsParams* argument je místo oddělený seznam hodnot z **VTS_** konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárky) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Určuje seznam obsahující krátké celé číslo, za nímž následuje BOOL.

Seznam **VTS_** konstanty, naleznete v tématu [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="on_event_range"></a>  ON_EVENT_RANGE

ON_EVENT_RANGE – makro použijte k definování funkci obslužné rutiny události pro události vyvolané libovolný ovládací prvek OLE, s ID ovládacího prvku v rámci souvislého rozsahu ID.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ke kterému patří této mapě událostí jímky.

*idFirst*<br/>
ID ovládacího prvku první ovládací prvek OLE v rozsahu.

*idLast*<br/>
ID ovládacího prvku poslední ovládací prvek OLE v rozsahu.

*dispid*<br/>
Identifikátor odeslání události vyvolané ovládacího prvku.

*pfnHandler*<br/>
Ukazatel na členskou funkci, která zpracovává událost. Tato funkce by měla mít hodnotu vrátí typ, první parametr typu UINT (pro ID ovládacího prvku) a typy dalších parametrů, které odpovídají parametrům události (viz *vtsParams*). Funkce by měla vrátit hodnotu TRUE označuje, že událost byla zpracována; v opačném případě FALSE.

*vtsParams*<br/>
Posloupnost **VTS_** konstanty, které určuje typy parametrů pro událost. První konstanta by měl být typu VTS_I4, pro ID ovládacího prvku. Jedná se o stejné konstanty, které se používají v odesílání položek mapování například DISP_FUNCTION.

### <a name="remarks"></a>Poznámky

*VtsParams* argument je místo oddělený seznam hodnot z **VTS_** konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárky) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Určuje seznam obsahující krátké celé číslo, za nímž následuje BOOL.

Seznam **VTS_** konstanty, naleznete v tématu [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Příklad

Následující příklad ukazuje obslužné rutiny události pro událost MouseDown implementována pro tři ovládací prvky (IDC_MYCTRL1 prostřednictvím IDC_MYCTRL3). Funkce obslužné rutiny události `OnRangeMouseDown`, je deklarována v souboru hlaviček třídy dialogového okna ( `CMyDlg`) jako:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Následující kód je definovaný v souboru implementace třídy dialogového okna.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="on_event_reflect"></a>  ON_EVENT_REFLECT

ON_EVENT_REFLECT – makro, při použití událostí jímky mapy ovládacího prvku OLE obálkové třídy, přijímá události vyvolané ovládací prvek předtím, než jsou zpracovávány kontejneru ovládacího prvku.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ke kterému patří této mapě událostí jímky.

*dispid*<br/>
Identifikátor odeslání události vyvolané ovládacího prvku.

*pfnHandler*<br/>
Ukazatel na členskou funkci, která zpracovává událost. Tato funkce by měla mít BOOL návratový typ a typy parametrů, které odpovídají parametrům události (viz *vtsParams*). Funkce by měla vrátit hodnotu TRUE označuje, že událost byla zpracována; v opačném případě FALSE.

*vtsParams*<br/>
Posloupnost **VTS_** konstanty, které určuje typy parametrů pro událost. Jedná se o stejné konstanty, které se používají v odesílání položek mapování například DISP_FUNCTION.

### <a name="remarks"></a>Poznámky

*VtsParams* argument je místo oddělený seznam hodnot z **VTS_** konstanty.

Jeden nebo více z těchto hodnot oddělených mezerami (ne čárky) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Určuje seznam obsahující krátké celé číslo, za nímž následuje BOOL.

Seznam **VTS_** konstanty, naleznete v tématu [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="on_propnotify"></a>  ON_PROPNOTIFY

ON_PROPNOTIFY – makro použijte k definování položku mapování jímky událostí pro zpracování oznámení o vlastnosti z ovládacího prvku OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ke kterému patří této mapě událostí jímky.

*id*<br/>
ID ovládacího prvku OLE.

*dispid*<br/>
ID odbavení vlastnost účastnící se oznámení.

*pfnRequest*<br/>
Ukazatel na členskou funkci, která zpracovává `OnRequestEdit` oznámení pro tuto vlastnost. Tato funkce by měla mít BOOL návratový typ a **BOOL** <strong>\*</strong> parametru. Tato funkce by měl nastavit parametr na hodnotu TRUE, vlastnost, která má změna povolit a hodnotu FALSE, aby se zakáže. Funkce by měla vrátit hodnotu TRUE označuje, že byla zpracována oznámení; v opačném případě FALSE.

*pfnChanged*<br/>
Ukazatel na členskou funkci, která zpracovává `OnChanged` oznámení pro tuto vlastnost. Funkce by měla obsahovat BOOL návratový typ a parametr UINT. Funkce by měla vrátit hodnotu TRUE označuje, že byla zpracována oznámení; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

*VtsParams* argument je místo oddělený seznam hodnot z **VTS_** konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárky) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Určuje seznam obsahující krátké celé číslo, za nímž následuje BOOL.

Seznam **VTS_** konstanty, naleznete v tématu [EVENT_CUSTOM](event-maps.md#event_custom).

##  <a name="on_propnotify_range"></a>  ON_PROPNOTIFY_RANGE

Definujte položku mapování jímky událostí pro zpracování vlastnost oznámení z ovládacích prvků OLE s ID ovládacího prvku v rámci souvislého rozsahu ID pomocí ON_PROPNOTIFY_RANGE – makro.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ke kterému patří této mapě událostí jímky.

*idFirst*<br/>
ID ovládacího prvku první ovládací prvek OLE v rozsahu.

*idLast*<br/>
ID ovládacího prvku poslední ovládací prvek OLE v rozsahu.

*dispid*<br/>
ID odbavení vlastnost účastnící se oznámení.

*pfnRequest*<br/>
Ukazatel na členskou funkci, která zpracovává `OnRequestEdit` oznámení pro tuto vlastnost. Tato funkce by měla mít `BOOL` návratový typ a `UINT` a `BOOL*` parametry. Funkce by měl nastavit parametr na hodnotu TRUE, vlastnost, která má změna povolit a hodnotu FALSE, aby se zakáže. Funkce by měla vrátit hodnotu TRUE označuje, že byla zpracována oznámení; v opačném případě FALSE.

*pfnChanged*<br/>
Ukazatel na členskou funkci, která zpracovává `OnChanged` oznámení pro tuto vlastnost. Funkce by měla být `BOOL` návratový typ a `UINT` parametru. Funkce by měla vrátit hodnotu TRUE označuje, že byla zpracována oznámení; v opačném případě FALSE.

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="on_propnotify_reflect"></a>  ON_PROPNOTIFY_REFLECT

ON_PROPNOTIFY_REFLECT – makro, při použití událostí jímky mapy ovládacího prvku OLE obálkové třídy, obdrží vlastnost oznámení zaslaná z ovládacího prvku, než jsou zpracovávány kontejneru ovládacího prvku.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ke kterému patří této mapě událostí jímky.

*dispid*<br/>
ID odbavení vlastnost účastnící se oznámení.

*pfnRequest*<br/>
Ukazatel na členskou funkci, která zpracovává `OnRequestEdit` oznámení pro tuto vlastnost. Tato funkce by měla mít BOOL návratový typ a **BOOL** <strong>\*</strong> parametru. Tato funkce by měl nastavit parametr na hodnotu TRUE, vlastnost, která má změna povolit a hodnotu FALSE, aby se zakáže. Funkce by měla vrátit hodnotu TRUE označuje, že byla zpracována oznámení; v opačném případě FALSE.

*pfnChanged*<br/>
Ukazatel na členskou funkci, která zpracovává `OnChanged` oznámení pro tuto vlastnost. Funkce by měla obsahovat BOOL návratový typ a žádné parametry. Funkce by měla vrátit hodnotu TRUE označuje, že byla zpracována oznámení; v opačném případě FALSE.

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
