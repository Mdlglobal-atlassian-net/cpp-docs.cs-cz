---
title: CCmdTarget – třída
ms.date: 11/04/2016
f1_keywords:
- CCmdTarget
- AFXWIN/CCmdTarget
- AFXWIN/CCmdTarget::CCmdTarget
- AFXWIN/CCmdTarget::BeginWaitCursor
- AFXWIN/CCmdTarget::DoOleVerb
- AFXWIN/CCmdTarget::EnableAutomation
- AFXWIN/CCmdTarget::EnableConnections
- AFXWIN/CCmdTarget::EnableTypeLib
- AFXWIN/CCmdTarget::EndWaitCursor
- AFXWIN/CCmdTarget::EnumOleVerbs
- AFXWIN/CCmdTarget::FromIDispatch
- AFXWIN/CCmdTarget::GetDispatchIID
- AFXWIN/CCmdTarget::GetIDispatch
- AFXWIN/CCmdTarget::GetTypeInfoCount
- AFXWIN/CCmdTarget::GetTypeInfoOfGuid
- AFXWIN/CCmdTarget::GetTypeLib
- AFXWIN/CCmdTarget::GetTypeLibCache
- AFXWIN/CCmdTarget::IsInvokeAllowed
- AFXWIN/CCmdTarget::IsResultExpected
- AFXWIN/CCmdTarget::OnCmdMsg
- AFXWIN/CCmdTarget::OnFinalRelease
- AFXWIN/CCmdTarget::RestoreWaitCursor
helpviewer_keywords:
- CCmdTarget [MFC], CCmdTarget
- CCmdTarget [MFC], BeginWaitCursor
- CCmdTarget [MFC], DoOleVerb
- CCmdTarget [MFC], EnableAutomation
- CCmdTarget [MFC], EnableConnections
- CCmdTarget [MFC], EnableTypeLib
- CCmdTarget [MFC], EndWaitCursor
- CCmdTarget [MFC], EnumOleVerbs
- CCmdTarget [MFC], FromIDispatch
- CCmdTarget [MFC], GetDispatchIID
- CCmdTarget [MFC], GetIDispatch
- CCmdTarget [MFC], GetTypeInfoCount
- CCmdTarget [MFC], GetTypeInfoOfGuid
- CCmdTarget [MFC], GetTypeLib
- CCmdTarget [MFC], GetTypeLibCache
- CCmdTarget [MFC], IsInvokeAllowed
- CCmdTarget [MFC], IsResultExpected
- CCmdTarget [MFC], OnCmdMsg
- CCmdTarget [MFC], OnFinalRelease
- CCmdTarget [MFC], RestoreWaitCursor
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
ms.openlocfilehash: e1b02da9914263017d637cb07b0f3b9f56cd6aa9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507709"
---
# <a name="ccmdtarget-class"></a>CCmdTarget – třída

Základní třída architektury mapy zpráv knihovna Microsoft Foundation Class.

