---
title: Mapy jímek událostí
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 731ed2403aae3332e81702673d1181e9e52399a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365725"
---
# <a name="event-sink-maps"></a>Mapy jímek událostí

Když vložený ovládací prvek OLE vyvolá událost, kontejner ovládacího prvku obdrží událost pomocí mechanismu nazývaného "mapování jímky událostí", které dodává knihovna MFC. Tato mapa jímky událostí určuje obslužné rutiny funkce pro každou konkrétní událost, jakož i parametry těchto událostí. Další informace o mapách jímky událostí naleznete v článku [Kontejnery ovládacího prvku ActiveX](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Mapy jímek událostí

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Spustí definici mapy jímky událostí.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Deklaruje mapu jímky událostí.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Ukončí definici mapy jímky událostí.|
|[ON_EVENT](#on_event)|Definuje obslužnou rutinu události pro konkrétní událost.|
|[ON_EVENT_RANGE](#on_event_range)|Definuje obslužnou rutinu události pro konkrétní událost vypálenou ze sady ovládacích prvků OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Přijímá události aktivována ovládacího prvku před jejich zpracování kontejneru ovládacího prvku.|
|[ON_PROPNOTIFY](#on_propnotify)|Definuje obslužnou rutinu pro zpracování oznámení vlastností z ovládacího prvku OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Definuje obslužnou rutinu pro zpracování oznámení vlastností ze sady ovládacích prvků OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Přijímá oznámení vlastností odeslaná ovládacím prvkem před jejich zpracováním kontejnerem ovládacího prvku.|

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP

Začíná definici mapy jímky událostí.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy ovládacího prvku, jehož mapování jímky událostí se jedná.

*Baseclass*<br/>
Určuje název základní třídy *Class*.

### <a name="remarks"></a>Poznámky

V souboru implementace (.cpp), který definuje členské funkce pro vaši třídu, spusťte mapu jímky událostí s BEGIN_EVENTSINK_MAP makro, přidejte položky maker pro každou událost, která má být upozorněna, a dokončete mapu jímky událostí s END_EVENTSINK_MAP makro.

Další informace o mapách jímky událostí a kontejnerech ovládacích prvku OLE naleznete v článku [Kontejnery ovládacího prvku ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP

Kontejner OLE může poskytnout mapu jímky událostí k určení událostí, na které bude kontejner upozorňován.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Poznámky

Použijte makro DECLARE_EVENTSINK_MAP na konci deklarace třídy. Potom v . CPP soubor, který definuje členské funkce pro třídu, použijte BEGIN_EVENTSINK_MAP makro, položky maker pro každou událost, která má být upozorněna, a END_EVENTSINK_MAP makro deklarovat konec seznamu jímky událostí.

Další informace o mapách jímky událostí naleznete v článku [Kontejnery ovládacího prvku ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a>END_EVENTSINK_MAP

Ukončí definici mapy jímky událostí.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="on_event"></a><a name="on_event"></a>ON_EVENT

Pomocí ON_EVENT makra definujte funkci obslužné rutiny události pro událost vypálenou ovládacím prvkem OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, do které patří mapa jímky této události.

*Id*<br/>
ID ovládacího prvku OLE.

*Dispid*<br/>
ID odeslání události vypálené ovládacím prvkem.

*pfnHandler*<br/>
Ukazatel na členská funkce, která zpracovává událost. Tato funkce by měla mít návratový typ BOOL a typy parametrů, které odpovídají parametrům události (viz *vtsParams*). Funkce by měla vrátit HODNOTU TRUE, která označuje, že událost byla zpracována; jinak FALSE.

*vtsParams*<br/>
Posloupnost **VTS_** konstant, která určuje typy parametrů pro událost. Jedná se o stejné konstanty, které se používají v položkách mapy odeslání, například DISP_FUNCTION.

### <a name="remarks"></a>Poznámky

Argument *vtsParams* je mezerou oddělený seznam hodnot z **konstant y VTS_.** Jedna nebo více těchto hodnot oddělených mezerami (nikoli čárkami) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

určuje seznam obsahující krátké celé číslo následované BOOL.

Seznam **konstant VTS_** naleznete v [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="on_event_range"></a><a name="on_event_range"></a>ON_EVENT_RANGE

Pomocí ON_EVENT_RANGE makra definujte funkci obslužné rutiny události pro událost vypálenou libovolným ovládacím prvkem OLE, který má ID ovládacího prvku v souvislém rozsahu ID.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, do které patří mapa jímky této události.

*idPrvní*<br/>
ID ovládacího prvku prvního ovládacího prvku OLE v oblasti.

*idPoslední*<br/>
ID ovládacího prvku posledního ovládacího prvku OLE v oblasti.

*Dispid*<br/>
ID odeslání události vypálené ovládacím prvkem.

*pfnHandler*<br/>
Ukazatel na členská funkce, která zpracovává událost. Tato funkce by měla mít návratový typ BOOL, první parametr typu UINT (pro ID ovládacího prvku) a další typy parametrů, které odpovídají parametrům události (viz *vtsParams*). Funkce by měla vrátit HODNOTU TRUE, která označuje, že událost byla zpracována; jinak FALSE.

*vtsParams*<br/>
Posloupnost **VTS_** konstant, která určuje typy parametrů pro událost. První konstanta by měla být typu VTS_I4 pro ID ovládacího prvku. Jedná se o stejné konstanty, které se používají v položkách mapy odeslání, například DISP_FUNCTION.

### <a name="remarks"></a>Poznámky

Argument *vtsParams* je mezerou oddělený seznam hodnot z **konstant y VTS_.** Jedna nebo více těchto hodnot oddělených mezerami (nikoli čárkami) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

určuje seznam obsahující krátké celé číslo následované BOOL.

Seznam **konstant VTS_** naleznete v [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Příklad

Následující příklad ukazuje obslužnou rutinu události pro událost MouseDown implementovanou pro tři ovládací prvky ( IDC_MYCTRL1 prostřednictvím IDC_MYCTRL3). Funkce obslužné rutiny události , `OnRangeMouseDown`je `CMyDlg`deklarována v souboru záhlaví třídy dialogu ( ) jako:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Níže uvedený kód je definován v souboru implementace třídy dialogu.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a>ON_EVENT_REFLECT

Makro ON_EVENT_REFLECT při použití v mapě jímky událostí obálky třídy ovládacího prvku OLE, obdrží události vyvolané ovládacím prvkem před jejich zpracováním kontejneru ovládacího prvku.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, do které patří mapa jímky této události.

*Dispid*<br/>
ID odeslání události vypálené ovládacím prvkem.

*pfnHandler*<br/>
Ukazatel na členská funkce, která zpracovává událost. Tato funkce by měla mít návratový typ BOOL a typy parametrů, které odpovídají parametrům události (viz *vtsParams*). Funkce by měla vrátit HODNOTU TRUE, která označuje, že událost byla zpracována; jinak FALSE.

*vtsParams*<br/>
Posloupnost **VTS_** konstant, která určuje typy parametrů pro událost. Jedná se o stejné konstanty, které se používají v položkách mapy odeslání, například DISP_FUNCTION.

### <a name="remarks"></a>Poznámky

Argument *vtsParams* je mezerou oddělený seznam hodnot z **konstant y VTS_.**

Jedna nebo více těchto hodnot oddělených mezerami (nikoli čárkami) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

určuje seznam obsahující krátké celé číslo následované BOOL.

Seznam **konstant VTS_** naleznete v [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="on_propnotify"></a><a name="on_propnotify"></a>ON_PROPNOTIFY

Pomocí ON_PROPNOTIFY makra definujte položku mapy jímky událostí pro zpracování oznámení vlastností z ovládacího prvku OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, do které patří mapa jímky této události.

*Id*<br/>
ID ovládacího prvku OLE.

*Dispid*<br/>
ID odeslání nemovitosti, která je součástí oznámení.

*pfnPožadavek*<br/>
Ukazatel na členská funkce, `OnRequestEdit` která zpracovává oznámení pro tuto vlastnost. Tato funkce by měla mít návratový typ BOOL a parametr **BOOL.** <strong>\*</strong> Tato funkce by měla nastavit parametr na HODNOTU TRUE, aby se vlastnost mohla změnit, a nepravda by měla být nepřípustná. Funkce by měla vrátit HODNOTU TRUE, která označuje, že oznámení bylo zpracováno. jinak FALSE.

*pfnZměněno*<br/>
Ukazatel na členská funkce, `OnChanged` která zpracovává oznámení pro tuto vlastnost. Funkce by měla mít návratový typ BOOL a parametr UINT. Funkce by měla vrátit TRUE označuje, že oznámení bylo zpracováno; jinak FALSE.

### <a name="remarks"></a>Poznámky

Argument *vtsParams* je mezerou oddělený seznam hodnot z **konstant y VTS_.** Jedna nebo více těchto hodnot oddělených mezerami (nikoli čárkami) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

určuje seznam obsahující krátké celé číslo následované BOOL.

Seznam **konstant VTS_** naleznete v [EVENT_CUSTOM](event-maps.md#event_custom).

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE

Pomocí ON_PROPNOTIFY_RANGE makra definujte položku mapy jímky událostí pro zpracování oznámení vlastností z libovolného ovládacího prvku OLE, který má ID ovládacího prvku v souvislém rozsahu ID.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, do které patří mapa jímky této události.

*idPrvní*<br/>
ID ovládacího prvku prvního ovládacího prvku OLE v oblasti.

*idPoslední*<br/>
ID ovládacího prvku posledního ovládacího prvku OLE v oblasti.

*Dispid*<br/>
ID odeslání nemovitosti, která je součástí oznámení.

*pfnPožadavek*<br/>
Ukazatel na členská funkce, `OnRequestEdit` která zpracovává oznámení pro tuto vlastnost. Tato funkce by `BOOL` měla `UINT` mít `BOOL*` návratový typ a parametry. Funkce by měla nastavit parametr na HODNOTU TRUE, aby se vlastnost mohla změnit, a nepravda by měla být nepřípustná. Funkce by měla vrátit TRUE označuje, že oznámení bylo zpracováno; jinak FALSE.

*pfnZměněno*<br/>
Ukazatel na členská funkce, `OnChanged` která zpracovává oznámení pro tuto vlastnost. Funkce by měla `BOOL` mít návratový typ a `UINT` parametr. Funkce by měla vrátit TRUE označuje, že oznámení bylo zpracováno; jinak FALSE.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT

Makro ON_PROPNOTIFY_REFLECT při použití v mapě jímky událostí obálky třídy ovládacího prvku OLE obdrží oznámení vlastností odeslaná ovládacím prvkem před jejich zpracováním kontejnerem ovládacího prvku.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, do které patří mapa jímky této události.

*Dispid*<br/>
ID odeslání nemovitosti, která je součástí oznámení.

*pfnPožadavek*<br/>
Ukazatel na členská funkce, `OnRequestEdit` která zpracovává oznámení pro tuto vlastnost. Tato funkce by měla mít návratový typ BOOL a parametr **BOOL.** <strong>\*</strong> Tato funkce by měla nastavit parametr na HODNOTU TRUE, aby se vlastnost mohla změnit, a nepravda by měla být nepřípustná. Funkce by měla vrátit HODNOTU TRUE, která označuje, že oznámení bylo zpracováno. jinak FALSE.

*pfnZměněno*<br/>
Ukazatel na členská funkce, `OnChanged` která zpracovává oznámení pro tuto vlastnost. Funkce by měla mít návratový typ BOOL a žádné parametry. Funkce by měla vrátit HODNOTU TRUE, která označuje, že oznámení bylo zpracováno. jinak FALSE.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
