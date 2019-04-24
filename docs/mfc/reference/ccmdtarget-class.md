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
ms.openlocfilehash: 9314717fab53b1a89b87d657ec617a4c6bd45b8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206438"
---
# <a name="ccmdtarget-class"></a>CCmdTarget – třída

Základní třída architektury zpráva – mapa knihovny Microsoft Foundation Class.

## <a name="syntax"></a>Syntaxe

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Vytvoří `CCmdTarget` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Zobrazí kurzor přesýpacích hodin kurzoru.|
|[CCmdTarget::DoOleVerb](#dooleverb)|Způsobí, že určený operaci OLE provést akci.|
|[CCmdTarget::EnableAutomation](#enableautomation)|Umožňuje automatizaci OLE `CCmdTarget` objektu.|
|[CCmdTarget::EnableConnections](#enableconnections)|Umožňuje spouštění událostí přes spojovací body.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Povolí knihovnu typů objektu.|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Vrátí předchozí kurzoru.|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Podává výčet příkazů objektu OLE.|
|[CCmdTarget::FromIDispatch](#fromidispatch)|Vrací ukazatel `CCmdTarget` objekt přidružený k `IDispatch` ukazatele.|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Získá ID odbavení primární rozhraní.|
|[CCmdTarget::GetIDispatch](#getidispatch)|Vrací ukazatel `IDispatch` objekt přidružený k `CCmdTarget` objektu.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Získá počet rozhraní typu informací, které poskytuje objekt.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Načte popis typu, která odpovídá zadaným identifikátorem GUID.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Získá ukazatel na knihovnu typů.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Získá mezipaměť knihovny typů.|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Umožňuje vyvolání metody automatizace.|
|[CCmdTarget::IsResultExpected](#isresultexpected)|Vrátí nenulovou hodnotu, pokud automatizaci funkce by měla vrátit hodnotu.|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Trasy a odesílá zprávy příkazu.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Vyčištění po uvolnění posledního odkazu OLE.|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Obnoví kurzor přesýpacích hodin.|

## <a name="remarks"></a>Poznámky

Mapy zpráv směruje na členské funkce, který napíšete jejich zpracování příkazů nebo zprávy. (Příkaz je zpráva z položky nabídky, příkazového tlačítka nebo přístupová klávesa.)

Klíče rozhraní třídy odvozené z `CCmdTarget` zahrnují [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), a [ CFrameWnd](../../mfc/reference/cframewnd-class.md). Pokud máte v úmyslu pro novou třídu pro zpracování zpráv, odvoďte třídu z jednoho z těchto `CCmdTarget`-odvozené třídy. Jen zřídka se odvodit třídu z `CCmdTarget` přímo.

Přehled cíle příkazů a `OnCmdMsg` směrování, najdete v článku [cíle příkazů](../../mfc/command-targets.md), [směrování příkazů](../../mfc/command-routing.md), a [mapování zpráv](../../mfc/mapping-messages.md).

`CCmdTarget` zahrnuje členské funkce, které zpracovávají zobrazení přesýpacích hodin kurzoru. Pokud očekáváte, že příkaz má provést znatelný časový interval pro spuštění, zobrazí kurzor přesýpacích hodin.

Mapy, podobně jako mapy zpráv odesílání, se používají k vystavení automatizace OLE `IDispatch` funkce. Zveřejněním toto rozhraní může volat jiné aplikace (například Visual Basic) do vaší aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor

Voláním této funkce k zobrazení kurzor jako přesýpací hodiny, pokud očekáváte, že příkaz má provést znatelný časový interval pro spuštění.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci, aby uživatel věděl, že je zaneprázdněný, jako např. kdy `CDocument` objekt načte nebo uloží samotné do souboru.

Akce `BeginWaitCursor` nejsou vždy efektivní mimo obslužnou rutinu jedna zpráva jako další akce, jako například `OnSetCursor` zpracování, může změnit kurzor.

Volání `EndWaitCursor` obnovit předchozí kurzoru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>  CCmdTarget::CCmdTarget

Vytvoří `CCmdTarget` objektu.

```
CCmdTarget();
```

##  <a name="dooleverb"></a>  CCmdTarget::DoOleVerb

Způsobí, že určený operaci OLE provést akci.

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Číselný identifikátor příkazu.

*lpMsg*<br/>
Ukazatel [MSG](/windows/desktop/api/winuser/ns-winuser-msg) struktura popisující události (jako je například poklepání), která vyvolá příkaz.

*hWndParent*<br/>
Popisovač okna dokumentu obsahující objekt.

*lpRect*<br/>
Ukazatel [RECT](/previous-versions/dd162897\(v=vs.85\)) struktury obsahující souřadnice, v pixelech, které definují objekt ohraničovacího rámečku v *hwndParent*.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je úspěšná, jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je v podstatě implementace [Funkce IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb). Jsou ve výčtu možných akcí [CCmdTarget::EnumOleVerbs](#enumoleverbs).

##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation

Voláním této funkce umožňující automatizaci OLE pro objekt.

```
void EnableAutomation();
```

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána z konstruktoru objektu a by měla být volána pouze pokud je deklarovaná mapa odbavení pro třídu. Další informace o službě automation najdete v článcích [klientům automatizace](../../mfc/automation-clients.md) a [automatizační servery](../../mfc/automation-servers.md).

##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections

Umožňuje spouštění událostí přes spojovací body.

```
void EnableConnections();
```

### <a name="remarks"></a>Poznámky

Pokud chcete povolit spojovací body, zavolejte tuto členskou funkci v konstruktoru odvozené třídy.

##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib

Povolí knihovnu typů objektu.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Poznámky

Voláním této členské funkce v konstruktoru vaše `CCmdTarget`-odvozenému objektu, pokud obsahuje informace o typu.

##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor

Voláním této funkce, jakmile zavoláte `BeginWaitCursor` členská funkce vrácení z přesýpacích hodin kurzor na předchozí kurzor.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce volá framework i poté, co se používá označení přesýpacích hodin kurzoru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>  CCmdTarget::EnumOleVerbs

Podává výčet příkazů objektu OLE.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Parametry

*ppenumOleVerb*<br/>
Ukazatel na ukazatel [IEnumOLEVERB](/windows/desktop/api/oleidl/nn-oleidl-ienumoleverb) rozhraní.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud objekt podporuje alespoň jeden příkaz OLE (v takovém případě \* *ppenumOleVerb* odkazuje na `IEnumOLEVERB` enumerátor rozhraní), jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je v podstatě implementace [IOleObject::EnumVerbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs).

##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch

Voláním této funkce mapují `IDispatch` ukazatel přijatých ze služby automation členské funkce třídy, do `CCmdTarget` objekt, který implementuje rozhraní `IDispatch` objektu.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Ukazatel `IDispatch` objektu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CCmdTarget` objekt přidružený k *lpDispatch*. Tato funkce vrací hodnotu NULL, pokud `IDispatch` objektu nebyl rozpoznán jako Microsoft Foundation Class `IDispatch` objektu.

### <a name="remarks"></a>Poznámky

Výsledkem této funkce je inverzní funkce k volání na členskou funkci `GetIDispatch`.

##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID

Získá ID odbavení primární rozhraní.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parametry

*pIID*<br/>
Ukazatel na Identifikátor rozhraní ( [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931)).

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je úspěšná, jinak hodnota FALSE. V případě úspěšného ověření \* *pIID* je nastavena na ID odbavení primární rozhraní.

### <a name="remarks"></a>Poznámky

Odvozené třídy by měly přepsat tuto členskou funkci (Pokud přepsána nebyla, `GetDispatchIID` vrátí FALSE). Zobrazit [COleControl](../../mfc/reference/colecontrol-class.md).

##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch

Zavolat tuto členskou funkci načíst `IDispatch` ukazatel z metody automatizace této buď vrátí `IDispatch` ukazatel nebo přejdete `IDispatch` ukazatelem, odkazem.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parametry

*bAddRef*<br/>
Určuje, jestli se má zvýšit počet odkazů pro objekt.

### <a name="return-value"></a>Návratová hodnota

`IDispatch` Ukazatel přidružená k objektu.

### <a name="remarks"></a>Poznámky

Pro objekty Toto volání `EnableAutomation` v jejich konstruktory, díky kterým jsou automatizace povolena, tato funkce vrací ukazatel na implementaci Foundation Class `IDispatch` , který používají klienti, kteří komunikují prostřednictvím `IDispatch` rozhraní. Volání této funkce automaticky přidá odkaz na ukazatel, takže není nutné provádět volání [IUnknown::AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref).

##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount

Získá počet rozhraní typu informací, které poskytuje objekt.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet rozhraní typu informací.

### <a name="remarks"></a>Poznámky

Tato členská funkce je v podstatě implementuje [IDispatch::GetTypeInfoCount](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Odvozené třídy by měly přepsat této funkce vrátí počet rozhraní informací o typu (0 nebo 1). Pokud přepsána nebyla, `GetTypeInfoCount` vrátí hodnotu 0. Chcete-li přepsat, použijte [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) makra, která také implementuje `GetTypeLib` a `GetTypeLibCache`.

##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid

Načte popis typu, která odpovídá zadaným identifikátorem GUID.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Identifikátor národního prostředí ( `LCID`).

*identifikátor GUID*<br/>
[GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) popisu typu.

*ppTypeInfo*<br/>
Ukazatel na ukazatel `ITypeInfo` rozhraní.

### <a name="return-value"></a>Návratová hodnota

HRESULT označující úspěchu nebo neúspěchu volání. V případě úspěšného ověření \* *ppTypeInfo* odkazuje na rozhraní typu informací.

##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib

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
Ukazatel na ukazatel `ITypeLib` rozhraní.

### <a name="return-value"></a>Návratová hodnota

HRESULT označující úspěchu nebo neúspěchu volání. V případě úspěšného ověření \* *ppTypeLib* odkazuje na typ rozhraní knihovny.

### <a name="remarks"></a>Poznámky

Odvozené třídy by měly přepsat tuto členskou funkci (Pokud přepsána nebyla, `GetTypeLib` vrátí TYPE_E_CANTLOADLIBRARY). Použití [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) makra, která také implementuje `GetTypeInfoCount` a `GetTypeLibCache`.

##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache

Získá mezipaměť knihovny typů.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CTypeLibCache` objektu.

### <a name="remarks"></a>Poznámky

Odvozené třídy by měly přepsat tuto členskou funkci (Pokud přepsána nebyla, `GetTypeLibCache` vrátí hodnotu NULL). Použití [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) makra, která také implementuje `GetTypeInfoCount` a `GetTypeLib`.

##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed

Tato funkce je volána implementace MFC atributu `IDispatch::Invoke` k určení, zda daný automation – metoda (identifikovaný *dispid*) může být vyvolána.

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*dispid*<br/>
ID odbavení

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud metoda může být vyvolaný, jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud `IsInvokeAllowed` vrátí hodnotu TRUE, `Invoke` pokračuje k volání metody; v opačném případě `Invoke` selže a vrátí e_unexpected, je.

Odvozené třídy lze přepsat tato funkce vrací odpovídající hodnoty (Pokud přepsána nebyla, `IsInvokeAllowed` vrátí hodnotu PRAVDA). Viz zejména [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected

Použití `IsResultExpected` pro ověření, zda klient očekává, že návratová hodnota ze svého volání funkce automatizace.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud automatizaci funkce by měla vracet hodnotu; jinak 0.

### <a name="remarks"></a>Poznámky

Poskytuje informace ke knihovně MFC Určuje, zda klient používá nebo ignorování výsledek volání funkce rozhraní OLE a knihovna MFC zase používá tyto informace k určení výsledků volání `IsResultExpected`. Pokud je produkční návratovou hodnotu nebo prostředek náročné na čas, můžete zvýšit efektivitu před computingu návratová hodnota volání této funkce.

Tato funkce vrátí 0 pouze jednou, tak, aby se zobrazí platný vrácené hodnoty z jiných funkcí automatizace, když je zavoláte funkci služby automation, který má klienta volána.

`IsResultExpected` vrací nenulovou hodnotu, pokud je volána při volání funkce rozhraní automatizace neprobíhá.

##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg

Volá se rozhraním, aby se směrovaly a odesílaly zprávy příkazů a pro zpracování aktualizace objektů uživatelského rozhraní příkazu.

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
Určuje kód příkazu oznámení. Zobrazit **poznámky** pro další informace o hodnotách pro *nCode*.

*pExtra*<br/>
Použít podle hodnoty *nCode*. Zobrazit **poznámky** Další informace o *pExtra*.

*pHandlerInfo*<br/>
Pokud není NULL, `OnCmdMsg` vyplní *pTarget* a *pmf* členy *pHandlerInfo* struktura namísto odesílání příkazu. Tento parametr by měl obvykle mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se zpracovává zprávy; jinak 0.

### <a name="remarks"></a>Poznámky

Toto je hlavní implementace rutiny příkaz architektury framework.

V době běhu `OnCmdMsg` odešle příkaz k jiné objekty nebo zpracovává příkazu samého voláním kořenová třída `CCmdTarget::OnCmdMsg`, který nepodporuje vyhledávání skutečné mapování zprávy. Úplný popis výchozí směrování příkazů, naleznete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).

Ve výjimečných případech můžete chtít přepsat tato členská funkce pro rozšíření rozhraní framework standardního směrování příkazů. Odkazovat na [Technická poznámka 21](../../mfc/tn021-command-and-message-routing.md) pro další podrobnosti o architektuře směrování příkazů.

Pokud přepíšete `OnCmdMsg`, je nutné zadat má hodnotu vhodnou pro *nCode*, kód upozornění příkazu a *pExtra*, která závisí na hodnotě *nCode* . V následující tabulce jsou uvedeny jejich odpovídající hodnoty:

|*nCode* hodnota|*pExtra* hodnota|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>  CCmdTarget::OnFinalRelease

Volá se rozhraním při uvolnění posledního odkazu OLE do nebo z objektu.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Poznámky

Přepsání této funkce se zvláštní zpracování v této situaci. Výchozí implementace odstraní objekt.

##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor

Voláním této funkce obnovení odpovídající přesýpacích hodin kurzor po změně kurzor systému (třeba po okno se zprávou otevřel a uzavřel pak při uprostřed časově náročná operace).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC acdual –](../../overview/visual-cpp-samples.md)<br/>
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