## <a name="syntax"></a>Syntaxe

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CCmdTarget:: CCmdTarget](#ccmdtarget)|`CCmdTarget` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CCmdTarget:: BeginWaitCursor](#beginwaitcursor)|Zobrazí kurzor jako ukazatel na přesýpací hodiny.|
|[CCmdTarget::DoOleVerb](#dooleverb)|Způsobí provedení akce zadané v příkazu OLE.|
|[CCmdTarget:: EnableAutomation](#enableautomation)|Povoluje automatizaci OLE pro `CCmdTarget` objekt.|
|[CCmdTarget:: EnableConnections](#enableconnections)|Povolí vypínání událostí prostřednictvím bodů připojení.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Povoluje knihovnu typů objektu.|
|[CCmdTarget:: EndWaitCursor](#endwaitcursor)|Vrátí se na předchozí kurzor.|
|[CCmdTarget:: EnumOleVerbs](#enumoleverbs)|Vytvoří výčet příkazů OLE objektu.|
|[CCmdTarget:: FromIDispatch](#fromidispatch)|Vrátí ukazatel na `CCmdTarget` objekt přidružený `IDispatch` k ukazateli.|
|[CCmdTarget:: GetDispatchIID](#getdispatchiid)|Získá primární ID odesílajícího rozhraní.|
|[CCmdTarget:: GetIDispatch](#getidispatch)|Vrátí ukazatel na `IDispatch` objekt přidružený `CCmdTarget` k objektu.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Načte počet rozhraní informací o typu, které objekt poskytuje.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Načte popis typu, který odpovídá zadanému identifikátoru GUID.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Získá ukazatel na knihovnu typů.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Získá mezipaměť knihovny typů.|
|[CCmdTarget:: IsInvokeAllowed](#isinvokeallowed)|Povoluje vyvolání metody automatizace.|
|[CCmdTarget:: IsResultExpected](#isresultexpected)|Vrátí nenulovou hodnotu, pokud má funkce automatizace vracet hodnotu.|
|[CCmdTarget:: OnCmdMsg –](#oncmdmsg)|Směruje a odesílá zprávy příkazů.|
|[CCmdTarget:: OnFinalRelease](#onfinalrelease)|Vyčistí se po uvolnění posledního odkazu OLE.|
|[CCmdTarget:: RestoreWaitCursor](#restorewaitcursor)|Obnoví kurzor přesýpací hodiny.|

## <a name="remarks"></a>Poznámky

Mapa zpráv směruje příkazy nebo zprávy na členské funkce, které zapisujete pro jejich zpracování. (Příkaz je zpráva z položky nabídky, příkazového tlačítka nebo klávesy akcelerátoru.)

Třídy klíčového rozhraní odvozené `CCmdTarget` z zahrnout [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [objektu CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)a [CFrameWnd](../../mfc/reference/cframewnd-class.md). Pokud máte v úmyslu pro zpracování zpráv novou třídou, odvodit třídu z jedné z `CCmdTarget`těchto odvozených tříd. Nebudete jen zřídka odvozovat `CCmdTarget` třídu přímo.

Přehled cílů příkazů `OnCmdMsg` a směrování najdete v tématech [cíle příkazů](../../mfc/command-targets.md), [směrování příkazů](../../mfc/command-routing.md)a [mapování zpráv](../../mfc/mapping-messages.md).

`CCmdTarget`zahrnuje členské funkce, které zpracovávají zobrazení ukazatele přesýpací hodiny. Pokud očekáváte, že se má příkaz Spustit včas, zobrazte ukazatel přesýpacích hodin.

Mapy odeslání, podobně jako mapy zpráv, se používají k vystavení `IDispatch` funkcí automatizace technologie OLE. Po vystavení tohoto rozhraní můžou další aplikace (například Visual Basic) volat do vaší aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="beginwaitcursor"></a>CCmdTarget:: BeginWaitCursor

Voláním této funkce zobrazíte kurzor jako přesýpací hodiny, pokud očekáváte, že příkaz bude při spuštění trvat znatelné časové intervaly.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci, aby zobrazila uživatele, který je zaneprázdněný, například když `CDocument` objekt načítá nebo ukládá sám sebe do souboru.

Akce `BeginWaitCursor` nástroje nejsou vždy platné mimo jednu obslužnou rutinu zprávy, protože jiné akce, `OnSetCursor` jako je například zpracování, mohou změnit kurzor.

Volá `EndWaitCursor` se, aby se obnovil předchozí kurzor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>CCmdTarget:: CCmdTarget

`CCmdTarget` Vytvoří objekt.

```
CCmdTarget();
```

##  <a name="dooleverb"></a>CCmdTarget::D oOleVerb

Způsobí provedení akce zadané v příkazu OLE.

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Číselný identifikátor příkazu

*lpMsg*<br/>
Ukazatel na strukturu [zprávy](/windows/win32/api/winuser/ns-winuser-msg) popisující událost (například poklikání), která vyvolala příkaz.

*hWndParent*<br/>
Popisovač okna dokumentu obsahujícího objekt

*lpRect*<br/>
Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) obsahující souřadnice v pixelech, které definují ohraničující obdélník objektu v *hwndParent*.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je to úspěšné, jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je v podstatě implementace [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Možné akce jsou vyčísleny pomocí [CCmdTarget:: EnumOleVerbs](#enumoleverbs).

##  <a name="enableautomation"></a>CCmdTarget:: EnableAutomation

Voláním této funkce povolíte automatizaci OLE pro objekt.

```
void EnableAutomation();
```

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána z konstruktoru vašeho objektu a měla by být volána pouze v případě, že byla pro třídu deklarována mapa odeslání. Další informace o automatizaci najdete v článcích [Automatizace](../../mfc/automation-clients.md) a [automatizační servery](../../mfc/automation-servers.md).

##  <a name="enableconnections"></a>CCmdTarget:: EnableConnections

Povolí vypínání událostí prostřednictvím bodů připojení.

```
void EnableConnections();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit spojovací body, zavolejte tuto členskou funkci v konstruktoru vaší odvozené třídy.

##  <a name="enabletypelib"></a>CCmdTarget:: EnableTypeLib

Povoluje knihovnu typů objektu.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Poznámky

Volejte tuto členskou funkci v konstruktoru `CCmdTarget`odvozeného objektu, pokud poskytuje informace o typu.

##  <a name="endwaitcursor"></a>CCmdTarget:: EndWaitCursor

Tuto funkci volejte po `BeginWaitCursor` volání členské funkce, která se vrátí z kurzoru na předchozí kurzor.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Poznámky

Rozhraní také volá tuto členskou funkci poté, co se nazývá kurzor přesýpací hodiny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>CCmdTarget:: EnumOleVerbs

Vytvoří výčet příkazů OLE objektu.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Parametry

*ppenumOleVerb*<br/>
Ukazatel na ukazatel na rozhraní [IEnumOLEVERB](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb) .

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud objekt podporuje alespoň jednu akci OLE (v takovém případě \* *ppenumOleVerb* odkazuje na `IEnumOLEVERB` rozhraní enumerátoru), jinak false.

### <a name="remarks"></a>Poznámky

Tato členská funkce je v podstatě implementace [IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

##  <a name="fromidispatch"></a>CCmdTarget:: FromIDispatch

Voláním této funkce namapujete `IDispatch` ukazatel, přijatý od členských funkcí automatizace třídy, `CCmdTarget` do objektu, který `IDispatch` implementuje rozhraní objektu.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Ukazatel na `IDispatch` objekt.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CCmdTarget` objekt přidružený k *LPDISPATCH*. Tato funkce vrátí hodnotu null, `IDispatch` Pokud objekt není rozpoznán jako objekt Microsoft Foundation Class `IDispatch` .

### <a name="remarks"></a>Poznámky

Výsledek této funkce je inverzní k volání členské funkce `GetIDispatch`.

##  <a name="getdispatchiid"></a>CCmdTarget:: GetDispatchIID

Získá primární ID odesílajícího rozhraní.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parametry

*pIID*<br/>
Ukazatel na ID rozhraní ( [identifikátor GUID](/previous-versions/aa373931\(v=vs.80\))).

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je to úspěšné, jinak FALSE. V případě úspěchu \* se *piid* nastaví na primární ID odesílajícího rozhraní.

### <a name="remarks"></a>Poznámky

Odvozené třídy by měly přepsat tuto členskou funkci (Pokud není přepsána, `GetDispatchIID` vrátí hodnotu false). Viz [COleControl –](../../mfc/reference/colecontrol-class.md).

##  <a name="getidispatch"></a>CCmdTarget:: GetIDispatch

Zavolejte tuto členskou funkci, aby načetla `IDispatch` ukazatel z metody automatizace, která buď `IDispatch` vrací ukazatel, nebo převezme `IDispatch` ukazatel na základě odkazu.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parametry

*bAddRef*<br/>
Určuje, zda se má zvýšit počet odkazů pro objekt.

### <a name="return-value"></a>Návratová hodnota

`IDispatch` Ukazatel přidružený k objektu.

### <a name="remarks"></a>Poznámky

Pro objekty, které `EnableAutomation` volají své konstruktory, aby byly povoleny automatizace, tato funkce vrátí ukazatel na `IDispatch` implementaci základní třídy, kterou používají `IDispatch` klienti, kteří komunikují prostřednictvím rozhraní. Volání této funkce automaticky přidá odkaz na ukazatel, takže není nutné volat rozhraní [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref).

##  <a name="gettypeinfocount"></a>CCmdTarget:: GetTypeInfoCount

Načte počet rozhraní informací o typu, které objekt poskytuje.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet rozhraní informací o typu.

### <a name="remarks"></a>Poznámky

Tato členská funkce v podstatě implementuje rozhraní [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Odvozené třídy by měly přepsat tuto funkci, aby vracely počet zadaných rozhraní informací o typu (0 nebo 1). Pokud není přepsán `GetTypeInfoCount` , vrátí hodnotu 0. Pro přepsání použijte makro [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , které také implementuje `GetTypeLib` a. `GetTypeLibCache`

##  <a name="gettypeinfoofguid"></a>CCmdTarget:: GetTypeInfoOfGuid

Načte popis typu, který odpovídá zadanému identifikátoru GUID.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Identifikátor národního prostředí ( `LCID`).

*guid*<br/>
[Identifikátor GUID](/previous-versions/aa373931\(v=vs.80\)) popisu typu

*ppTypeInfo*<br/>
Ukazatel na ukazatel na `ITypeInfo` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT označující úspěch nebo neúspěch volání. V \* případě úspěchu *ppTypeInfo* odkazuje na rozhraní informace o typu.

##  <a name="gettypelib"></a>CCmdTarget:: GetTypeLib

Získá ukazatel na knihovnu typů.

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Identifikátor národního prostředí (LCID).

*ppTypeLib*<br/>
Ukazatel na ukazatel na `ITypeLib` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT označující úspěch nebo neúspěch volání. V případě úspěchu \* *ppTypeLib* odkazuje na rozhraní knihovny typů.

### <a name="remarks"></a>Poznámky

Odvozené třídy by měly přepsat tuto členskou funkci (Pokud není přepsána, `GetTypeLib` vrátí TYPE_E_CANTLOADLIBRARY). Použijte makro [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , které také implementuje `GetTypeInfoCount` a. `GetTypeLibCache`

##  <a name="gettypelibcache"></a>CCmdTarget:: GetTypeLibCache

Získá mezipaměť knihovny typů.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CTypeLibCache` objekt.

### <a name="remarks"></a>Poznámky

Odvozené třídy by měly přepsat tuto členskou funkci (Pokud není přepsána, `GetTypeLibCache` vrátí hodnotu null). Použijte makro [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , které také implementuje `GetTypeInfoCount` a. `GetTypeLib`

##  <a name="isinvokeallowed"></a>CCmdTarget:: IsInvokeAllowed

Tato funkce je volána implementací `IDispatch::Invoke` knihovny MFC pro určení, zda lze vyvolat danou metodu automatizace (identifikovanou identifikátorem *DISPID*).

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*dispid*<br/>
ID odeslání.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je možné metodu vyvolat, jinak FALSE.

### <a name="remarks"></a>Poznámky

Pokud `IsInvokeAllowed` vrátí hodnotu true `Invoke` , pokračuje `Invoke` v volání metody. v opačném případě selže, vrátí E_UNEXPECTED.

Odvozené třídy mohou přepsat tuto funkci, aby vracely příslušné hodnoty (pokud nejsou `IsInvokeAllowed` přepsány, vrátí hodnotu true). Viz zejména [COleControl –:: IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

##  <a name="isresultexpected"></a>CCmdTarget:: IsResultExpected

Slouží `IsResultExpected` k zjištění, zda klient očekává návratovou hodnotu z volání funkce automatizace.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud by funkce automatizace měla vracet hodnotu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Rozhraní OLE poskytuje informace do knihovny MFC o tom, zda klient používá nebo ignoruje výsledek volání funkce, a knihovna MFC následně používá tyto informace k určení výsledku volání `IsResultExpected`. Pokud je produkce návratové hodnoty náročná na čas nebo prostředky, můžete zvýšit efektivitu voláním této funkce před výpočtem návratové hodnoty.

Tato funkce vrací 0 pouze jednou, takže budete platné návratové hodnoty z jiných funkcí automatizace, pokud je voláte z funkce automatizace, kterou klient volal.

`IsResultExpected`vrací nenulovou hodnotu, pokud je volána, když volání funkce automatizace neprobíhá.

##  <a name="oncmdmsg"></a>CCmdTarget:: OnCmdMsg –

Volá se rozhraním, aby se odeslaly zprávy příkazů pro směrování a odeslání a aby se zpracovala aktualizace objektů uživatelského rozhraní příkazu.

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Obsahuje ID příkazu.

*nCode*<br/>
Identifikuje kód oznámení příkazu. Další informace o hodnotách pro *nCode*najdete v tématu **poznámky** .

*pExtra*<br/>
Používá se v závislosti na hodnotě *nCode*. Další informace o *pExtra*najdete v tématu **poznámky** .

*pHandlerInfo*<br/>
Pokud není null, `OnCmdMsg` vyplní *pTarget* a *PMF* členové struktury *pHandlerInfo* místo odeslání příkazu. Tento parametr obvykle by měl mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je zpráva zpracována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Toto je hlavní rutina implementace architektury příkazu architektury.

V době `OnCmdMsg` běhu odešle příkaz do jiných objektů nebo zpracuje příkaz sám, a to voláním kořenové třídy `CCmdTarget::OnCmdMsg`, která provede aktuální vyhledávání mapy zprávy. Úplný popis výchozího směrování příkazů najdete v [tématech o zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md).

Ve výjimečných případech může být vhodné přepsat tuto členskou funkci tak, aby rozšířila standardní směrování příkazů rozhraní. Podrobné informace o architektuře směrování příkazů najdete v [technické poznámce 21](../../mfc/tn021-command-and-message-routing.md) .

Pokud `OnCmdMsg`přepíšete, je nutné dodat příslušnou hodnotu pro *nCode*, kód oznámení příkazu a *pExtra*, což závisí na hodnotě *nCode*. Následující tabulka uvádí jejich příslušné hodnoty:

|hodnota *nCode*|hodnota *pExtra*|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>CCmdTarget:: OnFinalRelease

Volá se rozhraním, když se uvolní poslední odkaz OLE na nebo z objektu.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Poznámky

Potlačením této funkce zajistíte speciální zpracování této situace. Výchozí implementace odstraní objekt.

##  <a name="restorewaitcursor"></a>CCmdTarget:: RestoreWaitCursor

Voláním této funkce obnovíte vhodný ukazatel na přesýpací hodiny po změně systémového kurzoru (například po otevření okna se zprávou a následném uzavření v průběhu operace s délkou).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Viz také:

[ACDUAL Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI – třída](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp – třída](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver – třída](../../mfc/reference/coledispatchdriver-class.md)
