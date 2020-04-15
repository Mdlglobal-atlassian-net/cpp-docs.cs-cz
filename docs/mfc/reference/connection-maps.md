---
title: Mapy připojení
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 947cd09023ef4028a32db8e2e4e8b33f7e04e0dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374804"
---
# <a name="connection-maps"></a>Mapy připojení

Ole ovládací prvky jsou schopny vystavit rozhraní pro jiné aplikace. Tato rozhraní umožňují pouze přístup z kontejneru do tohoto ovládacího prvku. Pokud ovládací prvek OLE chce získat přístup k externím rozhraním jiných objektů OLE, musí být vytvořen spojovací bod. Tento spojovací bod umožňuje ovládací prvek odchozí přístup k externí masy odeslání, jako jsou mapy událostí nebo funkce oznámení.

Knihovna tříd Microsoft Foundation nabízí programovací model, který podporuje spojovací body. V tomto modelu "mapy připojení" se používají k určení rozhraní nebo spojovací body pro ovládací prvek OLE. Mapy připojení obsahují jedno makro pro každý spojovací bod. Další informace o mapách připojení naleznete v třídě [CConnectionPoint.](../../mfc/reference/cconnectionpoint-class.md)

Ovládací prvek obvykle podporuje pouze dva body připojení: jeden pro události a jeden pro oznámení vlastností. Ty jsou implementovány `COleControl` základní třídy a vyžadují žádné další práce zapisovačovládacího prvku. Všechny další spojovací body, které chcete implementovat ve vaší třídě, musí být přidány ručně. Pro podporu map připojení a bodů knihovna MFC poskytuje následující makra:

