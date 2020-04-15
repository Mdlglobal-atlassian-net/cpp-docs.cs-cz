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
ms.openlocfilehash: 5ee4101302322a5212a80b32f095cdd13d9769e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352288"
---
# <a name="ccmdtarget-class"></a>CCmdTarget – třída

Základní třída pro architekturu mapy zpráv knihovny tříd microsoft foundation.

## <a name="syntax"></a>Syntaxe

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Vytvoří `CCmdTarget` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Zobrazí kurzor jako kurzor přesýpacích hodin.|
|[CCmdTarget::DoOleVerb](#dooleverb)|Způsobí, že akce určená slovesem OLE má být provedena.|
|[CCmdTarget::EnableAutomation](#enableautomation)|Umožňuje automatizaci `CCmdTarget` OLE pro objekt.|
|[CCmdTarget::EnableConnections](#enableconnections)|Povolí spuštění události přes spojovací body.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Povolí knihovnu typů objektu.|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Vrátí se na předchozí kurzor.|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Vyjmenovává slovesa OLE objektu.|
|[CCmdTarget::FromIDispatch](#fromidispatch)|Vrátí ukazatel na `CCmdTarget` objekt přidružený `IDispatch` k ukazateli.|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Získá ID primárního rozhraní odeslání.|
|[CCmdTarget::GetIDispatch](#getidispatch)|Vrátí ukazatel na `IDispatch` objekt přidružený `CCmdTarget` k objektu.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Načte počet rozhraní informace o typu, které poskytuje objekt.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Načte popis typu, který odpovídá zadanému identifikátoru GUID.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Získá ukazatel na knihovnu typů.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Získá mezipaměti knihovny typů.|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Umožňuje vyvolání metody automatizace.|
|[CCmdTarget::IsResultExpected](#isresultexpected)|Vrátí nenulovou, pokud by funkce automatizace měla vrátit hodnotu.|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Trasy a odesílá příkazové zprávy.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Vyčistí po vydání posledního odkazu OLE.|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Obnoví kurzor přesýpacích hodin.|

## <a name="remarks"></a>Poznámky

Mapa zpráv směruje příkazy nebo zprávy do členských funkcí, které zapisujete, aby je zvládala. (Příkaz je zpráva z položky nabídky, příkazového tlačítka nebo klávesy akcelerátoru.)

Klíčové framework třídy `CCmdTarget` odvozené z patří [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)a [CFrameWnd](../../mfc/reference/cframewnd-class.md). Pokud máte v úmyslu pro novou třídu pro zpracování `CCmdTarget`zpráv, odvodit třídu z jedné z těchto odvozených tříd. Zřídka bude odvodit `CCmdTarget` třídu přímo.

Přehled cílů příkazů a `OnCmdMsg` směrování naleznete v [tématu Command Targets](../../mfc/command-targets.md), [Command Routing](../../mfc/command-routing.md)a Mapping [Messages](../../mfc/mapping-messages.md).

`CCmdTarget`obsahuje členské funkce, které zpracovávají zobrazení kurzoru přesýpacích hodin. Zobrazení kurzor přesýpacích hodin, pokud očekáváte, že příkaz trvat znatelný časový interval ke spuštění.

Odeslání mapy, podobně jako mapy zpráv, `IDispatch` se používají k vystavení funkce automatizace OLE. Vystavením tohoto rozhraní mohou do aplikace volat jiné aplikace (například Visual Basic).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="ccmdtargetbeginwaitcursor"></a><a name="beginwaitcursor"></a>CCmdTarget::BeginWaitCursor

Volání této funkce zobrazí kurzor jako přesýpací hodiny, když očekáváte, že příkaz trvat znatelný časový interval spustit.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto funkci, aby uživateli zobrazilo, že je zaneprázdněn, například když se `CDocument` objekt načte nebo uloží do souboru.

Akce `BeginWaitCursor` nejsou vždy účinné mimo jednu obslužnou `OnSetCursor` rutinu zprávy jako jiné akce, jako je například zpracování, může změnit kurzor.

Volání `EndWaitCursor` obnovit předchozí kurzor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetccmdtarget"></a><a name="ccmdtarget"></a>CCmdTarget::CCmdTarget

Vytvoří `CCmdTarget` objekt.

```
CCmdTarget();
```

## <a name="ccmdtargetdooleverb"></a><a name="dooleverb"></a>CCmdTarget::DoOleVerb

Způsobí, že akce určená slovesem OLE má být provedena.

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*iSponož*<br/>
Číselný identifikátor slovesa.

*lpMsg*<br/>
Ukazatel na strukturu [MSG](/windows/win32/api/winuser/ns-winuser-msg) popisující událost (například poklepání), která vyvolala sloveso.

*hWndParent*<br/>
Popisovač okna dokumentu obsahujícího objekt.

*lpRect*<br/>
Ukazatel na [rect](/previous-versions/dd162897\(v=vs.85\)) struktury obsahující souřadnice v obrazových bodech, které definují ohraničující obdélník objektu v *hwndParent*.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu, jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je v podstatě implementace [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Možné akce jsou výčtu [CCmdTarget::EnumOleVerbs](#enumoleverbs).

## <a name="ccmdtargetenableautomation"></a><a name="enableautomation"></a>CCmdTarget::EnableAutomation

Volání této funkce povolit automatizaci OLE pro objekt.

```
void EnableAutomation();
```

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána z konstruktoru objektu a měla by být volána pouze v případě, že byla deklarována mapa odeslání pro třídu. Další informace o automatizaci naleznete v článcích [Automation Clients](../../mfc/automation-clients.md) and [Automation Servers](../../mfc/automation-servers.md).

## <a name="ccmdtargetenableconnections"></a><a name="enableconnections"></a>CCmdTarget::EnableConnections

Povolí spuštění události přes spojovací body.

```
void EnableConnections();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit spojovací body, volání této členské funkce v konstruktoru odvozené třídy.

## <a name="ccmdtargetenabletypelib"></a><a name="enabletypelib"></a>CCmdTarget::EnableTypeLib

Povolí knihovnu typů objektu.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Poznámky

Volání této členské funkce v `CCmdTarget`konstruktoru objektu odvozeného, pokud poskytuje informace o typu.

## <a name="ccmdtargetendwaitcursor"></a><a name="endwaitcursor"></a>CCmdTarget::EndWaitCursor

Volání této funkce po `BeginWaitCursor` volání členské funkce pro návrat z kurzoru přesýpacích hodin na předchozí kurzor.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Poznámky

Rozhraní Framework také volá tuto členská funkci poté, co volá kurzor přesýpacích hodin.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetenumoleverbs"></a><a name="enumoleverbs"></a>CCmdTarget::EnumOleVerbs

Vyjmenovává slovesa OLE objektu.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Parametry

*ppenumOleVerb*<br/>
Ukazatel na ukazatel rozhraní [IEnumOLEVERB.](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud objekt podporuje alespoň jedno sloveso OLE (v takovém případě \* *ppenumOleVerb* odkazuje na rozhraní čítače výčtu), `IEnumOLEVERB` jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je v podstatě implementace [IOleObject::EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

## <a name="ccmdtargetfromidispatch"></a><a name="fromidispatch"></a>CCmdTarget::FromIDispatch

Volání této funkce `IDispatch` mapovat ukazatel, přijaté z automatizace `CCmdTarget` členské funkce třídy do `IDispatch` objektu, který implementuje rozhraní objektu.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Ukazatel na `IDispatch` objekt.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CCmdTarget` objekt přidružený k *lpDispatch*. Tato funkce vrátí `IDispatch` hodnotu NULL, pokud objekt `IDispatch` není rozpoznán jako objekt třídy Microsoft Foundation.

### <a name="remarks"></a>Poznámky

Výsledkem této funkce je inverzní volání členské `GetIDispatch`funkce .

## <a name="ccmdtargetgetdispatchiid"></a><a name="getdispatchiid"></a>CCmdTarget::GetDispatchIID

Získá ID primárního rozhraní odeslání.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
Ukazatel na ID rozhraní [(identifikátor GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu, jinak FALSE. Pokud je \* *úspěšná, pIID* je nastavena na ID primárního rozhraní odeslání.

### <a name="remarks"></a>Poznámky

Odvozené třídy by měly přepsat tuto `GetDispatchIID` členská funkci (pokud není přepsána, vrátí hodnotu FALSE). Viz [COleControl](../../mfc/reference/colecontrol-class.md).

## <a name="ccmdtargetgetidispatch"></a><a name="getidispatch"></a>CCmdTarget::GetIDispatch

Volání této členské funkce `IDispatch` načíst ukazatel z metody `IDispatch` automatizace, `IDispatch` která buď vrátí ukazatel nebo má ukazatel odkazem.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parametry

*bAddRef*<br/>
Určuje, zda se má počet odkazů pro objekt narůstat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `IDispatch` přidružený k objektu.

### <a name="remarks"></a>Poznámky

Pro objekty, které volají `EnableAutomation` ve svých konstruktorech, což je automatizace `IDispatch` povolena, tato funkce vrátí `IDispatch` ukazatel na implementaci třídy nadace, která je používána klienty, kteří komunikují prostřednictvím rozhraní. Volání této funkce automaticky přidá odkaz na ukazatel, takže není nutné volat [iUnknown::AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref).

## <a name="ccmdtargetgettypeinfocount"></a><a name="gettypeinfocount"></a>CCmdTarget::GetTypeInfoCount

Načte počet rozhraní informace o typu, které poskytuje objekt.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet rozhraní informací o typu.

### <a name="remarks"></a>Poznámky

Tato členská funkce v podstatě implementuje [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Odvozené třídy by měly přepsat tuto funkci vrátit počet typů informačnírozhraní k dispozici (buď 0 nebo 1). Pokud není přepsána, `GetTypeInfoCount` vrátí hodnotu 0. Chcete-li přepsat, použijte [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) makro, `GetTypeLib` `GetTypeLibCache`které také implementuje a .

## <a name="ccmdtargetgettypeinfoofguid"></a><a name="gettypeinfoofguid"></a>CCmdTarget::GetTypeInfoOfGuid

Načte popis typu, který odpovídá zadanému identifikátoru GUID.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Identifikátor národního `LCID`prostředí ( ).

*Identifikátor guid*<br/>
[Identifikátor GUID](/previous-versions/cc317743(v%3dmsdn.10)) popisu typu.

*ppTypeInfo*<br/>
Ukazatel na ukazatel `ITypeInfo` na rozhraní.

### <a name="return-value"></a>Návratová hodnota

HRESULT označující úspěch nebo neúspěch volání. Pokud je \* úspěšná, *ppTypeInfo* odkazuje na rozhraní informace o typu.

## <a name="ccmdtargetgettypelib"></a><a name="gettypelib"></a>CCmdTarget::GetTypeLib

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

HRESULT označující úspěch nebo neúspěch volání. Pokud je \* úspěšná, *ppTypeLib* odkazuje na rozhraní knihovny typů.

### <a name="remarks"></a>Poznámky

Odvozené třídy by měly přepsat tuto `GetTypeLib` členskou funkci (pokud není přepsána, vrátí TYPE_E_CANTLOADLIBRARY). Použijte [makro IMPLEMENT_OLETYPELIB,](../../mfc/reference/type-library-access.md#implement_oletypelib) které `GetTypeInfoCount` také `GetTypeLibCache`implementuje a .

## <a name="ccmdtargetgettypelibcache"></a><a name="gettypelibcache"></a>CCmdTarget::GetTypeLibCache

Získá mezipaměti knihovny typů.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CTypeLibCache` objekt.

### <a name="remarks"></a>Poznámky

Odvozené třídy by měly přepsat tuto `GetTypeLibCache` člennou funkci (pokud není přepsána, vrátí hodnotu NULL). Použijte [makro IMPLEMENT_OLETYPELIB,](../../mfc/reference/type-library-access.md#implement_oletypelib) které `GetTypeInfoCount` také `GetTypeLib`implementuje a .

## <a name="ccmdtargetisinvokeallowed"></a><a name="isinvokeallowed"></a>CCmdTarget::IsInvokeAllowed

Tato funkce je volána implementací knihovny `IDispatch::Invoke` MFC k určení, zda lze vyvolat danou metodu automatizace (identifikovanou *dispidem).*

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
ID odeslání.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud lze metodu vyvolat, jinak FALSE.

### <a name="remarks"></a>Poznámky

Pokud `IsInvokeAllowed` vrátí `Invoke` true, pokračuje volání metody; v `Invoke` opačném případě se nezdaří, vrací E_UNEXPECTED.

Odvozené třídy mohou přepsat tuto funkci vrátit příslušné `IsInvokeAllowed` hodnoty (pokud nejsou přepsány, vrátí hodnotu TRUE). Viz zejména [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

## <a name="ccmdtargetisresultexpected"></a><a name="isresultexpected"></a>CCmdTarget::IsResultExpected

Slouží `IsResultExpected` ke zjištění, zda klient očekává vrácenou hodnotu z jeho volání funkce automatizace.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud by funkce automatizace měla vrátit hodnotu; jinak 0.

### <a name="remarks"></a>Poznámky

Rozhraní OLE poskytuje knihovně MFC informace o tom, zda klient používá nebo ignoruje výsledek volání funkce a knihovna MFC zase používá tyto informace k určení výsledku volání `IsResultExpected`. Pokud je výroba vrácené hodnoty časově nebo prostředky náročná, můžete zvýšit efektivitu voláním této funkce před výpočtem vrácené hodnoty.

Tato funkce vrátí 0 pouze jednou, takže získáte platné vrácené hodnoty z jiných funkcí automatizace, pokud je zavoláte z funkce automatizace, kterou klient zavolal.

`IsResultExpected`vrátí nenulovou hodnotu, pokud je volána, když neprobíhá volání funkce automatizace.

## <a name="ccmdtargetoncmdmsg"></a><a name="oncmdmsg"></a>CCmdTarget::OnCmdMsg

Volat rámci směrovat a odesílat příkazzprávy a zpracování aktualizace příkazu objekty uživatelského rozhraní.

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Obsahuje ID příkazu.

*nKód*<br/>
Identifikuje kód oznámení příkazu. Další informace o hodnotách pro *nCode*naleznete v **tématu Poznámky.**

*pExtra*<br/>
Používá se podle hodnoty *nCode*. Další **Remarks** informace o *pExtra*.

*pHandlerInfo*<br/>
Pokud ne `OnCmdMsg` NULL, vyplní *pTarget* a *pmf* členy *pHandlerInfo* struktury namísto odeslání příkazu. Tento parametr by měl být obvykle null.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zpráva zpracována; jinak 0.

### <a name="remarks"></a>Poznámky

Toto je hlavní implementace rutiny architektury příkazu rozhraní.

Za běhu `OnCmdMsg` odešle příkaz do jiných objektů nebo zpracovává samotný příkaz `CCmdTarget::OnCmdMsg`voláním kořenové třídy , která provádí skutečné vyhledávání mapy zpráv. Úplný popis výchozího směrování příkazů naleznete v tématu [Témata zpracování zpráv a mapování](../../mfc/message-handling-and-mapping.md).

Ve výjimečných případech můžete chtít přepsat tuto členskou funkci rozšířit rozhraní standardní příkaz směrování. Další podrobnosti o architektuře směrování příkazů naleznete v [technické poznámce 21.](../../mfc/tn021-command-and-message-routing.md)

`OnCmdMsg`Pokud přepíšete , musíte zadat příslušnou hodnotu pro *nCode*, kód oznámení příkazu a *pExtra*, který závisí na hodnotě *nCode*. V následující tabulce jsou uvedeny odpovídající hodnoty:

|*nHodnota Kódu*|hodnota *pExtra*|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

## <a name="ccmdtargetonfinalrelease"></a><a name="onfinalrelease"></a>CCmdTarget::OnFinalRelease

Volat rámci při uvolnění poslední ole odkaz na nebo z objektu.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci poskytnout zvláštní zpracování pro tuto situaci. Výchozí implementace odstraní objekt.

## <a name="ccmdtargetrestorewaitcursor"></a><a name="restorewaitcursor"></a>CCmdTarget::RestoreWaitCursor

Volání této funkce obnovit odpovídající kurzor přesýpacích hodin po změně kurzoru systému (například po otevření a zavření okna se zprávou, zatímco uprostřed zdlouhavé operace).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI – třída](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp – třída](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)<br/>
[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver – třída](../../mfc/reference/coledispatchdriver-class.md)
