---
title: "Třída COleControlSite | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80541bc777d2c77209812cbee621045b7d6c6507
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="colecontrolsite-class"></a>COleControlSite – třída
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
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Zdroj dat vytvoří vazbu výchozí vlastnost hostované ovládacího prvku.|  
|[COleControlSite::BindProperty](#bindproperty)|Zdroj dat vytvoří vazbu vlastnost hostované ovládacího prvku.|  
|[COleControlSite::CreateControl](#createcontrol)|Vytvoří hostované ovládací prvek ActiveX.|  
|[COleControlSite::DestroyControl](#destroycontrol)|Zničí hostovaného ovládacího prvku.|  
|[COleControlSite::DoVerb](#doverb)|Provede konkrétní operaci hostované ovládacího prvku.|  
|[COleControlSite::EnableDSC](#enabledsc)|Umožňuje data sourcing ovládacího prvku lokality.|  
|[COleControlSite::EnableWindow](#enablewindow)|Umožňuje řízení lokality.|  
|[COleControlSite::FreezeEvents](#freezeevents)|Určuje, pokud řízení lokality přijímá události.|  
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Získá výchozí tlačítko kód pro hostované ovládací prvek.|  
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Načte identifikátor ovládacího prvku.|  
|[COleControlSite::GetEventIID](#geteventiid)|Načte ID událostí rozhraní pro hostované ovládacího prvku.|  
|[COleControlSite::GetExStyle](#getexstyle)|Načte rozšířené styly ovládacího prvku lokality.|  
|[COleControlSite::GetProperty](#getproperty)|Načte určité vlastnosti hostované ovládacího prvku.|  
|[COleControlSite::GetStyle](#getstyle)|Načte styly ovládacího prvku lokality.|  
|[COleControlSite::GetWindowText](#getwindowtext)|Načte text hostované ovládacího prvku.|  
|[COleControlSite::InvokeHelper](#invokehelper)|Vyvolejte zvláštní metodu hostované ovládacího prvku.|  
|[COleControlSite::InvokeHelperV](#invokehelperv)|Vyvolání konkrétní metody hostovaného ovládacího prvku s seznam argumentů proměnných.|  
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Určuje, zda je ovládací prvek výchozího tlačítka v okně.|  
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Kontroluje stav viditelnosti ovládacího prvku lokality.|  
|[COleControlSite::ModifyStyle](#modifystyle)|Upravuje aktuální rozšířené styly ovládacího prvku lokality.|  
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Upravuje aktuální styly ovládacího prvku lokality.|  
|[COleControlSite::MoveWindow](#movewindow)|Změní umístění ovládacího prvku lokality.|  
|[COleControlSite::QuickActivate](#quickactivate)|Rychlé aktivuje hostovaného ovládacího prvku.|  
|[COleControlSite::SafeSetProperty](#safesetproperty)|Nastaví vlastnosti nebo metody ovládacího prvku bez pravděpodobnost, že došlo k výjimce.|  
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Nastaví výchozího tlačítka v okně.|  
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Načte identifikátor ovládacího prvku.|  
|[COleControlSite::SetFocus](#setfocus)|Nastaví fokus na ovládací prvek webu.|  
|[COleControlSite::SetProperty](#setproperty)|Nastaví konkrétní vlastnost hostované ovládacího prvku.|  
|[COleControlSite::SetPropertyV](#setpropertyv)|Nastaví konkrétní vlastnost hostované ovládacího prvku s seznam argumentů proměnných.|  
|[COleControlSite::SetWindowPos](#setwindowpos)|Nastavuje pozici ovládacího prvku lokality.|  
|[COleControlSite::SetWindowText](#setwindowtext)|Nastaví text hostované ovládacího prvku.|  
|[COleControlSite::ShowWindow](#showwindow)|Zobrazí nebo skryje ovládacího prvku lokality.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Načte informace klávesnice a klávesové zkratky pro hostované ovládací prvek.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Určuje, zda hostovaného ovládacího prvku ovládacího prvku bez oken.|  
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Obsahuje informace o zpracování pro ovládací prvek klávesnice.|  
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Soubor cookie bodu připojení ovládacího prvku.|  
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Různé stavy pro hostované ovládacího prvku.|  
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink` Souboru cookie ovládacího prvku.|  
|[COleControlSite::m_dwStyle](#m_dwstyle)|Styly ovládacího prvku hostované.|  
|[COleControlSite::m_hWnd](#m_hwnd)|Obslužná rutina ovládacího prvku lokality.|  
|[COleControlSite::m_iidEvents](#m_iidevents)|ID událostí rozhraní pro hostované ovládacího prvku.|  
|[COleControlSite::m_nID](#m_nid)|ID hostované ovládacího prvku.|  
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Ukazatel `IOleInPlaceActiveObject` objekt hostované ovládacího prvku.|  
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Kontejner hostované ovládacího prvku.|  
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Ukazatel `IOleInPlaceObject` objekt hostované ovládacího prvku.|  
|[COleControlSite::m_pObject](#m_pobject)|Ukazatel `IOleObjectInterface` rozhraní ovládacího prvku.|  
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Ukazatel `IOleInPlaceObjectWindowless` rozhraní ovládacího prvku.|  
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Ukazatel na objekt okna pro ovládací prvek hostované.|  
|[COleControlSite::m_rect](#m_rect)|Dimenze ovládacího prvku lokality.|  
  
## <a name="remarks"></a>Poznámky  
 Tato podpora je hlavním prostředkem, podle kterého embedded ovládací prvek ActiveX získává informace o umístění a rozsah jeho zobrazení lokality, její přezdívka, jeho uživatelské rozhraní, jeho vedlejším vlastnostem a dalším prostředkům poskytované jejímu kontejneru. `COleControlSite`plně implementuje [IOleControlSite](http://msdn.microsoft.com/library/windows/desktop/ms688502), [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706), [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), **IBoundObjectSite**, **INotifyDBEvents**, [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) rozhraní. Kromě toho se implementuje rozhraní IDispatch (poskytování podpory vedlejším vlastnostem a jímky událostí).  
  
 Chcete-li vytvořit k ActiveX řízení lokality pomocí `COleControlSite`, odvození třídy z `COleControlSite`. Ve vašem `CWnd`-přepsání v odvozené třídě pro kontejner (například vašem dialogovém okně) **CWnd::CreateControlSite** funkce.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxocc.h  
  
##  <a name="binddefaultproperty"></a>COleControlSite::BindDefaultProperty  
 Sváže volání objektu výchozí jednoduché vázané vlastnost, jako v knihovně typ označen jako základní kurzor, který je definován vlastností zdroje dat, uživatelské jméno, heslo a SQL zdroj dat ovládacího prvku.  
  
```  
virtual void BindDefaultProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    LPCTSTR szFieldName,  
    CWnd* pDSCWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Určuje, **DISPID** vlastnosti na ovládacího prvku vázané na data, která má být svázán s ovládacím zdroj dat.  
  
 `vtProp`  
 Určuje typ vlastnosti, která má být vázána – například `VT_BSTR`, **VT_VARIANT**a tak dále.  
  
 `szFieldName`  
 Určuje název sloupce, v kurzor poskytované prvek zdroje dat, ke kterému bude vázán vlastnost.  
  
 `pDSCWnd`  
 Ukazatel `CWnd`-odvozené objekt, který je hostitelem prvku zdroj dat, ke kterému bude vázán vlastnost.  
  
### <a name="remarks"></a>Poznámky  
 `CWnd` Objekt, na kterém volání této funkce musí být ovládacího prvku vázané na data.  
  
##  <a name="bindproperty"></a>COleControlSite::BindProperty  
 Sváže vlastnost jednoduché vázané volání objektu jako označený v knihovně typů základní kurzor, který je definován vlastností zdroje dat, uživatelské jméno, heslo a SQL zdroj dat ovládacího prvku.  
  
```  
virtual void BindProperty(
    DISPID dwDispId,  
    CWnd* pWndDSC);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispId*  
 Určuje, **DISPID** vlastnosti na ovládacího prvku vázané na data, která má být svázán s ovládacím zdroj dat.  
  
 `pWndDSC`  
 Ukazatel `CWnd`-odvozené objekt, který je hostitelem prvku zdroj dat, ke kterému bude vázán vlastnost.  
  
### <a name="remarks"></a>Poznámky  
 `CWnd` Objekt, na kterém volání této funkce musí být ovládacího prvku vázané na data.  
  
##  <a name="colecontrolsite"></a>COleControlSite::COleControlSite  
 Vytvoří nový `COleControlSite` objektu.  
  
```  
explicit COleControlSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parametry  
 `pCtrlCont`  
 Ukazatel na kontejneru ovládacího prvku (která představuje okna, který je hostitelem ovládacího prvku AtiveX).  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána [COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) funkce. Další informace o přizpůsobení vytvoření kontejnerů najdete v tématu [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).  
  
##  <a name="createcontrol"></a>COleControlSite::CreateControl  
 Vytvoří ovládacího prvku ActiveX hostované `COleControlSite` objektu.  
  
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
 `pWndCtrl`  
 Ukazatel na okno objekt reprezentující ovládacího prvku.  
  
 `clsid`  
 ID jedinečný třídy ovládacího prvku.  
  
 `lpszWindowName`  
 Ukazatel na text, který se zobrazí v ovládacím prvku. Nastaví hodnotu vlastnosti winodw titulek nebo Text (pokud existuje).  
  
 `dwStyle`  
 Styly systému Windows. Styly k dispozici jsou uvedeny v seznamu **poznámky** části.  
  
 `rect`  
 Určuje velikost a umístění ovládacího prvku. Může být buď `CRect` objekt nebo `RECT` struktury.  
  
 `nID`  
 Určuje ID ovládacího prvku podřízené okno.  
  
 `pPersist`  
 Ukazatel na `CFile` obsahující trvalý stav pro ovládací prvek. Výchozí hodnota je **NULL**, která určuje, že ovládací prvek se inicializuje bez obnovení stavu z jakékoli trvalé úložiště. Není-li **NULL**, by mělo být ukazatel na `CFile`-odvozené objekt, který obsahuje trvalé data ovládacího prvku ve formě datového proudu nebo úložiště. Tato data by byla uložena v předchozí aktivace klienta. `CFile` Může obsahovat další data, ale musí mít jeho ukazatele pro čtení a zápis nastavit do prvního bajtu trvalé dat při volání `CreateControl`.  
  
 `bStorage`  
 Určuje, zda data v `pPersist` by měl být interpretován jako `IStorage` nebo `IStream` data. Pokud data v `pPersist` je úložiště, `bStorage` by měla být **TRUE**. Pokud data v `pPersist` je datový proud, `bStorage` by měla být **FALSE**. Výchozí hodnota je **FALSE**.  
  
 `bstrLicKey`  
 Volitelné licence klíčová data. Tato data je potřeba pouze při vytváření ovládacích prvků, které vyžadují spuštění licenční klíč. Pokud ovládací prvek podporuje licencování, je nutné zadat licenční klíč pro vytvoření ovládacího prvku proběhla úspěšně. Výchozí hodnota je **NULL**.  
  
 `ppt`  
 Ukazatel **bodu** struktura, která obsahuje levém horním rohu ovládacího prvku. Velikost ovládacího prvku je dáno hodnotu *psize*. `ppt` a *psize* hodnoty jsou volitelné metodu sloužící k určení velikosti a pozice zpracovatelského ovládacího prvku.  
  
 *psize*  
 Ukazatel **velikost** struktura, která obsahuje velikosti ovládacího prvku. Levém horním rohu je dáno hodnotu `ppt`. `ppt` a *psize* hodnoty jsou volitelné metodu sloužící k určení velikosti a pozice zpracovatelského ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pouze podmnožinu Windows `dwStyle` příznaky podporuje `CreateControl`:  
  
- **Ws_visible –** vytvoří okno, které je původně viditelná. Vyžaduje, pokud chcete ovládat viditelné okamžitě, stejně jako obyčejnou windows.  
  
- **Ws_disabled –** vytvoří okno, které je původně zakázána. Okno zakázané nemůže přijímat vstup od uživatele. Můžete nastavit, pokud má vlastnost povoleno ovládacího prvku.  
  
- `WS_BORDER`Vytvoří okno se dynamicky čáry ohraničení. Můžete nastavit, pokud má vlastnost styl okraje na ovládací prvek.  
  
- **Ws_group –** Určuje první prvek skupiny ovládacích prvků. Uživatel může změnit fokus klávesnice z jednoho ovládacího prvku ve skupině na další pomocí klíčů směr. Všechny ovládací prvky, které jsou definované pomocí **ws_group –** styl po první prvek patří do stejné skupiny. Na další ovládací prvek s **ws_group –** styl končí skupině a spustí na další skupinu.  
  
- **Ws_tabstop –** určuje ovládací prvek, který může získat fokus klávesnice, při stisknutí klávesy TAB. Stisknutím klávesy TAB změní fokus klávesnice na další ovládací prvek z **ws_tabstop –** stylu.  
  
 Chcete-li vytvořit výchozí velikosti ovládacích prvků, použijte druhý přetížení.  
  
##  <a name="destroycontrol"></a>COleControlSite::DestroyControl  
 Zničí `COleControlSite` objektu.  
  
```  
virtual BOOL DestroyControl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo úspěšné, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Po dokončení objekt je uvolněn z paměti a všechny ukazatele na objekt již nejsou platné.  
  
##  <a name="doverb"></a>COleControlSite::DoVerb  
 Provede zadaný příkaz.  
  
```  
virtual HRESULT DoVerb(
    LONG nVerb,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nVerb`  
 Určuje příkaz provést. Může obsahovat jednu z těchto možností:  
  
|Hodnota|Význam|Symbol|  
|-----------|-------------|------------|  
|0|primární požadavek|`OLEIVERB_PRIMARY`|  
|-1|Sekundární operace|(Žádný)|  
|1|Zobrazí objekt pro úpravy.|`OLEIVERB_SHOW`|  
|-2|Upraví položky v samostatném okně.|`OLEIVERB_OPEN`|  
|-3|Skryje objektu.|`OLEIVERB_HIDE`|  
|-4|Aktivuje ovládací prvek na místě.|`OLEIVERB_UIACTIVATE`|  
|-5|Aktivuje ovládací prvek v místě, bez další prvky uživatelského rozhraní.|**OLEIVERB_INPLACEACTIVATE**|  
|-7|Zobrazení vlastností ovládacího prvku.|**OLEIVERB_PROPERTIES**|  
  
 `lpMsg`  
 Ukazatel na zprávu, která způsobila, že položka, která má být aktivována.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá přímo prostřednictvím ovládacího prvku `IOleObject` rozhraní provést zadanou operaci. Pokud je vyvolána výjimka v důsledku volání této funkce `HRESULT` vrácený kód chyby.  
  
 Další informace najdete v tématu [Funkce IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) ve Windows SDK.  
  
##  <a name="enabledsc"></a>COleControlSite::EnableDSC  
 Umožňuje data sourcing ovládacího prvku lokality.  
  
```  
virtual void EnableDSC();
```  
  
### <a name="remarks"></a>Poznámky  
 Voláno rámcem povolit a inicializace dat sourcing ovládacího prvku lokality. Funkci a poskytují přizpůsobené chování přepište.  
  
##  <a name="enablewindow"></a>COleControlSite::EnableWindow  
 Povolí nebo zakáže myši a klávesnice vstup do ovládacího prvku lokality.  
  
```  
virtual BOOL EnableWindow(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Určuje, jestli chcete povolit nebo zakázat okna: **TRUE** Pokud má být povoleno, jinak hodnota okno vstup **FALSE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla předtím zakázaná okna, jinak hodnota 0.  
  
##  <a name="freezeevents"></a>COleControlSite::FreezeEvents  
 Určuje, zda bude ovládací prvek webu zpracování nebo ignorovat události aktivována z ovládacího prvku.  
  
```  
void FreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parametry  
 `bFreeze`  
 Určuje, jestli chce přestane přijímat události ovládacího prvku lokality. Nenulové hodnoty, pokud ovládací prvek nepřijímá události; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bFreeze` je **TRUE**, řízení lokality požadavky na zastavení fring události ovládacího prvku. Pokud `bFreeze` je **FALSE**, chcete-li pokračovat, která iniciovala události ovládacího prvku požadavky řízení lokality.  
  
> [!NOTE]
>  Ovládací prvek není potřeba zastavit aktivaci událostí, pokud požadoval ovládacího prvku lokality. Pálení může pokračovat, ale všechny následné události budou ignorovány lokalita ovládacího prvku.  
  
##  <a name="getcontrolinfo"></a>COleControlSite::GetControlInfo  
 Načte informace o chování klávesnice a klávesové zkratky klávesnice ovládacího prvku.  
  
```  
void GetControlInfo();
```  
  
### <a name="remarks"></a>Poznámky  
 Informace jsou uloženy v [COleControlSite::m_ctlInfo](#m_ctlinfo).  
  
##  <a name="getdefbtncode"></a>COleControlSite::GetDefBtnCode  
 Určuje, zda je ovládací prvek výchozí tlačítko.  
  
```  
DWORD GetDefBtnCode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Může být jedna z následujících hodnot:  
  
- **DLGC_DEFPUSHBUTTON** ovládací prvek je výchozího tlačítka v dialogovém okně.  
  
- **DLGC_UNDEFPUSHBUTTON** ovládací prvek není výchozího tlačítka v dialogovém okně.  
  
- **0** ovládací prvek není tlačítko.  
  
##  <a name="getdlgctrlid"></a>COleControlSite::GetDlgCtrlID  
 Načte identifikátor ovládacího prvku.  
  
```  
virtual int GetDlgCtrlID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor položky dialogové okno ovládacího prvku.  
  
##  <a name="geteventiid"></a>COleControlSite::GetEventIID  
 Načte ukazatel na rozhraní event výchozí ovládacího prvku.  
  
```  
BOOL GetEventIID(IID* piid);
```  
  
### <a name="parameters"></a>Parametry  
 `piid`  
 Ukazatel na identifikátor rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo úspěšné, jinak hodnota 0. V případě úspěšného `piid` obsahuje ID rozhraní pro rozhraní událostí výchozí ovládacího prvku.  
  
##  <a name="getexstyle"></a>COleControlSite::GetExStyle  
 Načte rozšířené styly oken na.  
  
```  
virtual DWORD GetExStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Okno pro řízení je rozšířené styly.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li načíst regulární stylů, volejte [COleControlSite::GetStyle](#getstyle).  
  
##  <a name="getproperty"></a>COleControlSite::GetProperty  
 Získá vlastnost ovládacího prvku určeného `dwDispID`.  
  
```  
virtual void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Určuje ID odesílání vlastnost nalezena ve výchozím nastavení ovládacího prvku `IDispatch` rozhraní mají být načteny.  
  
 `vtProp`  
 Určuje typ vlastnosti, které mají být načteny. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvProp`  
 Adresa proměnné, která se zobrazí hodnota vlastnosti. Musí se shodovat s typem zadaným ve `vtProp`.  
  
### <a name="remarks"></a>Poznámky  
 Prostřednictvím je vrácena hodnota `pvProp`.  
  
##  <a name="getstyle"></a>COleControlSite::GetStyle  
 Načte styly ovládacího prvku lokality.  
  
```  
virtual DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Styly oken na.  
  
### <a name="remarks"></a>Poznámky  
 Seznam možných hodnot najdete v tématu [Windows styly](../../mfc/reference/styles-used-by-mfc.md#window-styles). Chcete-li načíst rozšířené styly ovládacího prvku lokality, volejte [COleControlSite::GetExStyle](#getexstyle).  
  
##  <a name="getwindowtext"></a>COleControlSite::GetWindowText  
 Načte aktuální text ovládacího prvku.  
  
```  
virtual void GetWindowText(CString& str) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Odkaz na `CString` objekt, který obsahuje aktuální text ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Pokud ovládací prvek podporuje uložených vlastností titulku, tato hodnota se vrátí. Pokud uložených vlastností popisek není podporován, je vrácena hodnota pro vlastnost Text.  
  
##  <a name="invokehelper"></a>COleControlSite::InvokeHelper  
 Vyvolá metody nebo vlastnosti určeného `dwDispID`, v rámci určeného `wFlags`.  
  
```  
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Určuje ID odesílání vlastnosti nebo metody, najít ovládacího prvku na `IDispatch` rozhraní, které má být volána.  
  
 `wFlags`  
 Příznaky popisující kontext volání volání metody IDispatch::Invoke. Pro možné `wFlags` hodnoty, najdete v části `IDispatch::Invoke` ve Windows SDK.  
  
 `vtRet`  
 Určuje typ vrácené hodnoty. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvRet`  
 Adresa proměnné, která bude přijímat hodnota vlastnosti nebo vrátit hodnotu. Musí se shodovat s typem zadaným ve `vtRet`.  
  
 `pbParamInfo`  
 Ukazatel na řetězce ukončené hodnotou null bajtů určení typů parametrů následující `pbParamInfo`. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Seznam proměnných parametrů typů zadaný v `pbParamInfo`.  
  
### <a name="remarks"></a>Poznámky  
 `pbParamInfo` Parametr určuje typy parametrů předaných pracovnímu metody nebo vlastnosti. Proměnné seznam argumentů je reprezentována... v deklaraci syntaxe.  
  
 Tato funkce převede parametry, které chcete **VARIANTARG** hodnoty a potom volá **volání metody IDispatch::Invoke** metoda na ovládací prvek. Pokud volání **volání metody IDispatch::Invoke** selže, tato funkce vyvolá výjimku. Pokud vrácený kód stavu **volání metody IDispatch::Invoke** je `DISP_E_EXCEPTION`, funkce vyvolá **COleDispatchException** objektu, jinak hodnota vyhodí `COleException`.  
  
##  <a name="invokehelperv"></a>COleControlSite::InvokeHelperV  
 Vyvolá metody nebo vlastnosti určeného `dwDispID`, v rámci určeného `wFlags`.  
  
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
 `dwDispID`  
 Určuje ID odesílání vlastnosti nebo metody, najít ovládacího prvku na `IDispatch` rozhraní, které má být volána.  
  
 `wFlags`  
 Příznaky popisující kontext volání volání metody IDispatch::Invoke.  
  
 `vtRet`  
 Určuje typ vrácené hodnoty. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvRet`  
 Adresa proměnné, která bude přijímat hodnota vlastnosti nebo vrátit hodnotu. Musí se shodovat s typem zadaným ve `vtRet`.  
  
 `pbParamInfo`  
 Ukazatel na řetězce ukončené hodnotou null bajtů určení typů parametrů následující `pbParamInfo`. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `argList`  
 Ukazatel na seznam argumentů s proměnnou.  
  
### <a name="remarks"></a>Poznámky  
 `pbParamInfo` Parametr určuje typy parametrů předaných pracovnímu metody nebo vlastnosti. Další parametry pro metodu nebo vlastnost volaná mohou být předány pomocí *VA_LIST –* parametr.  
  
 Obvykle se tato funkce je volána `COleControlSite::InvokeHelper`.  
  
##  <a name="isdefaultbutton"></a>COleControlSite::IsDefaultButton  
 Určuje, zda je ovládací prvek výchozí tlačítko.  
  
```  
BOOL IsDefaultButton();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je ovládací prvek výchozího tlačítka v okně, jinak hodnota nula.  
  
##  <a name="iswindowenabled"></a>COleControlSite::IsWindowEnabled  
 Určuje, zda je povoleno ovládacího prvku lokality.  
  
```  
virtual BOOL IsWindowEnabled() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty Pokud ovládací prvek je povoleno, jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota je načten z uložených vlastností ovládacího prvku povoleno.  
  
##  <a name="m_biswindowless"></a>COleControlSite::m_bIsWindowless  
 Určuje, zda je objekt ovládacího prvku bez oken.  
  
```  
BOOL m_bIsWindowless;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nenulové hodnoty, pokud ovládací prvek nemá žádný časový interval, v opačném případě hodnotu.  
  
##  <a name="m_ctlinfo"></a>COleControlSite::m_ctlInfo  
 Informace o zpracování vstupu klávesnice pomocí ovládacího prvku.  
  
```  
CONTROLINFO m_ctlInfo;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tyto informace jsou uloženy v [CONTROLINFO](http://msdn.microsoft.com/library/windows/desktop/ms680734) struktury.  
  
##  <a name="m_dweventsink"></a>COleControlSite::m_dwEventSink  
 Obsahuje spojovací bod soubor cookie z jímek událostí ovládacího prvku.  
  
```  
DWORD m_dwEventSink;  
```  
  
##  <a name="m_dwmiscstatus"></a>COleControlSite::m_dwMiscStatus  
 Obsahuje různé informace o řízení.  
  
```  
DWORD m_dwMiscStatus;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)ve Windows SDK.  
  
##  <a name="m_dwpropnotifysink"></a>COleControlSite::m_dwPropNotifySink  
 Obsahuje [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) souboru cookie.  
  
```  
DWORD m_dwPropNotifySink;  
```  
  
##  <a name="m_dwstyle"></a>COleControlSite::m_dwStyle  
 Obsahuje styly oken ovládacího prvku.  
  
```  
DWORD m_dwStyle;  
```  
  
##  <a name="m_hwnd"></a>COleControlSite::m_hWnd  
 Obsahuje `HWND` ovládacího prvku, nebo **NULL** Pokud ovládací prvek je bez oken.  
  
```  
HWND m_hWnd;  
```  
  
##  <a name="m_iidevents"></a>COleControlSite::m_iidEvents  
 Obsahuje ID rozhraní rozhraní jímky událostí výchozí ovládacího prvku.  
  
```  
IID m_iidEvents;  
```  
  
##  <a name="m_nid"></a>COleControlSite::m_nID  
 Obsahuje ID ovládacího prvku dialogové okno položky.  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_pactiveobject"></a>COleControlSite::m_pActiveObject  
 Obsahuje [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) rozhraní ovládacího prvku.  
  
```  
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;  
```  
  
##  <a name="m_pctrlcont"></a>COleControlSite::m_pCtrlCont  
 Obsahuje kontejneru ovládacího prvku (představující formuláře).  
  
```  
COleControlContainer* m_pCtrlCont;  
```  
  
##  <a name="m_pinplaceobject"></a>COleControlSite::m_pInPlaceObject  
 Obsahuje `IOleInPlaceObject` [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) rozhraní ovládacího prvku.  
  
```  
LPOLEINPLACEOBJECT m_pInPlaceObject;  
```  
  
##  <a name="m_pobject"></a>COleControlSite::m_pObject  
 Obsahuje **IOleObjectInterface** rozhraní ovládacího prvku.  
  
```  
LPOLEOBJECT m_pObject;  
```  
  
##  <a name="m_pwindowlessobject"></a>COleControlSite::m_pWindowlessObject  
 Obsahuje `IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) rozhraní ovládacího prvku.  
  
```  
IOleInPlaceObjectWindowless* m_pWindowlessObject;  
```  
  
##  <a name="m_pwndctrl"></a>COleControlSite::m_pWndCtrl  
 Obsahuje odkazy `CWnd` objekt, který reprezentuje samotném ovládacím prvku.  
  
```  
CWnd* m_pWndCtrl;  
```  
  
##  <a name="m_rect"></a>COleControlSite::m_rect  
 Obsahuje hranice ovládacího prvku, relativně k okno kontejneru.  
  
```  
CRect m_rect;  
```  
  
##  <a name="modifystyle"></a>COleControlSite::ModifyStyle  
 Upravit styly ovládacího prvku.  
  
```  
virtual BOOL ModifyStyle(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `dwRemove`  
 Styly odeberou z aktuální styly oken.  
  
 `dwAdd`  
 Styly přidávaného z aktuální styly oken.  
  
 `nFlags`  
 Okno umístění příznaky. Seznam možných hodnot najdete v tématu [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) funkce ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se změní stylů, jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Stock ovládacího prvku vlastnost povoleno budou upraveny tak, aby odpovídaly nastavení **ws_disabled –**. Uložených vlastností styl ohraničení ovládacího prvku budou upraveny tak, aby odpovídaly nastavení požadovaná pro `WS_BORDER`. Všechny ostatní styly použité přímo popisovač okna ovládacího prvku, pokud je k dispozici.  
  
 Upravit styly oken ovládacího prvku. Styly, které chcete přidat nebo odebrat lze spojovat pomocí bitová hodnota OR (&#124;) operátor. Najdete v článku [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) funkce ve Windows SDK pro informace o dostupném časovém intervalu stylů.  
  
 Pokud `nFlags` nenulový, `ModifyStyle` volá funkci Win32 `SetWindowPos`nebo ho překreslí okno tím, že zkombinujete `nFlags` s následující čtyři příznaky:  
  
- `SWP_NOSIZE`Zachová aktuální velikost.  
  
- `SWP_NOMOVE`Zachová aktuální pozici.  
  
- `SWP_NOZORDER`Zachová aktuální pořadí vykreslování.  
  
- `SWP_NOACTIVATE`Neaktivuje okna.  
  
 K úpravě časového období je rozšířené styly, volejte [ModifyStyleEx](#modifystyleex).  
  
##  <a name="modifystyleex"></a>COleControlSite::ModifyStyleEx  
 Změní rozšířené styly ovládacího prvku.  
  
```  
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `dwRemove`  
 Rozšířené styly odeberou z aktuální styly oken.  
  
 `dwAdd`  
 Rozšířené styly přidávaného z aktuální styly oken.  
  
 `nFlags`  
 Okno umístění příznaky. Seznam možných hodnot najdete v tématu [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) funkce ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se změní stylů, jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Uložených vlastností vzhledu ovládacího prvku budou upraveny tak, aby odpovídaly nastavení **WS_EX_CLIENTEDGE –**. Všechny ostatní rozšířené styly oken přímo do ovládacího prvku popisovač okna, se použijí, pokud je k dispozici.  
  
 Upravuje okno Rozšířené styly objekt ovládacího prvku lokality. Styly, které chcete přidat nebo odebrat lze spojovat pomocí bitová hodnota OR (&#124;) operátor. Najdete v článku [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkce ve Windows SDK pro informace o dostupném časovém intervalu stylů.  
  
 Pokud `nFlags` nenulový, `ModifyStyleEx` volá funkci Win32 `SetWindowPos`nebo ho překreslí okno tím, že zkombinujete `nFlags` s následující čtyři příznaky:  
  
- `SWP_NOSIZE`Zachová aktuální velikost.  
  
- `SWP_NOMOVE`Zachová aktuální pozici.  
  
- `SWP_NOZORDER`Zachová aktuální pořadí vykreslování.  
  
- `SWP_NOACTIVATE`Neaktivuje okna.  
  
 K úpravě časového období je rozšířené styly, volejte [ModifyStyle](#modifystyle).  
  
##  <a name="movewindow"></a>COleControlSite::MoveWindow  
 Změní umístění ovládacího prvku.  
  
```  
virtual void MoveWindow(
    int x,  
    int y,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Nové umístění na levé straně okna.  
  
 *y*  
 Nové umístění horní části okna.  
  
 `nWidth`  
 Šířka nové okno  
  
 `nHeight`  
 Nové výšku okna.  
  
##  <a name="quickactivate"></a>COleControlSite::QuickActivate  
 Rychlé aktivuje obsažené ovládacího prvku.  
  
```  
virtual BOOL QuickActivate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla aktivovaná řízení lokality, v opačném případě hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána pouze v případě, že uživatel je přepsání procesu vytvoření ovládacího prvku.  
  
 `IPersist*::Load` a `IPersist*::InitNew` metody by měla být volána po dokončení rychlé aktivace. Ovládací prvek zavede jeho připojení k kontejneru jímky během rychlé aktivace. Tato připojení však nejsou za provozu, dokud `IPersist*::Load` nebo `IPersist*::InitNew` byla volána.  
  
##  <a name="safesetproperty"></a>COleControlSite::SafeSetProperty  
 Nastaví vlastnost ovládacího prvku určeného `dwDispID`.  
  
```  
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Určuje ID odesílání vlastnosti nebo metody, najít ovládacího prvku na `IDispatch` rozhraní, které chcete nastavit.  
  
 `vtProp`  
 Určuje typ vlastnosti nastavit. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Jeden parametr v typu zadaném pomocí `vtProp`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Na rozdíl od `SetProperty` a `SetPropertyV`, pokud dojde k chybě (například došlo k pokusu o nastavení neexistující vlastnost), je vyvolána žádná výjimka.  
  
##  <a name="setdefaultbutton"></a>COleControlSite::SetDefaultButton  
 Nastaví ovládací prvek jako výchozího tlačítka.  
  
```  
void SetDefaultButton(BOOL bDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `bDefault`  
 Nenulové hodnoty, pokud se ovládací prvek by měl stane výchozí tlačítko; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Ovládací prvek musí mít **OLEMISC_ACTSLIKEBUTTON** stav nastaven bit.  
  
##  <a name="setdlgctrlid"></a>COleControlSite::SetDlgCtrlID  
 Změní hodnotu identifikátor položky dialogové okno ovládacího prvku.  
  
```  
virtual int SetDlgCtrlID(int nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Nová hodnota identifikátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného do předchozího dialogového okna položky identifikátor okna; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setfocus"></a>COleControlSite::SetFocus  
 Nastaví zaměření na ovládací prvek.  
  
```  
virtual CWnd* SetFocus();  
virtual CWnd* SetFocus(LPMSG lpmsg);
```  
  
### <a name="parameters"></a>Parametry  
 *lpmsg*  
 Ukazatel [MSG – struktura](../../mfc/reference/msg-structure1.md). Tato struktura obsahuje na aktivaci zpráv systému Windows `SetFocus` požadavku pro ovládací prvek obsažené v aktuální lokalitě ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na okno, která dřív měla fokus.  
  
##  <a name="setproperty"></a>COleControlSite::SetProperty  
 Nastaví vlastnost ovládacího prvku určeného `dwDispID`.  
  
```  
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Určuje ID odesílání vlastnosti nebo metody, najít ovládacího prvku na `IDispatch` rozhraní, které chcete nastavit.  
  
 `vtProp`  
 Určuje typ vlastnosti nastavit. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Jeden parametr v typu zadaném pomocí `vtProp`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `SetProperty` komunikaci se chyba, je vyvolána výjimka.  
  
 Typ výjimky je určen podle návratová hodnota pokus o nastavení vlastnosti nebo metody. Pokud je vrácenou hodnotou `DISP_E_EXCEPTION`, **COleDispatchExcpetion** výjimce dojde; jinak hodnota `COleException`.  
  
##  <a name="setpropertyv"></a>COleControlSite::SetPropertyV  
 Nastaví vlastnost ovládacího prvku určeného `dwDispID`.  
  
```  
virtual void SetPropertyV(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    va_list argList);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Určuje ID odesílání vlastnosti nebo metody, najít ovládacího prvku na `IDispatch` rozhraní, které chcete nastavit.  
  
 `vtProp`  
 Určuje typ vlastnosti nastavit. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `argList`  
 Ukazatel na seznam argumentů.  
  
### <a name="remarks"></a>Poznámky  
 Další parametry pro metodu nebo vlastnost volaná může být passeed pomocí *arg_list* parametr. Pokud `SetProperty` komunikaci se chyba, je vyvolána výjimka.  
  
 Typ výjimky je určen podle návratová hodnota pokus o nastavení vlastnosti nebo metody. Pokud je vrácenou hodnotou `DISP_E_EXCEPTION`, **COleDispatchExcpetion** výjimce dojde; jinak hodnota `COleException`.  
  
##  <a name="setwindowpos"></a>COleControlSite::SetWindowPos  
 Nastaví velikost, umístění a pořadí vykreslování ovládacího prvku lokality.  
  
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
 `pWndInsertAfter`  
 Ukazatel na okno.  
  
 *x*  
 Nové umístění na levé straně okna.  
  
 *y*  
 Nové umístění horní části okna.  
  
 `cx`  
 Šířka nové okno  
  
 `cy`  
 Nové výšku okna.  
  
 `nFlags`  
 Určuje interval pro změnu velikosti a rozmístění příznaky. Možné hodnoty, najdete v části poznámky pro [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu, jinak hodnota nula.  
  
##  <a name="setwindowtext"></a>COleControlSite::SetWindowText  
 Nastaví text pro řízení lokality.  
  
```  
virtual void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszString`  
 Ukazatel na řetězce ukončené hodnotou null má být použit jako nový název nebo ovládací prvek text.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se nejprve pokusí se nastavit uložených vlastností titulek. Pokud uložených vlastností popisek není podporován, je místo toho nastavit vlastnosti textu.  
  
##  <a name="showwindow"></a>COleControlSite::ShowWindow  
 Nastaví okna zobrazení stavu.  
  
```  
virtual BOOL ShowWindow(int nCmdShow);
```  
  
### <a name="parameters"></a>Parametry  
 `nCmdShow`  
 Určuje, jak řízení lokality se nezobrazí. Musí být jedna z následujících hodnot:  
  
- **SW_HIDE** skryje toto okno a předává aktivace pro další okno.  
  
- **SW_MINIMIZE** minimalizuje okno a aktivuje okno nejvyšší úrovně v seznamu systému.  
  
- **SW_RESTORE** Activates a zobrazí se okno. Pokud okno je minimalizován nebo maximalizovaný, Windows se obnoví na jeho původní velikost a umístění.  
  
- **SW_SHOW** aktivuje okně a zobrazí v jeho aktuální velikost a umístění.  
  
- **SW_SHOWMAXIMIZED** aktivuje okně a zobrazí jako maximalizovaném okně.  
  
- **SW_SHOWMINIMIZED** aktivuje okně a zobrazí jako ikonu.  
  
- **SW_SHOWMINNOACTIVE** zobrazí okno jako ikonu. Okno, který je aktuálně aktivní zůstává aktivní.  
  
- **SW_SHOWNA** zobrazí okno v jejím aktuálním stavu. Okno, který je aktuálně aktivní zůstává aktivní.  
  
- **SW_SHOWNOACTIVATE** okno se zobrazí v jeho nejnovější velikost a umístění. Okno, který je aktuálně aktivní zůstává aktivní.  
  
- **SW_SHOWNORMAL** Activates a zobrazí se okno. Pokud okno je minimalizován nebo maximalizovaný, Windows se obnoví na jeho původní velikost a umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl dříve viditelné; okna 0, pokud byl dříve skryté okna.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleControlContainer – třída](../../mfc/reference/colecontrolcontainer-class.md)