### <a name="connection-map-declaration-and-demarcation"></a>Deklarace a vymezení mapy připojení

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Deklaruje vložené třídy, která implementuje další bod připojení (musí být použit v deklaraci třídy).|
|[END_CONNECTION_PART](#end_connection_part)|Ukončí deklaraci spojovacího bodu (musí být použit v deklaraci třídy).|
|[CONNECTION_IID](#connection_iid)|Určuje ID rozhraní spojovacího bodu ovládacího prvku.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Deklaruje, že mapa připojení bude použita ve třídě (musí být použita v deklaraci třídy).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Začíná definice mapy připojení (musí být použitv implementaci třídy).|
|[END_CONNECTION_MAP](#end_connection_map)|Ukončí definici mapy připojení (musí být použitv implementaci třídy).|
|[CONNECTION_PART](#connection_part)|Určuje spojovací bod v mapě připojení ovládacího prvku.|

Následující funkce pomáhají jímce při navazování a odpojení připojení pomocí spojovacích bodů:

### <a name="initializationtermination-of-connection-points"></a>Inicializace/ukončení spojovacích bodů

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Naváže spojení mezi zdrojem a jímkou.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Přeruší spojení mezi zdrojem a jímkou.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a>BEGIN_CONNECTION_PART

Pomocí BEGIN_CONNECTION_PART makru zahajte definici dalších spojovacích bodů nad rámec bodů připojení událostí a vlastností.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy ovládacího prvku, jejíž spojovací bod se nachází.

*localClass*<br/>
Určuje název místní třídy, která implementuje spojovací bod.

### <a name="remarks"></a>Poznámky

V souboru deklarace (.h), který definuje členské funkce pro vaši třídu, spusťte spojovací bod s BEGIN_CONNECTION_PART makra, přidejte makro CONNECTION_IID a všechny další členské funkce, které chcete implementovat, a dokončete mapu spojovacího bodu pomocí END_CONNECTION_PART makra.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="end_connection_part"></a><a name="end_connection_part"></a>END_CONNECTION_PART

Ukončí deklaraci spojovacího bodu.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Parametry

*localClass*<br/>
Určuje název místní třídy, která implementuje spojovací bod.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="connection_iid"></a><a name="connection_iid"></a>CONNECTION_IID

Pomocí maker BEGIN_CONNECTION_PART a END_CONNECTION_PART definujte ID rozhraní pro bod připojení podporovaný ovládacím prvkem OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
ID rozhraní volaného spojovacím bodem.

### <a name="remarks"></a>Poznámky

Argument *iid* je ID rozhraní používané k identifikaci rozhraní, které bude spojovací bod volat na připojených jímky. Příklad:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

určuje spojovací bod, který `ISinkInterface` volá rozhraní.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP

Každá `COleControl`-derived třída v programu může poskytnout mapování připojení k určení dalších bodů připojení, které podporuje ovládací prvek.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Poznámky

Pokud ovládací prvek podporuje další body, použijte makro DECLARE_CONNECTION_MAP na konci deklarace třídy. Potom v souboru CPP, který definuje členské funkce pro třídu, použijte makro BEGIN_CONNECTION_MAP, CONNECTION_PART makra pro každý z bodů připojení ovládacího prvku a END_CONNECTION_MAP makro deklarovat konec mapy připojení.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP

Každá `COleControl`-derived třída v programu může poskytnout mapu připojení k určení spojovacíbody, které bude podporovat ovládací prvek.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy ovládacího prvku, jejíž mapování připojení se jedná.

*základna*<br/>
Určuje název základní třídy *Class*.

### <a name="remarks"></a>Poznámky

V implementaci (. CPP), který definuje členské funkce pro vaši třídu, spusťte mapu připojení s BEGIN_CONNECTION_MAP makra a přidejte položky maker pro každý z připojovacích bodů pomocí [CONNECTION_PART](#connection_part) makra. Nakonec dokončete mapu připojení s [END_CONNECTION_MAP](#end_connection_map) makru.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="end_connection_map"></a><a name="end_connection_map"></a>END_CONNECTION_MAP

Ukončí definici mapy připojení.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="connection_part"></a><a name="connection_part"></a>CONNECTION_PART

Mapuje spojovací bod pro ovládací prvek OLE na konkrétní ID rozhraní.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy ovládacího prvku, jejíž spojovací bod se nachází.

*Iid*<br/>
ID rozhraní volaného spojovacím bodem.

*localClass*<br/>
Určuje název místní třídy, která implementuje spojovací bod.

### <a name="remarks"></a>Poznámky

Příklad:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implementuje mapu připojení s bodem připojení, `IID_ISinkInterface` který volá rozhraní .

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a>AfxConnectionAdvise

Volání této funkce k navázání spojení mezi zdrojem, určené *pUnkSrc*a jímky, určené *pUnkSink*.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>Parametry

*pUnkSrc*<br/>
Ukazatel na objekt, který volá rozhraní.

*pUnkSink*<br/>
Ukazatel na objekt, který implementuje rozhraní.

*Iid*<br/>
ID rozhraní připojení.

*bRefCount*<br/>
True označuje, že vytvoření připojení by mělo způsobit zvýšení počtu odkazů *pUnkSink.* FALSE označuje, že počet odkazů by neměl být zpřísněn.

*pdwCookie*<br/>
Ukazatel na DWORD, kde je vrácenidentifikátor připojení. Tato hodnota by měla být předána `AfxConnectionUnadvise` jako parametr *dwCookie* při odpojení připojení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo navázáno připojení; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a>AfxConnectionUnadvise

Volání této funkce odpojit připojení mezi zdrojem, určené *pUnkSrc*a jímky, určené *pUnkSink*.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*pUnkSrc*<br/>
Ukazatel na objekt, který volá rozhraní.

*pUnkSink*<br/>
Ukazatel na objekt, který implementuje rozhraní.

*Iid*<br/>
ID rozhraní rozhraní spojovacího bodu.

*bRefCount*<br/>
True označuje, že odpojení připojení by mělo způsobit snížení počtu odkazů *pUnkSink.* FALSE označuje, že počet odkazů by neměl být snížen.

*dwCookie*<br/>
Identifikátor připojení vrácený společností `AfxConnectionAdvise`.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo připojení odpojeno; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
