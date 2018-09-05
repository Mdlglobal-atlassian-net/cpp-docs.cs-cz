---
title: Colecontrolsite – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
dev_langs:
- C++
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c1d483f6ba532a6d8eeee1a8ec831cfd1d94b62
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766162"
---
# <a name="colecontrolsite-class"></a>Colecontrolsite – třída
Poskytuje podporu pro rozhraní vlastního ovládacího prvku na straně klienta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleControlSite : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleControlSite::COleControlSite](#colecontrolsite)|Vytvoří `COleControlSite` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Výchozí vlastnost hostovaného ovládacího prvku vazby ke zdroji dat.|  
|[COleControlSite::BindProperty](#bindproperty)|Ke zdroji dat vytvoří vazbu vlastnosti hostovaného ovládacího prvku.|  
|[COleControlSite::CreateControl](#createcontrol)|Vytvoří hostovaného ovládacího prvku ActiveX.|  
|[COleControlSite::DestroyControl](#destroycontrol)|Zničí hostovaného ovládacího prvku.|  
|[COleControlSite::DoVerb](#doverb)|Spouští konkrétní příkaz hostovaného ovládacího prvku.|  
|[COleControlSite::EnableDSC](#enabledsc)|Umožňuje data sourcing pro ovládací prvek webu.|  
|[COleControlSite::EnableWindow](#enablewindow)|Umožňuje řízení lokality.|  
|[COleControlSite::FreezeEvents](#freezeevents)|Určuje, pokud ovládací prvek webu přijímá události.|  
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Získá výchozí tlačítko kód pro hostované ovládací prvek.|  
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Načte identifikátor ovládacího prvku.|  
|[COleControlSite::GetEventIID](#geteventiid)|Načte ID událostí rozhraní pro hostovaného ovládacího prvku.|  
|[COleControlSite::GetExStyle](#getexstyle)|Načte rozšířené styly ovládacího prvku lokality.|  
|[COleControlSite::GetProperty](#getproperty)|Načte určitou vlastnost hostovaného ovládacího prvku.|  
|[COleControlSite::GetStyle](#getstyle)|Načte styly ovládacího prvku lokality.|  
|[COleControlSite::GetWindowText](#getwindowtext)|Načte text hostovaného ovládacího prvku.|  
|[COleControlSite::InvokeHelper](#invokehelper)|Volání konkrétní metody hostovaného ovládacího prvku.|  
|[COleControlSite::InvokeHelperV](#invokehelperv)|Volání konkrétní metody hostovaného ovládacího prvku se seznamem argumentů proměnných.|  
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Určuje, zda ovládací prvek výchozí tlačítko v okně.|  
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Kontroluje stav viditelnosti ovládacího prvku lokality.|  
|[COleControlSite::ModifyStyle](#modifystyle)|Změní aktuální rozšířené styly ovládacího prvku lokality.|  
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Změní aktuální styly ovládacího prvku lokality.|  
|[COleControlSite::MoveWindow](#movewindow)|Změní pozici ovládacího prvku lokality.|  
|[COleControlSite::QuickActivate](#quickactivate)|Rychlé aktivuje hostovaného ovládacího prvku.|  
|[COleControlSite::SafeSetProperty](#safesetproperty)|Nastaví vlastnosti nebo metody ovládacího prvku bez pravděpodobnost, že došlo k výjimce.|  
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Nastaví výchozí tlačítko v okně.|  
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Načte identifikátor ovládacího prvku.|  
|[COleControlSite::SetFocus](#setfocus)|Nastaví fokus na ovládací prvek webu.|  
|[COleControlSite::SetProperty](#setproperty)|Nastaví konkrétní vlastnost ovládacího prvku prostředí.|  
|[COleControlSite::SetPropertyV](#setpropertyv)|Nastaví konkrétní vlastnost ovládacího prvku prostředí se seznamem argumentů proměnných.|  
|[COleControlSite::SetWindowPos](#setwindowpos)|Nastaví pozici ovládacího prvku lokality.|  
|[COleControlSite::SetWindowText](#setwindowtext)|Nastaví text hostovaného ovládacího prvku.|  
|[COleControlSite::ShowWindow](#showwindow)|Zobrazí nebo skryje řízení lokality.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Načte informace klávesnice a klávesových zkratek pro hostované ovládací prvek.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Určuje, zda hostované ovládací prvek je ovládací prvek bez oken.|  
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Obsahuje informace o zpracování pro ovládací prvek klávesnice.|  
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Soubor cookie bodu připojení ovládacího prvku.|  
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Různé stavy hostovaného ovládacího prvku.|  
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink` Souboru cookie ovládacího prvku.|  
|[COleControlSite::m_dwStyle](#m_dwstyle)|Styly hostovaného ovládacího prvku.|  
|[COleControlSite::m_hWnd](#m_hwnd)|Obslužná rutina ovládacího prvku lokality.|  
|[COleControlSite::m_iidEvents](#m_iidevents)|ID události rozhraní pro hostované ovládací prvek.|  
|[COleControlSite::m_nID](#m_nid)|ID hostovaného ovládacího prvku.|  
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Ukazatel `IOleInPlaceActiveObject` objekt hostovaného ovládacího prvku.|  
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Kontejner hostovaného ovládacího prvku.|  
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Ukazatel `IOleInPlaceObject` objekt hostovaného ovládacího prvku.|  
|[COleControlSite::m_pObject](#m_pobject)|Ukazatel `IOleObjectInterface` rozhraní ovládacího prvku.|  
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Ukazatel `IOleInPlaceObjectWindowless` rozhraní ovládacího prvku.|  
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Ukazatel na objekt okna pro ovládací prvek prostředí.|  
|[COleControlSite::m_rect](#m_rect)|Rozměry ovládacího prvku lokality.|  
  
## <a name="remarks"></a>Poznámky  
 Tato podpora je hlavním prostředkem, podle kterého vloženému ovládacímu prvku ActiveX získává informace o umístění a rozsah jeho web pro zobrazení, jeho monikeru, jeho uživatelské rozhraní, jeho vlastnosti prostředí a dalších prostředků poskytované svého kontejneru. `COleControlSite` plně implementuje [IOleControlSite](/windows/desktop/api/ocidl/nn-ocidl-iolecontrolsite), [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleClientSite](/windows/desktop/api/oleidl/nn-oleidl-ioleclientsite), [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink), `IBoundObjectSite`, `INotifyDBEvents`, [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) rozhraní. Kromě toho je implementováno rozhraní IDispatch (poskytují podporu pro vlastnosti prostředí a jímky událostí).  
  
 Chcete-li vytvořit pomocí webu ovládacího prvku ActiveX `COleControlSite`, odvoďte třídu z `COleControlSite`. Ve vaší `CWnd`-přepsat v odvozené třídě kontejneru (například vašem dialogovém okně) `CWnd::CreateControlSite` funkce.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxocc.h  
  
##  <a name="binddefaultproperty"></a>  COleControlSite::BindDefaultProperty  
 Základní ukazatel, který je definován zdroj dat, uživatelské jméno, heslo a SQL vlastnosti ovládacího prvku zdroje dat vytvoří vazbu volání objektů výchozí jednoduchý vázané vlastnosti, jako je označené v knihovně typů.  
  
```  
virtual void BindDefaultProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    LPCTSTR szFieldName,  
    CWnd* pDSCWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Určuje ovládací prvek vázaný na data, která má být svázána s ovládacím prvkem zdroj dat DISPID vlastnost.  
  
 *vtProp*  
 Určuje typ vlastnosti, která má být vázaný – například VT_BSTR, VT_VARIANT a tak dále.  
  
 *szFieldName*  
 Určuje název sloupce v kurzoru poskytuje ovládací prvek zdroje dat, ke kterému bude vázán vlastnost.  
  
 *pDSCWnd*  
 Ukazatel `CWnd`-objektu, který je hostitelem ovládací prvek zdroje dat, ke kterému bude vázán vlastnost.  
  
### <a name="remarks"></a>Poznámky  
 `CWnd` Objekt, na kterém voláním této funkce musí být ovládací prvek vázaný na data.  
  
##  <a name="bindproperty"></a>  COleControlSite::BindProperty  
 Základní ukazatel, který je definován zdroj dat, uživatelské jméno, heslo a SQL vlastnosti ovládacího prvku zdroje dat vytvoří vazbu volání objektů jednoduché vázané vlastnosti, jako označené v knihovně typů.  
  
```  
virtual void BindProperty(
    DISPID dwDispId,  
    CWnd* pWndDSC);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispId*  
 Určuje ovládací prvek vázaný na data, která má být svázána s ovládacím prvkem zdroj dat DISPID vlastnost.  
  
 *pWndDSC*  
 Ukazatel `CWnd`-objektu, který je hostitelem ovládací prvek zdroje dat, ke kterému bude vázán vlastnost.  
  
### <a name="remarks"></a>Poznámky  
 `CWnd` Objekt, na kterém voláním této funkce musí být ovládací prvek vázaný na data.  
  
##  <a name="colecontrolsite"></a>  COleControlSite::COleControlSite  
 Sestaví nový `COleControlSite` objektu.  
  
```  
explicit COleControlSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parametry  
 *pCtrlCont*  
 Ukazatel na kontejneru ovládacího prvku (který představuje okno, který je hostitelem AtiveX ovládacího prvku).  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána [COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) funkce. Další informace o přizpůsobení vytváření kontejnerů najdete v tématu [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).  
  
##  <a name="createcontrol"></a>  COleControlSite::CreateControl  
 Vytvoří ovládací prvek ActiveX, hostované `COleControlSite` objektu.  
  
```  
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    UINT nID,  
    CFile* pPersist = NULL,  
    BOOL bStorage = FALSE,  
    BSTR bstrLicKey = NULL);

 
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const POINT* ppt,  
    const SIZE* psize,  
    UINT nID,  
    CFile* pPersist = NULL,  
    BOOL bStorage = FALSE,  
    BSTR bstrLicKey = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndCtrl*  
 Ukazatel na objekt window představující ovládací prvek.  
  
 *identifikátor CLSID*  
 Třída jedinečné ID ovládacího prvku.  
  
 *lpszWindowName*  
 Ukazatel na text, který se zobrazí v ovládacím prvku. Nastaví hodnotu vlastnosti winodw titulek a Text (pokud existuje).  
  
 *dwStyle*  
 Styly Windows. Dostupné styly jsou uvedeny v části **poznámky** oddílu.  
  
 *Rect*  
 Určuje velikost a umístění ovládacího prvku. Může se jednat buď `CRect` objektu nebo `RECT` struktury.  
  
 *nID*  
 Určuje ID ovládacího prvku podřízené okno.  
  
 *pPersist*  
 Ukazatel `CFile` obsahující trvalý stav ovládacího prvku. Výchozí hodnota je NULL označující, že ovládací prvek se inicializuje bez obnovení stavu z jakékoli trvalého úložiště. Pokud není NULL, mělo by být ukazatel `CFile`-odvozenému objektu, který obsahuje ovládací prvek trvalá data ve formě datového proudu nebo úložiště. Tato data by byla uložena do předchozí aktivace klienta. `CFile` Může obsahovat další data, ale musí být ukazatel jeho čtení a zápis nastavení do prvního bajtu trvalá data v okamžiku volání `CreateControl`.  
  
 *bStorage*  
 Určuje, zda data v *pPersist* by měl být interpretován jako `IStorage` nebo `IStream` data. Pokud data v *pPersist* je úložiště, *bStorage* by měla být nastavena na možnost PRAVDA. Pokud data v *pPersist* je datový proud, *bStorage* by měl mít hodnotu FALSE. Výchozí hodnota je FALSE.  
  
 *bstrLicKey*  
 Volitelné licenční klíče data. Tato data je potřeba jenom pro vytváření ovládacích prvků, které vyžadují za běhu licenční klíč. Pokud ovládací prvek podporuje licencování, je nutné zadat licenční klíč pro vytvoření ovládacího prvku na úspěšné. Výchozí hodnota je NULL.  
  
 *ppt*  
 Ukazatel `POINT` strukturu, která obsahuje levého horního rohu ovládacího prvku. Velikost ovládacího prvku, je určen hodnotou *psize*. *Ppt* a *psize* hodnoty jsou volitelné metodu pro určení velikosti a umístění zpracovatelského ovládacího prvku.  
  
 *psize*  
 Ukazatel `SIZE` strukturu, která obsahuje velikost ovládacího prvku. Levém horním rohu je určen hodnotou *ppt*. *Ppt* a *psize* hodnoty jsou volitelné metodu pro určení velikosti a umístění zpracovatelského ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pouze podmnožinu Windows *dwStyle* nepodporuje příznaky `CreateControl`:  
  
- WS_VISIBLE vytvoří okno, které je zpočátku viditelné. Povinné, pokud chcete, aby ovládací prvek viditelný okamžitě, stejně jako běžná okna.  
  
- WS_DISABLED vytvoří okno, které je zpočátku zakázáno. Zakázané okno nepřijímá vstup od uživatele. Můžete nastavit, pokud ovládací prvek má vlastnost Enabled.  
  
- WS_BORDER vytvoří okno s dynamické čáry ohraničení. Můžete nastavit, pokud ovládací prvek má vlastnosti BorderStyle.  
  
- WS_GROUP Určuje první prvek skupiny ovládacích prvků. Uživatel může změnit fokus klávesnice z jednoho ovládacího prvku ve skupině na další pomocí šipkových kláves. Všechny ovládací prvky definované ve stylu WS_GROUP po prvním ovládacím prvku, patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP končí skupině a začíná další skupinu.  
  
- WS_TABSTOP určuje ovládací prvek, který může získat fokus klávesnice, když uživatel stiskne klávesu TAB. Na další ovládací prvek stylu WS_TABSTOP stisknutím klávesy TAB změní fokus klávesnice.  
  
 Druhé přetížení použijte k vytvoření výchozí velikosti ovládacích prvků.  
  
##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl  
 Odstraní `COleControlSite` objektu.  
  
```  
virtual BOOL DestroyControl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná, jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Po dokončení objektu je uvolněna z paměti a všechny ukazatele na objekt už nejsou platné.  
  
##  <a name="doverb"></a>  COleControlSite::DoVerb  
 Provede zadanou operaci.  
  
```  
virtual HRESULT DoVerb(
    LONG nVerb,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nVerb*  
 Určuje příkaz pro spuštění. Může obsahovat jednu z následujících akcí:  
  
|Hodnota|Význam|Symbol|  
|-----------|-------------|------------|  
|0|primární požadavek|OLEIVERB_PRIMARY|  
|-1|Sekundární příkaz|(Žádné)|  
|1|Zobrazí objekt pro úpravy.|OLEIVERB_SHOW|  
|-2|Upraví položka v samostatném okně.|OLEIVERB_OPEN|  
|-3|Skryje objektu.|OLEIVERB_HIDE|  
|-4|Aktivuje ovládací prvek na místě.|OLEIVERB_UIACTIVATE|  
|-5|Aktivuje ovládací prvek na místě a bez další prvky uživatelského rozhraní.|OLEIVERB_INPLACEACTIVATE|  
|-7|Zobrazení vlastností ovládacího prvku.|OLEIVERB_PROPERTIES|  
  
 *lpMsg*  
 Ukazatel na zprávu, která způsobila položka, která má být aktivován.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá přímo prostřednictvím ovládacího prvku `IOleObject` rozhraní provedla Zadaná operace. Pokud je vyvolána výjimka v důsledku volání funkce, vrátí se kód chyby HRESULT.  
  
 Další informace najdete v tématu [Funkce IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) v sadě Windows SDK.  
  
##  <a name="enabledsc"></a>  COleControlSite::EnableDSC  
 Umožňuje data sourcing pro ovládací prvek webu.  
  
```  
virtual void EnableDSC();
```  
  
### <a name="remarks"></a>Poznámky  
 Volá se rozhraním, které chcete povolit a inicializovat data sourcing pro ovládací prvek webu. Přepsání této funkce můžete poskytovat vlastní chování.  
  
##  <a name="enablewindow"></a>  COleControlSite::EnableWindow  
 Povolí nebo zakáže myši a klávesnice pro ovládací prvek webu.  
  
```  
virtual BOOL EnableWindow(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 *bEnable*  
 Určuje, jestli se má povolit nebo zakázat v okně: TRUE, pokud vstup okno má být povoleno, jinak hodnota FALSE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud byla zakázaná v okně, jinak 0.  
  
##  <a name="freezeevents"></a>  COleControlSite::FreezeEvents  
 Určuje, zda bude ovládací prvek webu zpracování nebo ignorovat události odesílané z ovládacího prvku.  
  
```  
void FreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parametry  
 *bFreeze*  
 Určuje, zda ovládací prvek webu chce přestane přijímat události. Nenulové, pokud ovládací prvek nepřijímá události. jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bFreeze* má hodnotu TRUE, web ovládací prvek požaduje zastavení fring událostí ovládacího prvku. Pokud *bFreeze* má hodnotu FALSE, web ovládací prvek požaduje ovládacího prvku abyste mohli pokračovat, vyvolává události.  
  
> [!NOTE]
>  Ovládací prvek není potřeba zastavit, pokud to vyžaduje ovládací prvek webu vyvolává události. Může pokračovat v jeho spuštění, ale pomocí ovládacího prvku lokality budou ignorovány všechny další události.  
  
##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo  
 Načte informace o klávesových zkratek klávesnice a chování klávesnice ovládacího prvku.  
  
```  
void GetControlInfo();
```  
  
### <a name="remarks"></a>Poznámky  
 Informace jsou uloženy v [COleControlSite::m_ctlInfo](#m_ctlinfo).  
  
##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode  
 Určuje, zda ovládací prvek výchozí příkazové tlačítko.  
  
```  
DWORD GetDefBtnCode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Může být jedna z následujících hodnot:  
  
- Ovládací prvek DLGC_DEFPUSHBUTTON je výchozí tlačítko v dialogovém okně.  
  
- Ovládací prvek DLGC_UNDEFPUSHBUTTON není výchozí tlačítko v dialogovém okně.  
  
- **0** ovládací prvek není tlačítko.  
  
##  <a name="getdlgctrlid"></a>  COleControlSite::GetDlgCtrlID  
 Načte identifikátor ovládacího prvku.  
  
```  
virtual int GetDlgCtrlID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor položky dialogového okna ovládacího prvku.  
  
##  <a name="geteventiid"></a>  COleControlSite::GetEventIID  
 Načte ukazatel na rozhraní výchozí událost ovládacího prvku.  
  
```  
BOOL GetEventIID(IID* piid);
```  
  
### <a name="parameters"></a>Parametry  
 *piid*  
 Ukazatel na identifikátor rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná, jinak 0. V případě úspěšného ověření *piid* obsahuje ID rozhraní pro rozhraní události výchozí ovládacího prvku.  
  
##  <a name="getexstyle"></a>  COleControlSite::GetExStyle  
 Rozšířené styly oken na načte.  
  
```  
virtual DWORD GetExStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V okně Ovládací prvek v rozšířené styly.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li načíst regulárních styly, zavolejte [COleControlSite::GetStyle](#getstyle).  
  
##  <a name="getproperty"></a>  COleControlSite::GetProperty  
 Získá vlastnosti ovládacího prvku určené *dwDispID*.  
  
```  
virtual void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Určuje ID odeslání výchozí ovládacího prvku nalezena vlastnost `IDispatch` rozhraní, který se má načíst.  
  
 *vtProp*  
 Určuje typ vlastnosti, který se má načíst. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *pvProp*  
 Adresa proměnné, která se zobrazí hodnotu vlastnosti. Musí odpovídat typu určeného *vtProp*.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota, je vrácena prostřednictvím *pvProp*.  
  
##  <a name="getstyle"></a>  COleControlSite::GetStyle  
 Načte styly ovládacího prvku lokality.  
  
```  
virtual DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V okně Styly.  
  
### <a name="remarks"></a>Poznámky  
 Seznam možných hodnot najdete v tématu [styly Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles). Chcete-li získat rozšířené styly ovládacího prvku serveru, zavolejte [COleControlSite::GetExStyle](#getexstyle).  
  
##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText  
 Načte aktuální text ovládacího prvku.  
  
```  
virtual void GetWindowText(CString& str) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *str*  
 Odkaz na `CString` objekt, který obsahuje aktuální text ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Pokud ovládací prvek podporuje uložených vlastností titulek, vrátí se tato hodnota. Pokud popisek uložených vlastností se nepodporuje, je vrácena hodnota pro vlastnost Text.  
  
##  <a name="invokehelper"></a>  COleControlSite::InvokeHelper  
 Vyvolá metodu nebo vlastnost určenou *dwDispID*, v rámci určeného *wFlags*.  
  
```  
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Určuje hodnotu dispatch ID vlastnosti nebo metody v ovládacího prvku `IDispatch` rozhraní má být volána.  
  
 *wFlags*  
 Příznaky popisující kontext volání IDispatch::Invoke. K případnému *wFlags* hodnoty, najdete v článku `IDispatch::Invoke` v sadě Windows SDK.  
  
 *vtRet*  
 Určuje typ vrácené hodnoty. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *pvRet*  
 Adresa proměnné, která bude přijímat hodnoty vlastnosti nebo návratovou hodnotu. Musí odpovídat typu určeného *vtRet*.  
  
 *pbParamInfo*  
 Ukazatel na řetězec zakončený hodnotou null bajtů určující typy parametrů za *pbParamInfo*. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Proměnné seznam parametrů typů uvedených v *pbParamInfo*.  
  
### <a name="remarks"></a>Poznámky  
 *PbParamInfo* parametr určuje typy parametry předané do metody nebo vlastnosti. Proměnné seznam argumentů, které je reprezentován... v syntaxi deklarace.  
  
 Tato funkce převede parametry VARIANTARG hodnoty a potom vyvolá `IDispatch::Invoke` metoda na ovládacím prvku. Pokud volání `IDispatch::Invoke` selže, tato funkce vyvolá výjimku. Pokud stavový kód vrácený `IDispatch::Invoke` je `DISP_E_EXCEPTION`, tato funkce vyvolá `COleDispatchException` objektu, jinak se vyvolá `COleException`.  
  
##  <a name="invokehelperv"></a>  COleControlSite::InvokeHelperV  
 Vyvolá metodu nebo vlastnost určenou *dwDispID*, v rámci určeného *wFlags*.  
  
```  
virtual void InvokeHelperV(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo,  
    va_list argList);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Určuje hodnotu dispatch ID vlastnosti nebo metody v ovládacího prvku `IDispatch` rozhraní má být volána.  
  
 *wFlags*  
 Příznaky popisující kontext volání IDispatch::Invoke.  
  
 *vtRet*  
 Určuje typ vrácené hodnoty. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *pvRet*  
 Adresa proměnné, která bude přijímat hodnoty vlastnosti nebo návratovou hodnotu. Musí odpovídat typu určeného *vtRet*.  
  
 *pbParamInfo*  
 Ukazatel na řetězec zakončený hodnotou null bajtů určující typy parametrů za *pbParamInfo*. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *Seznam_argumentů*  
 Ukazatel na seznam argumentů s proměnnou délkou.  
  
### <a name="remarks"></a>Poznámky  
 *PbParamInfo* parametr určuje typy parametry předané do metody nebo vlastnosti. Je možné předat další parametry pro metody nebo vlastnosti vyvolání pomocí *va_list* parametru.  
  
 Obvykle se tato funkce je volána `COleControlSite::InvokeHelper`.  
  
##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton  
 Určuje, zda ovládací prvek výchozí tlačítko.  
  
```  
BOOL IsDefaultButton();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je ovládací prvek výchozí tlačítko v okně, jinak hodnota nula.  
  
##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled  
 Určuje, zda je povoleno řízení lokality.  
  
```  
virtual BOOL IsWindowEnabled() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud ovládací prvek je povoleno, jinak hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota je načten z uložené vlastnosti Enabled ovládacího prvku.  
  
##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless  
 Určuje, zda je objekt ovládací prvek bez oken.  
  
```  
BOOL m_bIsWindowless;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nenulové, pokud ovládací prvek nemá žádný časový interval, v opačném případě hodnotu.  
  
##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo  
 Informace o zpracování vstupu klávesnice ovládacím prvkem.  
  
```  
CONTROLINFO m_ctlInfo;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tyto informace jsou uloženy v [CONTROLINFO](/windows/desktop/api/ocidl/ns-ocidl-tagcontrolinfo) struktury.  
  
##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink  
 Obsahuje soubor cookie je spojovací bod z jímky událostí ovládacího prvku.  
  
```  
DWORD m_dwEventSink;  
```  
  
##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus  
 Obsahuje různé informace o ovládacím prvku.  
  
```  
DWORD m_dwMiscStatus;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc)v sadě Windows SDK.  
  
##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink  
 Obsahuje [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) souboru cookie.  
  
```  
DWORD m_dwPropNotifySink;  
```  
  
##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle  
 Obsahuje styly oken ovládacího prvku.  
  
```  
DWORD m_dwStyle;  
```  
  
##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd  
 Obsahuje HWND ovládacího prvku, nebo hodnota NULL, pokud je ovládací prvek bez oken.  
  
```  
HWND m_hWnd;  
```  
  
##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents  
 Obsahuje ID rozhraní rozhraní stoku událostí výchozí ovládacího prvku.  
  
```  
IID m_iidEvents;  
```  
  
##  <a name="m_nid"></a>  COleControlSite::m_nID  
 Obsahuje ID položky dialogového okna ovládacího prvku  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject  
 Obsahuje [IOleInPlaceActiveObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceactiveobject) rozhraní ovládacího prvku.  
  
```  
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;  
```  
  
##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont  
 Obsahuje (představující formuláře) kontejneru ovládacího prvku.  
  
```  
COleControlContainer* m_pCtrlCont;  
```  
  
##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject  
 Obsahuje `IOleInPlaceObject` [IOleInPlaceObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceobject) rozhraní ovládacího prvku.  
  
```  
LPOLEINPLACEOBJECT m_pInPlaceObject;  
```  
  
##  <a name="m_pobject"></a>  COleControlSite::m_pObject  
 Obsahuje `IOleObjectInterface` rozhraní ovládacího prvku.  
  
```  
LPOLEOBJECT m_pObject;  
```  
  
##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject  
 Obsahuje `IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) rozhraní ovládacího prvku.  
  
```  
IOleInPlaceObjectWindowless* m_pWindowlessObject;  
```  
  
##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl  
 Obsahuje ukazatel `CWnd` objekt, který představuje samotný ovládací prvek.  
  
```  
CWnd* m_pWndCtrl;  
```  
  
##  <a name="m_rect"></a>  COleControlSite::m_rect  
 Obsahuje hranice ovládacího prvku vzhledem k oknu kontejneru.  
  
```  
CRect m_rect;  
```  
  
##  <a name="modifystyle"></a>  COleControlSite::ModifyStyle  
 Upravit styly ovládacího prvku.  
  
```  
virtual BOOL ModifyStyle(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *dwRemove*  
 Styly odeberou z aktuální styly oken.  
  
 *dwAdd*  
 Styly přidávané z aktuální styly oken.  
  
 *nFlags*  
 Okno umístění příznaky. Seznam možných hodnot, najdete v článku [SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) funkce v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud se změní styly, jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 Stock vlastnosti Enabled ovládacího prvku budou upraveny tak, aby odpovídaly nastavení WS_DISABLED. Uložených vlastností styl ohraničení ovládacího prvku budou upraveny tak, aby odpovídaly nastavení požadovaná pro WS_BORDER. Další styly použijí přímo na popisovač okna ovládacího prvku, pokud je k dispozici.  
  
 Upraví okno Styly ovládacího prvku. Styly, které chcete přidat nebo odebrat je možné kombinovat s použitím bitový operátor OR ( &#124; ) – operátor. Zobrazit [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) funkce v sadě Windows SDK pro informace o stylech dostupném časovém intervalu.  
  
 Pokud *nFlags* nenulové, `ModifyStyle` volá funkci Win32 `SetWindowPos`, nebo ho překreslí okna tím, že zkombinujete *nFlags* následující čtyři Flags:  
  
- SWP_NOSIZE zachová aktuální velikost.  
  
- SWP_NOMOVE zachová aktuální pozici.  
  
- SWP_NOZORDER zachová aktuální pořadí.  
  
- SWP_NOACTIVATE neaktivuje okna.  
  
 Okno Změnit na rozšířené styly, zavolejte [ModifyStyleEx](#modifystyleex).  
  
##  <a name="modifystyleex"></a>  COleControlSite::ModifyStyleEx  
 Změní rozšířené styly ovládacího prvku.  
  
```  
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *dwRemove*  
 Rozšířené styly odeberou z aktuální styly oken.  
  
 *dwAdd*  
 Rozšířené styly přidávané z aktuální styly oken.  
  
 *nFlags*  
 Okno umístění příznaky. Seznam možných hodnot, najdete v článku [SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) funkce v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud se změní styly, jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 Stock vlastnosti Appearance ovládacího prvku budou upraveny tak, aby odpovídaly nastavení WS_EX_CLIENTEDGE. Všechny ostatní rozšířené styly oken se použijí přímo na popisovač okna ovládacího prvku, pokud je k dispozici.  
  
 Upraví okno Rozšířené styly ovládacího prvku objektu lokality. Styly, které chcete přidat nebo odebrat je možné kombinovat s použitím bitový operátor OR ( &#124; ) – operátor. Zobrazit [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) funkce v sadě Windows SDK pro informace o stylech dostupném časovém intervalu.  
  
 Pokud *nFlags* nenulové, `ModifyStyleEx` volá funkci Win32 `SetWindowPos`, nebo ho překreslí okna tím, že zkombinujete *nFlags* následující čtyři Flags:  
  
- SWP_NOSIZE zachová aktuální velikost.  
  
- SWP_NOMOVE zachová aktuální pozici.  
  
- SWP_NOZORDER zachová aktuální pořadí.  
  
- SWP_NOACTIVATE neaktivuje okna.  
  
 Okno Změnit na rozšířené styly, zavolejte [ModifyStyle](#modifystyle).  
  
##  <a name="movewindow"></a>  COleControlSite::MoveWindow  
 Změní pozice ovládacího prvku.  
  
```  
virtual void MoveWindow(
    int x,  
    int y,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Nové umístění levé části okna.  
  
 *y*  
 Novou pozici horní části okna.  
  
 *nWidth*  
 Nové šířku okna  
  
 *nHeight*  
 Nové výšku okna.  
  
##  <a name="quickactivate"></a>  COleControlSite::QuickActivate  
 Rychlé aktivuje obsažený ovládací prvek.  
  
```  
virtual BOOL QuickActivate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud byl aktivován ovládací prvek webu, v opačném případě hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci lze volat pouze v případě, že uživatel je přepsání v procesu vytváření ovládacího prvku.  
  
 `IPersist*::Load` a `IPersist*::InitNew` metody by měla být volána, když dojde k rychlé aktivace. Ovládací prvek by měl vytvořit její připojení ke kontejneru jímky během rychlé aktivace. Ale tato připojení nejsou za provozu do `IPersist*::Load` nebo `IPersist*::InitNew` byla volána.  
  
##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty  
 Nastaví vlastnosti ovládacího prvku určené *dwDispID*.  
  
```  
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Určuje hodnotu dispatch ID vlastnosti nebo metody v ovládacího prvku `IDispatch` rozhraní, která se má nastavit.  
  
 *vtProp*  
 Určuje typ vlastnosti. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Jeden parametr typu určeného *vtProp*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak nula.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Na rozdíl od `SetProperty` a `SetPropertyV`, pokud dojde k chybě (například při pokusu o nastavení vlastnosti neexistující), není vyvolána žádná výjimka.  
  
##  <a name="setdefaultbutton"></a>  COleControlSite::SetDefaultButton  
 Nastaví ovládací prvek jako výchozího tlačítka.  
  
```  
void SetDefaultButton(BOOL bDefault);
```  
  
### <a name="parameters"></a>Parametry  
 *bDefault*  
 Nenulové, pokud ovládací prvek by měl být výchozí tlačítko; jinak nula.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Ovládací prvek musí mít OLEMISC_ACTSLIKEBUTTON stav bit sady.  
  
##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID  
 Změní hodnotu identifikátor položky ovládacího prvku dialogu.  
  
```  
virtual int SetDlgCtrlID(int nID);
```  
  
### <a name="parameters"></a>Parametry  
 *nID*  
 Nová hodnota identifikátoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného ověření předchozím dialogovém okně Položka identifikátor okna. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setfocus"></a>  COleControlSite::SetFocus  
 Nastaví zaměření na ovládací prvek.  
  
```  
virtual CWnd* SetFocus();  
virtual CWnd* SetFocus(LPMSG lpmsg);
```  
  
### <a name="parameters"></a>Parametry  
 *lpmsg*  
 Ukazatel [msg – struktura](../../mfc/reference/msg-structure1.md). Tato struktura obsahuje aktivace Windows zprávy `SetFocus` požadavek pro ovládací prvek obsažený v aktuální lokalitě ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na okno, které dříve měly fokus.  
  
##  <a name="setproperty"></a>  COleControlSite::SetProperty  
 Nastaví vlastnosti ovládacího prvku určené *dwDispID*.  
  
```  
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Určuje hodnotu dispatch ID vlastnosti nebo metody v ovládacího prvku `IDispatch` rozhraní, která se má nastavit.  
  
 *vtProp*  
 Určuje typ vlastnosti. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Jeden parametr typu určeného *vtProp*.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `SetProperty` zjistí chybu, je vyvolána výjimka.  
  
 Typ výjimky je určen návratovou hodnotou pokus o nastavení vlastnosti nebo metody. Pokud je návratová hodnota `DISP_E_EXCEPTION`, `COleDispatchExcpetion` jinak k této výjimce dojde `COleException`.  
  
##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV  
 Nastaví vlastnosti ovládacího prvku určené *dwDispID*.  
  
```  
virtual void SetPropertyV(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    va_list argList);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Určuje hodnotu dispatch ID vlastnosti nebo metody v ovládacího prvku `IDispatch` rozhraní, která se má nastavit.  
  
 *vtProp*  
 Určuje typ vlastnosti. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *Seznam_argumentů*  
 Ukazatel na seznam argumentů.  
  
### <a name="remarks"></a>Poznámky  
 Další parametry pro metody nebo vlastnosti vyvolání může být passeed pomocí *arg_list* parametru. Pokud `SetProperty` zjistí chybu, je vyvolána výjimka.  
  
 Typ výjimky je určen návratovou hodnotou pokus o nastavení vlastnosti nebo metody. Pokud je návratová hodnota `DISP_E_EXCEPTION`, `COleDispatchExcpetion` jinak k této výjimce dojde `COleException`.  
  
##  <a name="setwindowpos"></a>  COleControlSite::SetWindowPos  
 Nastaví velikost, umístění a pořadí z ovládacího prvku lokality.  
  
```  
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,  
    int x,  
    int y,  
    int cx,  
    int cy,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndInsertAfter*  
 Ukazatel na okno.  
  
 *x*  
 Nové umístění levé části okna.  
  
 *y*  
 Novou pozici horní části okna.  
  
 *CX*  
 Nové šířku okna  
  
 *CY*  
 Nové výšku okna.  
  
 *nFlags*  
 Určuje okno pro změnu velikosti a polohování příznaky. Možné hodnoty najdete v části poznámky [SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulovou hodnotu v případě úspěchu, jinak hodnotu nula.  
  
##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText  
 Nastaví text pro ovládací prvek webu.  
  
```  
virtual void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszString*  
 Ukazatel na řetězec zakončený hodnotou null se použije jako nový název nebo ovládací prvek text.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se nejprve pokusí nastavit uložených vlastností titulek. Pokud popisek uložených vlastností není podporovaná, je místo toho nastavte vlastnost Text.  
  
##  <a name="showwindow"></a>  COleControlSite::ShowWindow  
 Nastaví v okně zobrazení stavu.  
  
```  
virtual BOOL ShowWindow(int nCmdShow);
```  
  
### <a name="parameters"></a>Parametry  
 *nCmdShow*  
 Určuje, jak má být zobrazen ovládací prvek webu. Musí být jeden z následujících hodnot:  
  
- SW_HIDE skrývá toto okno a předá do další okno aktivace.  
  
- SW_MINIMIZE minimalizuje okno a aktivuje okno nejvyšší úrovně v seznamu v systému.  
  
- Aktivuje SW_RESTORE a zobrazí v okně. Pokud v okně je minimalizovaná nebo maximalizované, Windows jej obnoví na jeho původní velikost a umístění.  
  
- SW_SHOW aktivuje v okně a zobrazí jej v jeho aktuální velikost a umístění.  
  
- SW_SHOWMAXIMIZED aktivuje v okně a zobrazí ho jako maximalizovaném okně.  
  
- SW_SHOWMINIMIZED aktivuje v okně a zobrazí ho jako ikona.  
  
- SW_SHOWMINNOACTIVE zobrazí okno jako ikona. V okně, která je aktuálně aktivní zůstává aktivní.  
  
- SW_SHOWNA zobrazí okno v jejím aktuálním stavu. V okně, která je aktuálně aktivní zůstává aktivní.  
  
- SW_SHOWNOACTIVATE zobrazí okno v jeho aktuální velikost a umístění. V okně, která je aktuálně aktivní zůstává aktivní.  
  
- Aktivuje SW_SHOWNORMAL a zobrazí v okně. Pokud v okně je minimalizovaná nebo maximalizované, Windows jej obnoví na jeho původní velikost a umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo dříve vidět; okna 0, pokud byla dříve skrytá okna.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleControlContainer – třída](../../mfc/reference/colecontrolcontainer-class.md)
