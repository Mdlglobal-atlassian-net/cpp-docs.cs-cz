---
title: "CCmdTarget – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0bdca1e4193be46a28739b01aed6e26e0e388b13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccmdtarget-class"></a>CCmdTarget – třída
Základní třída pro architekturu map zpráv Microsoft Foundation Class Library.  
  
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
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Zobrazí kurzor jako přesýpacích hodin kurzoru.|  
|[CCmdTarget::DoOleVerb](#dooleverb)|Způsobí, že akce určeného OLE operaci provést.|  
|[CCmdTarget::EnableAutomation](#enableautomation)|OLE – automatizace pro umožňuje `CCmdTarget` objektu.|  
|[CCmdTarget::EnableConnections](#enableconnections)|Umožňuje spouštění událostí prostřednictvím bodů připojení.|  
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Umožňuje knihovny typů objektu.|  
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Vrátí k předchozí kurzor.|  
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Vytvoří výčet příkazy OLE objektu.|  
|[CCmdTarget::FromIDispatch](#fromidispatch)|Vrátí ukazatel `CCmdTarget` objekt přidružený k `IDispatch` ukazatel.|  
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Získá ID expedice primární rozhraní.|  
|[CCmdTarget::GetIDispatch](#getidispatch)|Vrátí ukazatel `IDispatch` objekt přidružený k `CCmdTarget` objektu.|  
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Načte počet rozhraní typ informace, které poskytuje objekt.|  
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Načte popis typu, který odpovídá zadaným identifikátorem GUID.|  
|[CCmdTarget::GetTypeLib](#gettypelib)|Získá ukazatel na knihovny typů.|  
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Získá typ mezipaměti knihovny.|  
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Umožňuje vyvolání metody automatizace.|  
|[CCmdTarget::IsResultExpected](#isresultexpected)|Vrátí nenulové hodnoty, pokud automatizaci funkce by měl vrátit hodnotu.|  
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Trasy a odešle příkaz zprávy.|  
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Vyčistí po vydání odkaz na poslední OLE.|  
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Obnoví přesýpacích hodin kurzor.|  
  
## <a name="remarks"></a>Poznámky  
 Mapy zpráv směruje příkazy nebo zprávy členské funkce, které můžete psát k jejich zpracování. (Příkaz je zpráva z položky nabídky, příkazového tlačítka nebo klíče akcelerátoru.)  
  
 Klíče framework třídy odvozené od `CCmdTarget` zahrnují [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), a [ CFrameWnd](../../mfc/reference/cframewnd-class.md). Pokud máte v úmyslu pro novou třídu pro zpracování zprávy, odvození třídy z jednoho z těchto `CCmdTarget`-odvozených třídách. Občas bude odvození třídy z `CCmdTarget` přímo.  
  
 Přehled cíle příkazů a `OnCmdMsg` směrování, najdete v části [cíle příkazů](../../mfc/command-targets.md), [směrování příkazů](../../mfc/command-routing.md), a [mapování zpráv](../../mfc/mapping-messages.md).  
  
 `CCmdTarget`obsahuje členské funkce, které zpracovávají zobrazení přesýpacích hodin kurzoru. Zobrazte přesýpacích hodin kurzor, pokud očekáváte, že příkazu, který bude trvat znatelné časovém intervalu provést.  
  
 Mapy, podobně jako mapy zpráv odesílání, se používají k vystavení OLE – automatizace `IDispatch` funkce. Díky zpřístupnění toto rozhraní, můžete do své aplikace volat jiné aplikace (například Visual Basic).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="beginwaitcursor"></a>CCmdTarget::BeginWaitCursor  
 Volání této funkce zobrazuje kurzor jako přesýpací hodiny, pokud očekáváte, že příkazu, který bude trvat znatelné časovém intervalu provést.  
  
```  
void BeginWaitCursor();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se uživateli zobrazí, že je zaneprázdněný, jako např. kdy volá framework **CDocument** objekt načte nebo samotné uloží do souboru.  
  
 Akce `BeginWaitCursor` nejsou vždy efektivní mimo obslužnou rutinu jedné zprávy jako jiné akce, jako například `OnSetCursor` zpracování, by se mohly změnit kurzor.  
  
 Volání `EndWaitCursor` obnovit předchozí kurzor.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="ccmdtarget"></a>CCmdTarget::CCmdTarget  
 Vytvoří `CCmdTarget` objektu.  
  
```  
CCmdTarget();
```  
  
##  <a name="dooleverb"></a>CCmdTarget::DoOleVerb  
 Způsobí, že akce určeného OLE operaci provést.  
  
```  
BOOL DoOleVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Číselný identifikátor operace.  
  
 `lpMsg`  
 Ukazatel [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) struktura popisující událost (například poklikejte na soubor), která volá příkaz.  
  
 `hWndParent`  
 Popisovač okna dokumentu, který obsahuje objekt.  
  
 `lpRect`  
 Ukazatel [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura obsahující souřadnice v pixelech, které definují objekt je ohraničujícího rámečku v *hwndParent*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud úspěšný, jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je v podstatě implementací [Funkce IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508). Jsou ve výčtu možných akcí [CCmdTarget::EnumOleVerbs](#enumoleverbs).  
  
##  <a name="enableautomation"></a>CCmdTarget::EnableAutomation  
 Volejte tuto funkci povolit OLE – automatizace pro objekt.  
  
```  
void EnableAutomation();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je obvykle volána z konstruktoru objektu a by měla být volána pouze pokud bylo deklarováno expediční mapy pro třídu. Další informace o automatizaci najdete v článcích [klienti automatizace](../../mfc/automation-clients.md) a [automatizační servery](../../mfc/automation-servers.md).  
  
##  <a name="enableconnections"></a>CCmdTarget::EnableConnections  
 Umožňuje spouštění událostí prostřednictvím bodů připojení.  
  
```  
void EnableConnections();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete povolit spojovací body, volání této funkce členů v konstruktoru odvozené třídy.  
  
##  <a name="enabletypelib"></a>CCmdTarget::EnableTypeLib  
 Umožňuje knihovny typů objektu.  
  
```  
void EnableTypeLib();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce členů v konstruktoru vaší `CCmdTarget`– pokud poskytuje informace o typu odvozeného objektu. Další informace najdete v článku znalostní báze Knowledge Base Q185720, "postupy: poskytování informací o typu ze serveru automatizace MFC." Články znalostní báze jsou k dispozici na [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="endwaitcursor"></a>CCmdTarget::EndWaitCursor  
 Volání této funkce po můžete volat `BeginWaitCursor` – členská funkce vrácení z přesýpacích hodin kurzor na předchozí kurzor.  
  
```  
void EndWaitCursor();
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce volá framework také po volal přesýpacích hodin kurzor.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="enumoleverbs"></a>CCmdTarget::EnumOleVerbs  
 Vytvoří výčet příkazy OLE objektu.  
  
```  
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>Parametry  
 `ppenumOleVerb`  
 Ukazatel na ukazatel na [IEnumOLEVERB](http://msdn.microsoft.com/library/windows/desktop/ms695084) rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud objekt podporuje alespoň jeden příkaz OLE (v takovém případě \* `ppenumOleVerb` odkazuje na **IEnumOLEVERB** enumerátor rozhraní), jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je v podstatě implementací [IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781).  
  
##  <a name="fromidispatch"></a>CCmdTarget::FromIDispatch  
 Volání této funkce mapovat `IDispatch` ukazatele, obdržel z automatizace členské funkce třídy, do `CCmdTarget` objekt, který implementuje rozhraní z `IDispatch` objektu.  
  
```  
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDispatch`  
 Ukazatel na `IDispatch` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CCmdTarget` objekt přidružený k `lpDispatch`. Funkce vrátí hodnotu **NULL** Pokud `IDispatch` objektu nebyl rozpoznán jako třída Microsoft Foundation `IDispatch` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Výsledkem této funkce je inverzní volání funkce člen `GetIDispatch`.  
  
##  <a name="getdispatchiid"></a>CCmdTarget::GetDispatchIID  
 Získá ID expedice primární rozhraní.  
  
```  
virtual BOOL GetDispatchIID(IID* pIID);
```  
  
### <a name="parameters"></a>Parametry  
 *pIID*  
 Ukazatel na ID rozhraní ( [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931)).  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud úspěšný, jinak hodnota FALSE. V případě úspěšného \* *pIID* je nastaven na ID expedice primární rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Odvozené třídy by měly přepsat tuto – členská funkce (Pokud přepsána nejsou, `GetDispatchIID` vrátí hodnotu FALSE). V tématu [COleControl](../../mfc/reference/colecontrol-class.md).  
  
 Další informace najdete v článku znalostní báze Knowledge Base Q185720, "postupy: poskytování informací o typu ze serveru automatizace MFC." Články znalostní báze jsou k dispozici na [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="getidispatch"></a>CCmdTarget::GetIDispatch  
 Volání této funkce člen načíst `IDispatch` ukazatel z metody automatizace této buď vrátí `IDispatch` ukazatel nebo trvá `IDispatch` ukazatel odkazem.  
  
```  
LPDISPATCH GetIDispatch(BOOL bAddRef);
```  
  
### <a name="parameters"></a>Parametry  
 *bAddRef*  
 Určuje, jestli se má zvýšit počet odkazů pro daný objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 `IDispatch` Ukazatel přidružená k objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pro objekty tohoto volání `EnableAutomation` v jejich konstruktory přitom automatizace povolené, vrátí tato funkce ukazatel na implementaci třídy Foundation `IDispatch` používané klienty, kteří komunikují prostřednictvím `IDispatch` rozhraní. Volání této funkce automaticky přidá odkaz na ukazatele, takže není nutné vytvářet volání [IUnknown::AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379).  
  
##  <a name="gettypeinfocount"></a>CCmdTarget::GetTypeInfoCount  
 Načte počet rozhraní typ informace, které poskytuje objekt.  
  
```  
virtual UINT GetTypeInfoCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet typ informace rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen v podstatě implementuje [IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12).  
  
 Odvozené třídy by měly přepsat tuto funkci k vrátí počet rozhraní informace typu poskytovaných (0 nebo 1). Pokud přepsána nejsou, **GetTypeInfoCount** vrátí hodnotu 0. Chcete-li přepsat, použijte [implement_oletypelib –](../../mfc/reference/type-library-access.md#implement_oletypelib) makro, která také implementuje `GetTypeLib` a `GetTypeLibCache`.  
  
##  <a name="gettypeinfoofguid"></a>CCmdTarget::GetTypeInfoOfGuid  
 Načte popis typu, který odpovídá zadaným identifikátorem GUID.  
  
```  
HRESULT GetTypeInfoOfGuid(
    LCID lcid,  
    const GUID& guid,  
    LPTYPEINFO* ppTypeInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `lcid`  
 Identifikátor národního prostředí ( `LCID`).  
  
 `guid`  
 [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931) popisu typu.  
  
 `ppTypeInfo`  
 Ukazatel na ukazatel `ITypeInfo` rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 HRESULT indikující úspěch nebo selhání volání. V případě úspěšného * `ppTypeInfo` odkazuje na typ informace rozhraní.  
  
##  <a name="gettypelib"></a>CCmdTarget::GetTypeLib  
 Získá ukazatel na knihovny typů.  
  
```  
virtual HRESULT GetTypeLib(
    LCID lcid,  
    LPTYPELIB* ppTypeLib);
```  
  
### <a name="parameters"></a>Parametry  
 `lcid`  
 Identifikátor národního prostředí ( `LCID`).  
  
 `ppTypeLib`  
 Ukazatel na ukazatel `ITypeLib` rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 HRESULT indikující úspěch nebo selhání volání. V případě úspěšného * `ppTypeLib` odkazuje na typ knihovny rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Odvozené třídy by měly přepsat tuto – členská funkce (Pokud přepsána nejsou, `GetTypeLib` vrátí TYPE_E_CANTLOADLIBRARY). Použití [implement_oletypelib –](../../mfc/reference/type-library-access.md#implement_oletypelib) makro, která také implementuje `GetTypeInfoCount` a `GetTypeLibCache`.  
  
##  <a name="gettypelibcache"></a>CCmdTarget::GetTypeLibCache  
 Získá typ mezipaměti knihovny.  
  
```  
virtual CTypeLibCache* GetTypeLibCache();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel **CTypeLibCache** objektu.  
  
### <a name="remarks"></a>Poznámky  
 Odvozené třídy by měly přepsat tuto – členská funkce (Pokud přepsána nejsou, **GetTypeLibCache** vrátí hodnotu NULL). Použití [implement_oletypelib –](../../mfc/reference/type-library-access.md#implement_oletypelib) makro, která také implementuje `GetTypeInfoCount` a `GetTypeLib`.  
  
##  <a name="isinvokeallowed"></a>CCmdTarget::IsInvokeAllowed  
 Tato funkce je volána implementací knihovny MFC z **volání metody IDispatch::Invoke** k určení, zda metoda daného automatizace (identifikovaný `dispid`) může být volána.  
  
```  
virtual BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="parameters"></a>Parametry  
 `dispid`  
 Odesílání ID.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda může být vyvolaná, jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `IsInvokeAllowed` vrátí hodnotu TRUE, **Invoke** pokračuje k volání metody; jinak `Invoke` se nezdaří, vrátí E_UNEXPECTED.  
  
 Odvozené třídy můžete přepsat této funkci vrátíte odpovídající hodnoty (Pokud přepsána nejsou, `IsInvokeAllowed` vrátí hodnotu TRUE). Viz zejména [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).  
  
##  <a name="isresultexpected"></a>CCmdTarget::IsResultExpected  
 Použití `IsResultExpected` zjistit, zda klient očekává návratovou hodnotu z její volání funkce automatizace.  
  
```  
BOOL IsResultExpected();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud automatizaci funkce by měla vrátit hodnotu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní OLE poskytuje informace o tom, jestli je klient pomocí nebo ignoruje výsledek volání funkce MFC a knihovny MFC pak používá tuto informaci k určení výsledek volání `IsResultExpected`. Pokud produkční návratovou hodnotu času - nebo prostředky, můžete zvýšit efektivitu voláním této funkce před computing návratovou hodnotu.  
  
 Tato funkce vrátí hodnotu 0, pouze jednou, abyste se při volání je z funkce automatizace, získat platný návratové hodnoty z jiných funkcí automatizace volal klienta.  
  
 `IsResultExpected`vrátí nenulovou hodnotu, pokud je volána, když se automatizaci volání funkce není v průběhu.  
  
##  <a name="oncmdmsg"></a>CCmdTarget::OnCmdMsg  
 Voláno rámcem ke směrování a odesílání příkazů zpráv a ke zpracování aktualizace objektů uživatelského rozhraní příkazu.  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Obsahuje ID příkazu.  
  
 `nCode`  
 Určuje kód příkaz oznámení. V tématu **poznámky** pro další informace o hodnotách pro `nCode`.  
  
 `pExtra`  
 Použít podle hodnoty `nCode`. V tématu **poznámky** Další informace o `pExtra`.  
  
 `pHandlerInfo`  
 Není-li **NULL**, `OnCmdMsg` vyplní **pTarget** a **pmf** členy `pHandlerInfo` struktura místo odeslání příkazu. Obvykle se tento parametr by měl být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se zpracovává zprávy; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Toto je hlavní implementace rutiny příkaz architektury framework.  
  
 V době běhu `OnCmdMsg` odešle zprávu příkaz, který má jiné objekty nebo zpracovává samotný příkaz voláním kořenová třída `CCmdTarget::OnCmdMsg`, což neodpovídá skutečné mapy zpráv vyhledávání. Úplný popis výchozí směrování příkazů, najdete v části [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
 Ve výjimečných případech můžete chtít funkci člen rozšíření rozhraní framework přepsat standardního směrování příkazů. Odkazovat na [Technická poznámka 21](../../mfc/tn021-command-and-message-routing.md) rozšířené informace o architektuře směrování příkazů.  
  
 Pokud přepíšete `OnCmdMsg`, je nutné zadat hodnotu vhodnou pro `nCode`, kód příkaz oznámení a `pExtra`, která závisí na hodnotu `nCode`. Následující tabulka uvádí jejich příslušné hodnoty:  
  
|`nCode`Hodnota|`pExtra`Hodnota|  
|-------------------|--------------------|  
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)*|  
|CN_EVENT|AFX_EVENT *|  
|CN_UPDATE_COMMAND_UI|CCmdUI *|  
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)*|  
|CN_OLE_UNREGISTER|NULL|  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]  
  
##  <a name="onfinalrelease"></a>CCmdTarget::OnFinalRelease  
 Voláno rámcem, až bude vydaná poslední OLE odkaz na nebo z objektu.  
  
```  
virtual void OnFinalRelease();
```  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkce zajistit zvláštní zpracování pro tuto situaci. Výchozí implementace odstraní objekt.  
  
##  <a name="restorewaitcursor"></a>CCmdTarget::RestoreWaitCursor  
 Volání této funkce obnovit příslušná kurzor přesýpacích hodin po změně kurzor systému (například po zprávou má otevřít a pak uzavřen při uprostřed časově náročná operace).  
  
```  
void RestoreWaitCursor();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC acdual –](../../visual-cpp-samples.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CCmdUI – třída](../../mfc/reference/ccmdui-class.md)   
 [CDocument – třída](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp – třída](../../mfc/reference/cwinapp-class.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CView – třída](../../mfc/reference/cview-class.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [COleDispatchDriver – třída](../../mfc/reference/coledispatchdriver-class.md)
