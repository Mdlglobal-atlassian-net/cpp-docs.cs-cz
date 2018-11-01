---
title: Mapy připojení
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 388b3d1961f9c7cf3598db08a986c2205ac34bc5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624806"
---
# <a name="connection-maps"></a>Mapy připojení

Ovládací prvky OLE se zveřejňují rozhraní k ostatním aplikacím. Tato rozhraní povolení přístupu jenom z kontejneru do ovládacího prvku. Pokud ovládací prvek OLE požaduje pro přístup k externí rozhraní dalšími objekty OLE, musí vytvořit bod připojení. Tento spojovací bod umožňuje odchozí přístup k externím expediční mapy, jako je mapa událostí nebo funkce oznámení ovládacího prvku.

Knihovny Microsoft Foundation Class nabízí programovací model, který podporuje spojovací body. V tomto modelu "připojení mapuje" se používají k určení rozhraní nebo přípojných bodů ovládacího prvku OLE. Mapy připojení obsahovat jedno makro pro každý bod připojení. Další informace o připojení mapy, najdete v článku [cconnectionpoint –](../../mfc/reference/cconnectionpoint-class.md) třídy.

Obvykle bude ovládací prvek podporovat pouze dvě spojovací body: jeden pro události a jeden pro vlastnost oznámení. Tyto jsou implementované `COleControl` základní třídy a vyžadovat žádná další činnost tvůrci ovládacího prvku. Žádné další spojovací body, které chcete implementovat ve třídě musí přidat ručně. Pro podporu připojení mapy a body, knihovna MFC poskytuje následující makra:

