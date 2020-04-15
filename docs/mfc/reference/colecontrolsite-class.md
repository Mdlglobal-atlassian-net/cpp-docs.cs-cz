---
title: COleControlSite – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 6cf12d017db1a1558b0dd915d9f3ba85894bee19
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366157"
---
# <a name="colecontrolsite-class"></a>COleControlSite – třída

Poskytuje podporu pro vlastní rozhraní řízení na straně klienta.

## <a name="syntax"></a>Syntaxe

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleControlSite::COleControlSite](#colecontrolsite)|Vytvoří `COleControlSite` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleControlSite::Vlastnost BindDefaultProperty](#binddefaultproperty)|Sváže výchozí vlastnost hostovaného ovládacího prvku se zdrojem dat.|
|[COleControlSite::Vlastnost BindProperty](#bindproperty)|Sváže vlastnost hostovaného ovládacího prvku se zdrojem dat.|
|[COleControlSite::CreateControl](#createcontrol)|Vytvoří hostovaný ovládací prvek ActiveX.|
|[COleControlSite::DestroyControl](#destroycontrol)|Zničí hostovaný ovládací prvek.|
|[COleControlSite::DoVerb](#doverb)|Provede konkrétní sloveso hostovaného ovládacího prvku.|
|[COleControlSite::EnableDSC](#enabledsc)|Umožňuje získávání dat pro řídicí lokalitu.|
|[COleControlSite::EnableWindow](#enablewindow)|Povolí řídicí lokalitu.|
|[COleControlSite::FreezeEvents](#freezeevents)|Určuje, zda řídicí lokalita přijímá události.|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Načte výchozí kód tlačítka pro hostovaný ovládací prvek.|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Načte identifikátor ovládacího prvku.|
|[COleControlSite::GeteventiID](#geteventiid)|Načte ID rozhraní události pro hostovaný ovládací prvek.|
|[COleControlSite::GetExStyle](#getexstyle)|Načte rozšířené styly řídicího webu.|
|[COleControlSite::Vlastnost GetProperty](#getproperty)|Načte určitou vlastnost hostovaného ovládacího prvku.|
|[COleControlSite::GetStyle](#getstyle)|Načte styly řídicího webu.|
|[COleControlSite::GetWindowText](#getwindowtext)|Načte text hostovaného ovládacího prvku.|
|[COleControlSite::InvokeHelper](#invokehelper)|Vyvolat konkrétní metodu hostovaného ovládacího prvku.|
|[COleControlSite::InvokeHelperV](#invokehelperv)|Vyvolat konkrétní metodu hostovaného ovládacího prvku s proměnnýseznam argumentů.|
|[COleControlSite::Tlačítko IsDefaultButton](#isdefaultbutton)|Určuje, zda je ovládací prvek výchozím tlačítkem v okně.|
|[COleControlSite::IsWindowEnabled COleControlSite::IsWindowEnabled COleControlSite::IsWindowEnabled COle](#iswindowenabled)|Zkontroluje viditelný stav řídicího webu.|
|[COleControlSite::Změnit styl](#modifystyle)|Upraví aktuální rozšířené styly řídicího webu.|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Upraví aktuální styly řídicího webu.|
|[COleControlSite::MoveWindow](#movewindow)|Změní polohu řídicího místa.|
|[COleControlSite::QuickActivate](#quickactivate)|Rychle aktivuje hostovaný ovládací prvek.|
|[COleControlSite::SafeSetProperty](#safesetproperty)|Nastaví vlastnost nebo metodu ovládacího prvku bez možnosti vyvolání výjimky.|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Nastaví výchozí tlačítko v okně.|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Načte identifikátor ovládacího prvku.|
|[COleControlSite::SetFocus](#setfocus)|Nastaví fokus na řídicí web.|
|[COleControlSite::SetProperty](#setproperty)|Nastaví určitou vlastnost hostovaného ovládacího prvku.|
|[COleControlSite::SetPropertyV](#setpropertyv)|Nastaví určitou vlastnost hostovaného ovládacího prvku se seznamem proměnných argumentů.|
|[COleControlSite::SetWindowPos](#setwindowpos)|Nastaví pozici řídicího webu.|
|[COleControlSite::SetWindowText](#setwindowtext)|Nastaví text hostovaného ovládacího prvku.|
|[COleControlSite::Zobrazitokno](#showwindow)|Zobrazí nebo skryje řídicí web.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Načte informace o klávesnici a mnemotechnické pomůcky pro hostované ovládací prvek.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Určuje, zda je hostovaný ovládací prvek ovládací prvek bez oken.|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Obsahuje informace o zpracování klávesnice pro ovládací prvek.|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Soubor cookie spojovacího bodu ovládacího prvku.|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Různé stavy pro hostovaný ovládací prvek.|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|Soubor `IPropertyNotifySink` cookie ovládacího prvku.|
|[COleControlSite::m_dwStyle](#m_dwstyle)|Styly hostovaného ovládacího prvku.|
|[COleControlSite::m_hWnd](#m_hwnd)|Popisovač řídicího místa.|
|[COleControlSite::m_iidEvents](#m_iidevents)|ID rozhraní události pro hostovaný ovládací prvek.|
|[COleControlSite::m_nID](#m_nid)|ID hostovaného ovládacího prvku.|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Ukazatel na `IOleInPlaceActiveObject` objekt hostovaného ovládacího prvku.|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Kontejner hostovaného ovládacího prvku.|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Ukazatel na `IOleInPlaceObject` objekt hostovaného ovládacího prvku.|
|[COleControlSite::m_pObject](#m_pobject)|Ukazatel na `IOleObjectInterface` rozhraní ovládacího prvku.|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Ukazatel na `IOleInPlaceObjectWindowless` rozhraní ovládacího prvku.|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Ukazatel na objekt okna pro hostovaný ovládací prvek.|
|[COleControlSite::m_rect](#m_rect)|Rozměry řídicího místa.|

## <a name="remarks"></a>Poznámky

Tato podpora je primárním prostředkem, kterým vložený ovládací prvek ActiveX získává informace o umístění a rozsahu jeho webu zobrazení, jeho zástupný název, jeho uživatelské rozhraní, jeho okolí vlastnosti a další prostředky poskytované jeho kontejneru. `COleControlSite`plně implementuje rozhraní [IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite), [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite), [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), `IBoundObjectSite`, `INotifyDBEvents`, [IRowSetNotify.](../../data/oledb/irowsetnotifyimpl-class.md) Kromě toho je implementováno také rozhraní IDispatch (poskytující podporu pro vlastnosti okolí a jímky událostí).

Chcete-li vytvořit lokalitu `COleControlSite`ovládacího prvku `COleControlSite`ActiveX pomocí , odvoděte třídu z aplikace . Ve `CWnd`vaší odvozené třídě pro kontejner (například dialogové okno) přepište `CWnd::CreateControlSite` funkci.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxocc.h

## <a name="colecontrolsitebinddefaultproperty"></a><a name="binddefaultproperty"></a>COleControlSite::Vlastnost BindDefaultProperty

Sváže výchozí vlastnost simple bound volajícího objektu, jak je označena v knihovně typů, s podkladovým kurzorem, který je definován vlastnostmi DataSource, UserName, Password a SQL ovládacího prvku zdroje dat.

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje dispid vlastnosti na ovládací prvek vázaný na data, který má být vázán na ovládací prvek zdroje dat.

*vtProp*<br/>
Určuje typ vlastnosti, která má být vázána, například VT_BSTR, VT_VARIANT a tak dále.

*szFieldName*<br/>
Určuje název sloupce v kurzoru poskytovaném ovládacím prvkem zdroje dat, ke kterému bude vlastnost vázána.

*pDSCWnd*<br/>
Ukazatel na `CWnd`-derived objekt, který je hostitelem ovládacího prvku zdroj dat, ke kterému bude vlastnost vázána.

### <a name="remarks"></a>Poznámky

Objekt, `CWnd` na kterém voláte tuto funkci, musí být ovládací prvek vázaný na data.

## <a name="colecontrolsitebindproperty"></a><a name="bindproperty"></a>COleControlSite::Vlastnost BindProperty

Sváže vlastnost simple bound volajícího objektu označenou v knihovně typů s podkladovým kurzorem, který je definován vlastnostmi DataSource, UserName, Password a SQL ovládacího prvku zdroje dat.

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>Parametry

*dwDispId*<br/>
Určuje dispid vlastnosti na ovládací prvek vázaný na data, který má být vázán na ovládací prvek zdroje dat.

*pWndDSC*<br/>
Ukazatel na `CWnd`-derived objekt, který je hostitelem ovládacího prvku zdroj dat, ke kterému bude vlastnost vázána.

### <a name="remarks"></a>Poznámky

Objekt, `CWnd` na kterém voláte tuto funkci, musí být ovládací prvek vázaný na data.

## <a name="colecontrolsitecolecontrolsite"></a><a name="colecontrolsite"></a>COleControlSite::COleControlSite

Vytvoří nový `COleControlSite` objekt.

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parametry

*pCtrlCont*<br/>
Ukazatel na kontejner ovládacího prvku (který představuje okno, které hostuje ovládací prvek AtiveX).

### <a name="remarks"></a>Poznámky

Tato funkce je volána funkcí [COccManager::CreateContainer.](../../mfc/reference/coccmanager-class.md#createcontainer) Další informace o přizpůsobení vytváření kontejnerů naleznete v tématu [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).

## <a name="colecontrolsitecreatecontrol"></a><a name="createcontrol"></a>COleControlSite::CreateControl

Vytvoří ovládací prvek ActiveX, `COleControlSite` který je hostován objektem.

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

*pWndCtrl*<br/>
Ukazatel na objekt okna představující ovládací prvek.

*Identifikátor clsid*<br/>
Jedinečné ID třídy ovládacího prvku.

*lpszNázev_okna*<br/>
Ukazatel na text, který má být zobrazen v ovládacím prvku. Nastaví hodnotu vlastnosti Titulek nebo Text winodw (pokud existuje).

*dwStyl*<br/>
Styly systému Windows. Dostupné styly jsou uvedeny v části **Poznámky.**

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku. Může to být `CRect` objekt `RECT` nebo struktura.

*Nid*<br/>
Určuje ID podřízeného okna ovládacího prvku.

*pPřetrvávají*<br/>
Ukazatel na `CFile` obsahující trvalý stav ovládacího prvku. Výchozí hodnota je NULL, označující, že ovládací prvek inicializuje sám bez obnovení jeho stavu z jakékoli trvalé úložiště. Pokud není NULL, by měl `CFile`být ukazatel na -odvozený objekt, který obsahuje trvalé data ovládacího prvku, ve formě datového proudu nebo úložiště. Tato data mohla být uložena při předchozí aktivaci klienta. Může `CFile` obsahovat jiná data, ale musí mít ukazatel pro čtení a zápis nastavený na `CreateControl`první bajt trvalých dat v době volání aplikace .

*bÚložiště*<br/>
Označuje, zda data v *pPersist* `IStorage` by `IStream` měla být interpretována jako nebo data. Pokud data v *pPersist* je úložiště, *bStorage* by měla být TRUE. Pokud data v *pPersist* je datový proud, *bStorage* by měl být FALSE. Výchozí hodnota je FALSE.

*bstrLicKey*<br/>
Volitelná data licenčního klíče. Tato data jsou potřebná pouze pro vytváření ovládacích prvků, které vyžadují licenční klíč za běhu. Pokud ovládací prvek podporuje licencování, je nutné zadat licenční klíč pro vytvoření ovládacího prvku úspěšné. Výchozí hodnota je NULL.

*Ppt*<br/>
Ukazatel na `POINT` strukturu, která obsahuje levý horní roh ovládacího prvku. Velikost ovládacího prvku je určena hodnotou *psize*. Hodnoty *ppt* a *psize* jsou volitelnou metodou určení velikosti a umístění opf ovládacího prvku.

*pvelikost*<br/>
Ukazatel na `SIZE` strukturu, která obsahuje velikost ovládacího prvku. Levý horní roh je určen hodnotou *ppt*. Hodnoty *ppt* a *psize* jsou volitelnou metodou určení velikosti a umístění opf ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pouze podmnožinu příznaků *Windows dwStyle* jsou podporovány `CreateControl`:

- WS_VISIBLE Vytvoří okno, které je zpočátku viditelné. Povinné, pokud chcete, aby byl ovládací prvek viditelný okamžitě, jako běžná okna.

- WS_DISABLED Vytvoří okno, které je zpočátku zakázáno. Zakázané okno nemůže přijímat vstup od uživatele. Lze nastavit, pokud má ovládací prvek vlastnost Enabled.

- WS_BORDER Vytvoří okno s tenkým ohraničením. Lze nastavit, pokud má ovládací prvek vlastnost BorderStyle.

- WS_GROUP Určuje první ovládací prvek skupiny ovládacích prvků. Uživatel může pomocí směrových kláves změnit fokus klávesnice z jednoho ovládacího prvku ve skupině na další. Všechny ovládací prvky definované WS_GROUP stylu po prvním ovládacím prvku patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP ukončí skupinu a spustí další skupinu.

- WS_TABSTOP Určuje ovládací prvek, který může přijímat fokus klávesnice, když uživatel stiskne klávesu TAB. Stisknutím klávesy TAB se změní zaostření klávesnice na další ovládací prvek WS_TABSTOP stylu.

Druhé přetížení použijte k vytvoření ovládacích prvků výchozí velikosti.

## <a name="colecontrolsitedestroycontrol"></a><a name="destroycontrol"></a>COleControlSite::DestroyControl

Zničí `COleControlSite` objekt.

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Po dokončení je objekt uvolněn z paměti a všechny ukazatele na objekt již nejsou platné.

## <a name="colecontrolsitedoverb"></a><a name="doverb"></a>COleControlSite::DoVerb

Provede zadané sloveso.

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>Parametry

*nSVNože*<br/>
Určuje sloveso, které má být spuštěno. Může obsahovat jednu z následujících možností:

|Hodnota|Význam|Symbol|
|-----------|-------------|------------|
|0|primární požadavek|OLEIVERB_PRIMARY|
|-1|Sekundární sloveso|(None)|
|1|Zobrazí objekt pro úpravy.|OLEIVERB_SHOW|
|-2|Upovená položku v samostatném okně.|OLEIVERB_OPEN|
|-3|Skryje objekt.|OLEIVERB_HIDE|
|-4|Aktivuje ovládací prvek na místě.|OLEIVERB_UIACTIVATE|
|-5|Aktivuje ovládací prvek na místě, bez dalších prvků uživatelského rozhraní.|OLEIVERB_INPLACEACTIVATE|
|-7|Zobrazení vlastností ovládacího prvku.|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
Ukazatel na zprávu, která způsobila aktivaci položky.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce přímo volá prostřednictvím rozhraní ovládacího `IOleObject` prvku ke spuštění zadaného slovesa. Pokud je vyvolána výjimka v důsledku tohoto volání funkce, je vrácen kód chyby HRESULT.

Další informace naleznete v tématu [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v sadě Windows SDK.

## <a name="colecontrolsiteenabledsc"></a><a name="enabledsc"></a>COleControlSite::EnableDSC

Umožňuje získávání dat pro řídicí lokalitu.

```
virtual void EnableDSC();
```

### <a name="remarks"></a>Poznámky

Volat rámci povolit a inicializovat získávání dat pro řídicí lokality. Přepsat tuto funkci poskytnout vlastní chování.

## <a name="colecontrolsiteenablewindow"></a><a name="enablewindow"></a>COleControlSite::EnableWindow

Povolí nebo zakáže vstup myši a klávesnice na řídicí web.

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda má být okno povoleno nebo zakázáno: PRAVDA, má-li být povolen vstup okna, jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo okno dříve zakázáno, jinak 0.

## <a name="colecontrolsitefreezeevents"></a><a name="freezeevents"></a>COleControlSite::FreezeEvents

Určuje, zda bude lokalita ovládacího prvku zpracovávat nebo ignorovat události vypálené z ovládacího prvku.

```
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bZmrazení*<br/>
Určuje, zda si lokalita ovládacího prvku přeje zastavit přijímání událostí. Nenulová, pokud ovládací prvek nepřijímá události; jinak nula.

### <a name="remarks"></a>Poznámky

Pokud *bFreeze* je PRAVDA, server ovládacího prvku požaduje ovládací prvek zastavit fring události. Pokud *bFreeze* je FALSE, server ovládacího prvku požaduje ovládací prvek pokračovat v spouštění událostí.

> [!NOTE]
> Ovládací prvek není nutné zastavit spouštění událostí, pokud o to kontrolní lokality. Může pokračovat v spouštění, ale všechny následné události budou ignorovány řídicím serverem.

## <a name="colecontrolsitegetcontrolinfo"></a><a name="getcontrolinfo"></a>COleControlSite::GetControlInfo

Načte informace o ovládacím prvku klávesnice mnemotechnické pomůcky a chování klávesnice.

```
void GetControlInfo();
```

### <a name="remarks"></a>Poznámky

Informace jsou uloženy v [COleControlSite::m_ctlInfo](#m_ctlinfo).

## <a name="colecontrolsitegetdefbtncode"></a><a name="getdefbtncode"></a>COleControlSite::GetDefBtnCode

Určuje, zda je ovládací prvek výchozím tlačítkem.

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>Návratová hodnota

Může se na nich vyvěšovat jedna z následujících hodnot:

- DLGC_DEFPUSHBUTTON Control je výchozí tlačítko v dialogovém okně.

- DLGC_UNDEFPUSHBUTTON Control není v dialogovém okně výchozím tlačítkem.

- **0** Ovládání není tlačítko.

## <a name="colecontrolsitegetdlgctrlid"></a><a name="getdlgctrlid"></a>COleControlSite::GetDlgCtrlID

Načte identifikátor ovládacího prvku.

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor položky dialogu ovládacího prvku.

## <a name="colecontrolsitegeteventiid"></a><a name="geteventiid"></a>COleControlSite::GeteventiID

Načte ukazatel na výchozí rozhraní události ovládacího prvku.

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>Parametry

*piid*<br/>
Ukazatel na ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, jinak 0. V případě *úspěchu, piid* obsahuje ID rozhraní pro výchozí rozhraní události ovládacího prvku.

## <a name="colecontrolsitegetexstyle"></a><a name="getexstyle"></a>COleControlSite::GetExStyle

Načte rozšířené styly okna.

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Rozšířené styly ovládacího okna.

### <a name="remarks"></a>Poznámky

Chcete-li načíst běžné styly, zavolejte [COleControlSite::GetStyle](#getstyle).

## <a name="colecontrolsitegetproperty"></a><a name="getproperty"></a>COleControlSite::Vlastnost GetProperty

Získá vlastnost ovládacího prvku určené *dwDispID*.

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identifikuje ID odeslání vlastnosti, které lze nalézt `IDispatch` na výchozí rozhraní ovládacího prvku, které mají být načteny.

*vtProp*<br/>
Určuje typ vlastnosti, která má být načtena. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvProp*<br/>
Adresa proměnné, která obdrží hodnotu vlastnosti. Musí odpovídat typu určenému *vtProp*.

### <a name="remarks"></a>Poznámky

Hodnota je vrácena prostřednictvím *pvProp*.

## <a name="colecontrolsitegetstyle"></a><a name="getstyle"></a>COleControlSite::GetStyle

Načte styly řídicího webu.

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Styly okna.

### <a name="remarks"></a>Poznámky

Seznam možných hodnot naleznete v tématu [Styly systému Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles). Chcete-li načíst rozšířené styly lokality ovládacího prvku, zavolejte [COleControlSite::GetExStyle](#getexstyle).

## <a name="colecontrolsitegetwindowtext"></a><a name="getwindowtext"></a>COleControlSite::GetWindowText

Načte aktuální text ovládacího prvku.

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Odkaz na `CString` objekt, který obsahuje aktuální text ovládacího prvku.

### <a name="remarks"></a>Poznámky

Pokud ovládací prvek podporuje caption stock vlastnost, tato hodnota je vrácena. Pokud vlastnost Caption stock není podporována, je vrácena hodnota vlastnosti Text.

## <a name="colecontrolsiteinvokehelper"></a><a name="invokehelper"></a>COleControlSite::InvokeHelper

Vyvolá metodu nebo vlastnost určenou *dwDispID*v kontextu určeném *wFlags*.

```
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identifikuje ID odeslání vlastnosti nebo metody, které se `IDispatch` nacházejí v rozhraní ovládacího prvku, které mají být vyvolány.

*wPříznaky*<br/>
Příznaky popisující kontext volání iDispatch::Invoke. Možné hodnoty *wFlags* `IDispatch::Invoke` naleznete v sadě Windows SDK.

*vtRet*<br/>
Určuje typ vrácené hodnoty. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Adresa proměnné, která obdrží hodnotu vlastnosti nebo vrácenou hodnotu. Musí odpovídat typu určenému *vtRet*.

*pbParamInfo*<br/>
Ukazatel na řetězec bajtů ukončený nulou určující typy parametrů následujících *po pbParamInfo*. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Variabilní seznam parametrů, typů určených v *pbParamInfo*.

### <a name="remarks"></a>Poznámky

Parametr *pbParamInfo* určuje typy parametrů předaných metodě nebo vlastnosti. Variabilní seznam argumentů je reprezentován ... v deklaraci syntaxe.

Tato funkce převede parametry na hodnoty VARIANTARG `IDispatch::Invoke` a poté vyvolá metodu ovládacího prvku. Pokud volání `IDispatch::Invoke` nezdaří, tato funkce vyvolá výjimku. Pokud je stavový `IDispatch::Invoke` `DISP_E_EXCEPTION`kód vrácený , `COleDispatchException` tato funkce vyvolá `COleException`objekt, jinak vyvolá .

## <a name="colecontrolsiteinvokehelperv"></a><a name="invokehelperv"></a>COleControlSite::InvokeHelperV

Vyvolá metodu nebo vlastnost určenou *dwDispID*v kontextu určeném *wFlags*.

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

*dwDispID*<br/>
Identifikuje ID odeslání vlastnosti nebo metody, které se `IDispatch` nacházejí v rozhraní ovládacího prvku, které mají být vyvolány.

*wPříznaky*<br/>
Příznaky popisující kontext volání iDispatch::Invoke.

*vtRet*<br/>
Určuje typ vrácené hodnoty. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Adresa proměnné, která obdrží hodnotu vlastnosti nebo vrácenou hodnotu. Musí odpovídat typu určenému *vtRet*.

*pbParamInfo*<br/>
Ukazatel na řetězec bajtů ukončený nulou určující typy parametrů následujících *po pbParamInfo*. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*seznam arglist*<br/>
Ukazatel na seznam proměnných argumentů.

### <a name="remarks"></a>Poznámky

Parametr *pbParamInfo* určuje typy parametrů předaných metodě nebo vlastnosti. Další parametry pro volanou metodu nebo vlastnost lze předat pomocí *parametru va_list.*

Obvykle je tato funkce `COleControlSite::InvokeHelper`volána společností .

## <a name="colecontrolsiteisdefaultbutton"></a><a name="isdefaultbutton"></a>COleControlSite::Tlačítko IsDefaultButton

Určuje, zda je ovládací prvek výchozím tlačítkem.

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je ovládací prvek výchozím tlačítkem v okně, jinak nula.

## <a name="colecontrolsiteiswindowenabled"></a><a name="iswindowenabled"></a>COleControlSite::IsWindowEnabled COleControlSite::IsWindowEnabled COleControlSite::IsWindowEnabled COle

Určuje, zda je povolena lokalita ovládacího prvku.

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je ovládací prvek povolen, jinak nula.

### <a name="remarks"></a>Poznámky

Hodnota je načtena z vlastnosti Enabled stock ovládacího prvku.

## <a name="colecontrolsitem_biswindowless"></a><a name="m_biswindowless"></a>COleControlSite::m_bIsWindowless

Určuje, zda je objekt ovládací prvek bez oken.

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>Poznámky

Nenulová, pokud ovládací prvek nemá žádné okno, jinak nula.

## <a name="colecontrolsitem_ctlinfo"></a><a name="m_ctlinfo"></a>COleControlSite::m_ctlInfo

Informace o tom, jak je ovládáním zpracováno zadávání montovny klávesnicí.

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>Poznámky

Tyto informace jsou uloženy ve struktuře [CONTROLINFO.](/windows/win32/api/ocidl/ns-ocidl-controlinfo)

## <a name="colecontrolsitem_dweventsink"></a><a name="m_dweventsink"></a>COleControlSite::m_dwEventSink

Obsahuje soubor cookie spojovacího bodu z jímky událostí ovládacího prvku.

```
DWORD m_dwEventSink;
```

## <a name="colecontrolsitem_dwmiscstatus"></a><a name="m_dwmiscstatus"></a>COleControlSite::m_dwMiscStatus

Obsahuje různé informace o ovládacím prvku.

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)v sadě Windows SDK.

## <a name="colecontrolsitem_dwpropnotifysink"></a><a name="m_dwpropnotifysink"></a>COleControlSite::m_dwPropNotifySink

Obsahuje soubor cookie [IPropertyNotifySink.](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)

```
DWORD m_dwPropNotifySink;
```

## <a name="colecontrolsitem_dwstyle"></a><a name="m_dwstyle"></a>COleControlSite::m_dwStyle

Obsahuje window styly ovládacího prvku.

```
DWORD m_dwStyle;
```

## <a name="colecontrolsitem_hwnd"></a><a name="m_hwnd"></a>COleControlSite::m_hWnd

Obsahuje HWND ovládacího prvku nebo NULL, pokud je ovládací prvek bez oken.

```
HWND m_hWnd;
```

## <a name="colecontrolsitem_iidevents"></a><a name="m_iidevents"></a>COleControlSite::m_iidEvents

Obsahuje ID rozhraní výchozího rozhraní jímky událostí ovládacího prvku.

```
IID m_iidEvents;
```

## <a name="colecontrolsitem_nid"></a><a name="m_nid"></a>COleControlSite::m_nID

Obsahuje ID dialogového okna ovládacího prvku.

```
UINT m_nID;
```

## <a name="colecontrolsitem_pactiveobject"></a><a name="m_pactiveobject"></a>COleControlSite::m_pActiveObject

Obsahuje rozhraní [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) ovládacího prvku.

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

## <a name="colecontrolsitem_pctrlcont"></a><a name="m_pctrlcont"></a>COleControlSite::m_pCtrlCont

Obsahuje kontejner ovládacího prvku (představující formulář).

```
COleControlContainer* m_pCtrlCont;
```

## <a name="colecontrolsitem_pinplaceobject"></a><a name="m_pinplaceobject"></a>COleControlSite::m_pInPlaceObject

`IOleInPlaceObject` Obsahuje rozhraní [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) ovládacího prvku.

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

## <a name="colecontrolsitem_pobject"></a><a name="m_pobject"></a>COleControlSite::m_pObject

Obsahuje `IOleObjectInterface` rozhraní ovládacího prvku.

```
LPOLEOBJECT m_pObject;
```

## <a name="colecontrolsitem_pwindowlessobject"></a><a name="m_pwindowlessobject"></a>COleControlSite::m_pWindowlessObject

`IOleInPlaceObjectWindowless`Obsahuje [rozhraní IOleInPlaceObjectLess](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) ovládacího prvku.

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

## <a name="colecontrolsitem_pwndctrl"></a><a name="m_pwndctrl"></a>COleControlSite::m_pWndCtrl

Obsahuje ukazatel na `CWnd` objekt, který představuje samotný ovládací prvek.

```
CWnd* m_pWndCtrl;
```

## <a name="colecontrolsitem_rect"></a><a name="m_rect"></a>COleControlSite::m_rect

Obsahuje hranice ovládacího prvku vzhledem k okno kontejneru.

```
CRect m_rect;
```

## <a name="colecontrolsitemodifystyle"></a><a name="modifystyle"></a>COleControlSite::Změnit styl

Upraví styly ovládacího prvku.

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*dwOdstranit*<br/>
Styly, které mají být odebrány z aktuálních stylů oken.

*dwAdd*<br/>
Styly, které mají být přidány z aktuálních stylů oken.

*nPříznaky*<br/>
Příznaky umístění okna. Seznam možných hodnot naleznete v tématu [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) funkce v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se změní styly, jinak nula.

### <a name="remarks"></a>Poznámky

Vlastnost Enabled ovládacího prvku bude upravena tak, aby odpovídala nastavení pro WS_DISABLED. Vlastnost Border Style ovládacího prvku bude upravena tak, aby odpovídala požadovanému nastavení pro WS_BORDER. Všechny ostatní styly jsou použity přímo na popisovač okna ovládacího prvku, pokud je k dispozici.

Upraví styly oken ovládacího prvku. Styly, které mají být přidány nebo odebrány, lze kombinovat pomocí bitového operátoru OR ( &#124;). Informace o dostupných stylech oken naleznete v části [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v ksouboru Windows SDK.

Pokud *nFlags* je `ModifyStyle` nenulová, volá `SetWindowPos`Win32 funkce a překreslí okno kombinací *nFlags* s následujícími čtyřmi příznaky:

- SWP_NOSIZE Zachová aktuální velikost.

- SWP_NOMOVE Zachová aktuální pozici.

- SWP_NOZORDER Zachová aktuální pořadí Z.

- SWP_NOACTIVATE Neaktivuje okno.

Chcete-li upravit rozšířené styly okna, zavolejte [ModifyStyleEx](#modifystyleex).

## <a name="colecontrolsitemodifystyleex"></a><a name="modifystyleex"></a>COleControlSite::ModifyStyleEx

Upraví rozšířené styly ovládacího prvku.

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*dwOdstranit*<br/>
Rozšířené styly, které mají být odebrány z aktuálních stylů oken.

*dwAdd*<br/>
Rozšířené styly, které mají být přidány z aktuálních stylů oken.

*nPříznaky*<br/>
Příznaky umístění okna. Seznam možných hodnot naleznete v tématu [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) funkce v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se změní styly, jinak nula.

### <a name="remarks"></a>Poznámky

Vlastnost Vzhled ovládacího prvku bude upravena tak, aby odpovídala nastavení pro WS_EX_CLIENTEDGE. Všechny ostatní rozšířené styly okna jsou použity přímo na popisovač okna ovládacího prvku, pokud je k dispozici.

Změní rozšířené styly okna objektu řídicího místa. Styly, které mají být přidány nebo odebrány, lze kombinovat pomocí bitového operátoru OR ( &#124;). Informace o dostupných stylech oken naleznete v části [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v ksouboru Windows SDK.

Pokud *nFlags* je `ModifyStyleEx` nenulová, volá `SetWindowPos`Win32 funkce a překreslí okno kombinací *nFlags* s následujícími čtyřmi příznaky:

- SWP_NOSIZE Zachová aktuální velikost.

- SWP_NOMOVE Zachová aktuální pozici.

- SWP_NOZORDER Zachová aktuální pořadí Z.

- SWP_NOACTIVATE Neaktivuje okno.

Chcete-li upravit rozšířené styly okna, zavolejte [ModifyStyle](#modifystyle).

## <a name="colecontrolsitemovewindow"></a><a name="movewindow"></a>COleControlSite::MoveWindow

Změní polohu ovládacího prvku.

```
virtual void MoveWindow(
    int x,
    int y,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Nová poloha levé strany okna.

*Y*<br/>
Nová pozice v horní části okna.

*nŠířka*<br/>
Nová šířka okna

*nVýška*<br/>
Nová výška okna.

## <a name="colecontrolsitequickactivate"></a><a name="quickactivate"></a>COleControlSite::QuickActivate

Rychle aktivuje uzavřený ovládací prvek.

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla aktivována řídicí lokalita, jinak nula.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána pouze v případě, že uživatel přepíše proces vytváření ovládacího prvku.

Metody `IPersist*::Load` `IPersist*::InitNew` a by měly být volány po rychlé aktivaci dojde. Ovládací prvek by měl navázat jeho připojení k jímky kontejneru během rychlé aktivace. Tato připojení však nejsou `IPersist*::Load` `IPersist*::InitNew` aktivní, dokud nebo byla volána.

## <a name="colecontrolsitesafesetproperty"></a><a name="safesetproperty"></a>COleControlSite::SafeSetProperty

Nastaví vlastnost ovládacího prvku určenou *dwDispID*.

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identifikuje ID odeslání vlastnosti nebo metody, které se `IDispatch` nacházejí v rozhraní ovládacího prvku, které mají být nastaveny.

*vtProp*<br/>
Určuje typ vlastnosti, která má být nastavena. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Jeden parametr typu určeného *vtProp*.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Na `SetProperty` `SetPropertyV`rozdíl od a , pokud dojde k chybě (například při pokusu o nastavení neexistující vlastnost), není vyvolána žádná výjimka.

## <a name="colecontrolsitesetdefaultbutton"></a><a name="setdefaultbutton"></a>COleControlSite::SetDefaultButton

Nastaví ovládací prvek jako výchozí tlačítko.

```
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*bVýchozí*<br/>
Nenulová, pokud by se ovládací prvek měl stát výchozím tlačítkem; jinak nula.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Ovládací prvek musí mít nastaven OLEMISC_ACTSLIKEBUTTON stavový bit.

## <a name="colecontrolsitesetdlgctrlid"></a><a name="setdlgctrlid"></a>COleControlSite::SetDlgCtrlID

Změní hodnotu identifikátoru položky dialogového okna ovládacího prvku.

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Nová hodnota identifikátoru.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, předchozí dialogová položka identifikátor okna; jinak 0.

### <a name="remarks"></a>Poznámky

## <a name="colecontrolsitesetfocus"></a><a name="setfocus"></a>COleControlSite::SetFocus

Nastaví fokus na ovládací prvek.

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>Parametry

*lpmsg*<br/>
Ukazatel na [strukturu MSG](/windows/win32/api/winuser/ns-winuser-msg). Tato struktura obsahuje zprávu systému Windows, která spouští `SetFocus` požadavek na ovládací prvek obsažený v aktuální lokalitě ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno, které dříve mělo fokus.

## <a name="colecontrolsitesetproperty"></a><a name="setproperty"></a>COleControlSite::SetProperty

Nastaví vlastnost ovládacího prvku určenou *dwDispID*.

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identifikuje ID odeslání vlastnosti nebo metody, které se `IDispatch` nacházejí v rozhraní ovládacího prvku, které mají být nastaveny.

*vtProp*<br/>
Určuje typ vlastnosti, která má být nastavena. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Jeden parametr typu určeného *vtProp*.

### <a name="remarks"></a>Poznámky

Pokud `SetProperty` dojde k chybě, je vyvolána výjimka.

Typ výjimky je určen vrácenou hodnotou pokusu o nastavení vlastnosti nebo metody. Pokud je `DISP_E_EXCEPTION`vrácená `COleDispatchExcpetion` hodnota , je vyvolána; jinak `COleException`.

## <a name="colecontrolsitesetpropertyv"></a><a name="setpropertyv"></a>COleControlSite::SetPropertyV

Nastaví vlastnost ovládacího prvku určenou *dwDispID*.

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identifikuje ID odeslání vlastnosti nebo metody, které se `IDispatch` nacházejí v rozhraní ovládacího prvku, které mají být nastaveny.

*vtProp*<br/>
Určuje typ vlastnosti, která má být nastavena. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*seznam arglist*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Další parametry pro volanou metodu nebo vlastnost lze předat pomocí *parametru arg_list.* Pokud `SetProperty` dojde k chybě, je vyvolána výjimka.

Typ výjimky je určen vrácenou hodnotou pokusu o nastavení vlastnosti nebo metody. Pokud je `DISP_E_EXCEPTION`vrácená `COleDispatchExcpetion` hodnota , je vyvolána; jinak `COleException`.

## <a name="colecontrolsitesetwindowpos"></a><a name="setwindowpos"></a>COleControlSite::SetWindowPos

Nastaví velikost, umístění a pořadí Z řídicího webu.

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

*pWndInsertPo*<br/>
Ukazatel na okno.

*X*<br/>
Nová poloha levé strany okna.

*Y*<br/>
Nová pozice v horní části okna.

*Cx*<br/>
Nová šířka okna

*Cy*<br/>
Nová výška okna.

*nPříznaky*<br/>
Určuje příznaky velikosti a umístění okna. Možné hodnoty naleznete v části Poznámky pro [setwindowpos](/windows/win32/api/winuser/nf-winuser-setwindowpos) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, jinak nula.

## <a name="colecontrolsitesetwindowtext"></a><a name="setwindowtext"></a>COleControlSite::SetWindowText

Nastaví text pro řídicí web.

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
Ukazatel na řetězec s nulovým ukončením, který má být použit jako nový text nadpisu nebo ovládacího prvku.

### <a name="remarks"></a>Poznámky

Tato funkce se nejprve pokusí nastavit vlastnost Caption stock. Pokud vlastnost Caption stock není podporována, je místo toho nastavena vlastnost Text.

## <a name="colecontrolsiteshowwindow"></a><a name="showwindow"></a>COleControlSite::Zobrazitokno

Nastaví stav zobrazení okna.

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parametry

*nCmdZobrazit*<br/>
Určuje způsob zobrazení řídicí lokality. Musí se jednat o jednu z následujících hodnot:

- SW_HIDE Skryje toto okno a předá aktivaci do jiného okna.

- SW_MINIMIZE Minimalizuje okno a aktivuje okno nejvyšší úrovně v seznamu systému.

- SW_RESTORE Aktivuje a zobrazí okno. Pokud je okno minimalizováno nebo maximalizováno, systém Windows jej obnoví do původní velikosti a umístění.

- SW_SHOW Aktivuje okno a zobrazí ho v aktuální velikosti a poloze.

- SW_SHOWMAXIMIZED Aktivuje okno a zobrazí ho jako maximalizované okno.

- SW_SHOWMINIMIZED Aktivuje okno a zobrazí ho jako ikonu.

- SW_SHOWMINNOACTIVE Zobrazí okno jako ikonu. Okno, které je aktuálně aktivní, zůstane aktivní.

- SW_SHOWNA Zobrazí okno v aktuálním stavu. Okno, které je aktuálně aktivní, zůstane aktivní.

- SW_SHOWNOACTIVATE Zobrazí okno v nejnovější velikosti a poloze. Okno, které je aktuálně aktivní, zůstane aktivní.

- SW_SHOWNORMAL Aktivuje a zobrazí okno. Pokud je okno minimalizováno nebo maximalizováno, systém Windows jej obnoví do původní velikosti a umístění.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo okno dříve viditelné; 0, pokud bylo okno dříve skryto.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer – třída](../../mfc/reference/colecontrolcontainer-class.md)