### <a name="connection-map-declaration-and-demarcation"></a>Připojení mapování deklarace a Rozhraničení

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Deklaruje vložené třídy, která implementuje na další připojovací bod (musí se použít v deklaraci třídy).|
|[END_CONNECTION_PART](#end_connection_part)|Ukončí deklarace spojovací bod (musí se použít v deklaraci třídy).|
|[CONNECTION_IID](#connection_iid)|Určuje rozhraní ID bodu připojení ovládacího prvku.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Deklaruje, že připojení mapy se použije ve třídě (musí se použít v deklaraci třídy).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Začíná definici mapy připojení (musí být použitý v implementaci třídy).|
|[END_CONNECTION_MAP](#end_connection_map)|Ukončí definici mapy připojení (musí být použitý v implementaci třídy).|
|[CONNECTION_PART](#connection_part)|Určuje spojovací bod v mapování ovládacího prvku připojení.|

Následující funkce pomáhají jímka při navazování a odpojí připojení pomocí spojovací body:

### <a name="initializationtermination-of-connection-points"></a>Inicializace nebo ukončení spojovacích bodů

|||
|-|-|
|[Afxconnectionadvise –](#afxconnectionadvise)|Naváže připojení mezi zdroj a jímku.|
|[Afxconnectionunadvise –](#afxconnectionunadvise)|Zruší připojení mezi zdroj a jímku.|

##  <a name="begin_connection_part"></a>  BEGIN_CONNECTION_PART

Použíjte BEGIN_CONNECTION_PART – makro zahájíte definice další spojovací body nad rámec spojovací body oznámení událostí a vlastností.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje, že je název třídy ovládacího prvku, jehož přípojný bod to.

*localClass*<br/>
Určuje název místní třídy, která implementuje bod připojení.

### <a name="remarks"></a>Poznámky

V deklaraci (.h) souboru, který definuje členské funkce třídy je spojovací bod začínat BEGIN_CONNECTION_PART – makro pak přidejte CONNECTION_IID – makro a další členské funkce, které chcete implementovat a dokončete připojení bod mapy s END_CONNECTION_PART – makro

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="end_connection_part"></a>  END_CONNECTION_PART

Ukončí deklarace spojovací bod.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Parametry

*localClass*<br/>
Určuje název místní třídy, která implementuje bod připojení.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="connection_iid"></a>  CONNECTION_IID

Použijte mezi BEGIN_CONNECTION_PART a END_CONNECTION_PART makra k definování rozhraní ID bodu připojení nepodporuje ovládacího prvku OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Parametry

*identifikátor IID*<br/>
ID rozhraní rozhraní s názvem podle spojovací bod.

### <a name="remarks"></a>Poznámky

*Iid* argument je rozhraní ID sloužící k identifikaci rozhraní, které je spojovací bod zavolá na jeho připojené jímky. Příklad:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

Určuje bod připojení, která volá `ISinkInterface` rozhraní.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="declare_connection_map"></a>  DECLARE_CONNECTION_MAP

Každý `COleControl`-odvozené třídy ve svém programu můžete zadat mapu připojení k určení dalších spojovací body, které podporuje ovládacího prvku.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Poznámky

Pokud váš ovládací prvek podporuje další body, použijte DECLARE_CONNECTION_MAP – makro na konci deklaraci vaší třídy. Poté v souboru .cpp, který definuje členské funkce třídy, pomocí BEGIN_CONNECTION_MAP – makro CONNECTION_PART makra pro každou z ovládacího prvku spojovací body a END_CONNECTION_MAP – makro můžete deklarovat konec mapování připojení.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="begin_connection_map"></a>  BEGIN_CONNECTION_MAP

Každý `COleControl`-odvozené třídy ve svém programu můžete zadat mapu připojení k určení spojovací body, které bude váš ovládací prvek podporovat.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje, že je název třídy ovládacího prvku, namapujte tento parametr jehož připojení.

*theBase*<br/>
Určuje název základní třídy *theClass*.

### <a name="remarks"></a>Poznámky

V implementaci (. Soubor CPP), který definuje člena funkce pro třídu, začínat BEGIN_CONNECTION_MAP – makro mapu připojení a pak přidat makro položky pro každý z vašich bodů připojení pomocí [CONNECTION_PART](#connection_part) – makro. Nakonec proveďte mapování připojení se [END_CONNECTION_MAP](#end_connection_map) – makro.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="end_connection_map"></a>  END_CONNECTION_MAP

Ukončí definici mapy připojení.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="connection_part"></a>  CONNECTION_PART

Bod připojení pro ovládací prvek OLE se mapuje na ID konkrétní rozhraní.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje, že je název třídy ovládacího prvku, jehož přípojný bod to.

*identifikátor IID*<br/>
ID rozhraní rozhraní s názvem podle spojovací bod.

*localClass*<br/>
Určuje název místní třídy, která implementuje bod připojení.

### <a name="remarks"></a>Poznámky

Příklad:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implementuje mapu připojení se spojovacím bodem, který volá `IID_ISinkInterface` rozhraní.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="afxconnectionadvise"></a>  Afxconnectionadvise –

Voláním této funkce k navázání připojení mezi zdrojem určená *pUnkSrc*a jímky, určené *pUnkSink*.

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

*identifikátor IID*<br/>
ID rozhraní připojení.

*bRefCount*<br/>
Hodnota TRUE označuje, že vytváří připojení by měl způsobit, že počet odkazů *pUnkSink* k navýšení. Hodnota FALSE označuje, že by neměl být zvýšen počet odkazů.

*pdwCookie*<br/>
Ukazatel na DWORD, kde se vrátí identifikátor připojení. Tato hodnota by měla předávat jako *dwCookie* parametr `AfxConnectionUnadvise` při odpojení připojení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo vytvořeno připojení; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

##  <a name="afxconnectionunadvise"></a>  Afxconnectionunadvise –

Voláním této funkce se odpojit připojení mezi zdrojem určená *pUnkSrc*a jímky, určené *pUnkSink*.

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

*identifikátor IID*<br/>
Rozhraní ID bodu rozhraní připojení.

*bRefCount*<br/>
Hodnota TRUE označuje, že odpojení připojení by se měl počet odkazů *pUnkSink* chcete snížit. Hodnota FALSE označuje, že by neměl být snížen počet odkazů.

*dwCookie*<br/>
Identifikátor připojení vrácených `AfxConnectionAdvise`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo ukončeno připojení; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
