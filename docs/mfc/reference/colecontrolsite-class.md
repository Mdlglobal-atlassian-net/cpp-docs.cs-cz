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
ms.openlocfilehash: 9b9b68a001acdf4b08d9cfc01cc67c43217d9a57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504306"
---
# <a name="colecontrolsite-class"></a>COleControlSite – třída

Poskytuje podporu pro vlastní rozhraní ovládacích prvků na straně klienta.

## <a name="syntax"></a>Syntaxe

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleControlSite::COleControlSite](#colecontrolsite)|`COleControlSite` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Váže výchozí vlastnost hostovaného ovládacího prvku na zdroj dat.|
|[COleControlSite::BindProperty](#bindproperty)|Váže vlastnost hostovaného ovládacího prvku na zdroj dat.|
|[COleControlSite::CreateControl](#createcontrol)|Vytvoří hostovaný ovládací prvek ActiveX.|
|[COleControlSite::DestroyControl](#destroycontrol)|Zničí hostovaný ovládací prvek.|
|[COleControlSite::DoVerb](#doverb)|Provede konkrétní příkaz hostovaného ovládacího prvku.|
|[COleControlSite::EnableDSC](#enabledsc)|Povoluje pro web ovládacího prvku datový původ.|
|[COleControlSite::EnableWindow](#enablewindow)|Povolí ovládací prvek webu.|
|[COleControlSite:: Freezeevents.](#freezeevents)|Určuje, zda server ovládacího prvku přijímá události.|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Načte výchozí kód tlačítka pro hostovaný ovládací prvek.|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Načte identifikátor ovládacího prvku.|
|[COleControlSite::GetEventIID](#geteventiid)|Načte ID rozhraní události pro hostovaný ovládací prvek.|
|[COleControlSite::GetExStyle](#getexstyle)|Načte rozšířené styly webu ovládacího prvku.|
|[COleControlSite::GetProperty](#getproperty)|Načte konkrétní vlastnost hostovaného ovládacího prvku.|
|[COleControlSite::GetStyle](#getstyle)|Načte styly webu ovládacího prvku.|
|[COleControlSite::GetWindowText](#getwindowtext)|Načte text hostovaného ovládacího prvku.|
|[COleControlSite::InvokeHelper](#invokehelper)|Vyvolat konkrétní metodu hostovaného ovládacího prvku.|
|[COleControlSite::InvokeHelperV](#invokehelperv)|Vyvolejte konkrétní metodu hostovaného ovládacího prvku se seznamem proměnných argumentů.|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Určuje, zda je ovládací prvek v okně výchozím tlačítkem.|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Kontroluje stav viditelnosti lokality ovládacího prvku.|
|[COleControlSite::ModifyStyle](#modifystyle)|Upraví aktuální rozšířené styly webu ovládacího prvku.|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Upraví aktuální styly webu ovládacího prvku.|
|[COleControlSite::MoveWindow](#movewindow)|Změní pozici lokality ovládacího prvku.|
|[COleControlSite::QuickActivate](#quickactivate)|Rychle aktivuje hostovaný ovládací prvek.|
|[COleControlSite::SafeSetProperty](#safesetproperty)|Nastaví vlastnost nebo metodu ovládacího prvku bez šance na vyvolání výjimky.|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Nastaví výchozí tlačítko v okně.|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Načte identifikátor ovládacího prvku.|
|[COleControlSite::SetFocus](#setfocus)|Nastaví fokus na lokalitu ovládacího prvku.|
|[COleControlSite::SetProperty](#setproperty)|Nastaví konkrétní vlastnost hostovaného ovládacího prvku.|
|[COleControlSite::SetPropertyV](#setpropertyv)|Nastaví konkrétní vlastnost hostovaného ovládacího prvku se seznamem proměnných argumentů.|
|[COleControlSite::SetWindowPos](#setwindowpos)|Nastaví pozici ovládacího prvku lokality.|
|[COleControlSite::SetWindowText](#setwindowtext)|Nastaví text hostovaného ovládacího prvku.|
|[COleControlSite::ShowWindow](#showwindow)|Zobrazí nebo skryje web ovládacího prvku.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Načte informace o klávesnici a klávesové zkratky pro hostovaný ovládací prvek.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Určuje, zda je hostovaný ovládací prvek ovládacím prvkem bez oken.|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Obsahuje informace o zpracování klávesnice pro ovládací prvek.|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Soubor cookie spojovacího bodu ovládacího prvku|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Různé stavy pro hostovaný ovládací prvek.|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink` Soubor cookie ovládacího prvku|
|[COleControlSite::m_dwStyle](#m_dwstyle)|Styly hostovaného ovládacího prvku|
|[COleControlSite::m_hWnd](#m_hwnd)|Popisovač lokality ovládacího prvku.|
|[COleControlSite::m_iidEvents](#m_iidevents)|ID rozhraní události pro hostovaný ovládací prvek.|
|[COleControlSite::m_nID](#m_nid)|ID hostovaného ovládacího prvku|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Ukazatel na `IOleInPlaceActiveObject` objekt hostovaného ovládacího prvku.|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Kontejner hostovaného ovládacího prvku|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Ukazatel na `IOleInPlaceObject` objekt hostovaného ovládacího prvku.|
|[COleControlSite::m_pObject](#m_pobject)|Ukazatel na `IOleObjectInterface` rozhraní ovládacího prvku.|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Ukazatel na `IOleInPlaceObjectWindowless` rozhraní ovládacího prvku.|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Ukazatel na objekt okna pro hostovaný ovládací prvek.|
|[COleControlSite::m_rect](#m_rect)|Rozměry řídicího webu.|

## <a name="remarks"></a>Poznámky

Tato podpora je hlavním prostředkem, kdy integrovaný ovládací prvek ActiveX získává informace o umístění a rozsahu jeho zobrazovaného webu, jeho monikeru, jeho uživatelského rozhraní, jeho okolí vlastností a dalších prostředcích poskytovaných kontejnerem. `COleControlSite`plně implementuje rozhraní [IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite), [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite), [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), `IBoundObjectSite`, `INotifyDBEvents`, [IRowsetNotify](../../data/oledb/irowsetnotifyimpl-class.md) . Kromě toho je implementováno také rozhraní IDispatch (poskytování podpory pro ambientní vlastnosti a jímky událostí).

Chcete-li vytvořit web ovládacího prvku `COleControlSite`ActiveX pomocí, odvodit `COleControlSite`třídu z. V odvozené třídě kontejneru (například v dialogovém okně) `CWnd::CreateControlSite` přepište funkci. `CWnd`

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxocc. h

##  <a name="binddefaultproperty"></a>COleControlSite::BindDefaultProperty

Vytvoří vazbu výchozí vlastnosti jednoduché vázaného objektu volání, která je označena v knihovně typů, k základnímu kurzoru, který je definován vlastnostmi DataSource, UserName, Password a SQL ovládacího prvku zdroje dat.

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje DISPID vlastnosti ovládacího prvku vázaného na data, který má být svázán s ovládacím prvkem zdroje dat.

*vtProp*<br/>
Určuje typ vlastnosti, která má být svázána, například VT_BSTR, VT_VARIANT a tak dále.

*szFieldName*<br/>
Určuje název sloupce v kurzoru, který poskytuje ovládací prvek zdroje dat, na který bude tato vlastnost vázaná.

*pDSCWnd*<br/>
Ukazatel na `CWnd`objekt odvozený od zdroje dat, který je hostitelem ovládacího prvku zdroje dat, na který bude vlastnost svázána.

### <a name="remarks"></a>Poznámky

`CWnd` Objekt, na kterém zavoláte tuto funkci, musí být ovládací prvek vázaný na data.

##  <a name="bindproperty"></a>COleControlSite::BindProperty

Váže vlastnost jednoduchého vázaného objektu, jak je označena v knihovně typů, k základnímu ukazateli, který je definován vlastnostmi DataSource, UserName, Password a SQL ovládacího prvku zdroje dat.

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>Parametry

*dwDispId*<br/>
Určuje DISPID vlastnosti ovládacího prvku vázaného na data, který má být svázán s ovládacím prvkem zdroje dat.

*pWndDSC*<br/>
Ukazatel na `CWnd`objekt odvozený od zdroje dat, který je hostitelem ovládacího prvku zdroje dat, na který bude vlastnost svázána.

### <a name="remarks"></a>Poznámky

`CWnd` Objekt, na kterém zavoláte tuto funkci, musí být ovládací prvek vázaný na data.

##  <a name="colecontrolsite"></a>COleControlSite::COleControlSite

Vytvoří nový `COleControlSite` objekt.

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parametry

*pCtrlCont*<br/>
Ukazatel na kontejner ovládacího prvku (který představuje okno, které je hostitelem ovládacího prvku AtiveX).

### <a name="remarks"></a>Poznámky

Tato funkce je volána funkcí [COccManager:: CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) . Další informace o přizpůsobení vytváření kontejnerů naleznete v tématu [COccManager:: CreateSite](../../mfc/reference/coccmanager-class.md#createsite).

##  <a name="createcontrol"></a>COleControlSite::CreateControl

Vytvoří ovládací prvek ActiveX, který je hostovaný `COleControlSite` objektem.

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
Ukazatel na objekt okna reprezentující ovládací prvek.

*CLSID*<br/>
Jedinečné ID třídy ovládacího prvku

*lpszWindowName*<br/>
Ukazatel na text, který má být zobrazen v ovládacím prvku. Nastaví hodnotu vlastnosti Caption nebo text winodw (pokud existuje).

*dwStyle*<br/>
Styly Windows. Dostupné styly jsou uvedeny v části **poznámky** .

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku. Může to být buď `CRect` objekt, `RECT` nebo struktura.

*nID*<br/>
Určuje ID podřízeného okna ovládacího prvku.

*pPersist*<br/>
Ukazatel na `CFile` obsahující trvalý stav ovládacího prvku. Výchozí hodnota je NULL, což značí, že se ovládací prvek inicializuje sám bez obnovení jeho stavu z jakéhokoli trvalého úložiště. Pokud hodnota není null, mělo by se jednat o ukazatel `CFile`na objekt odvozený od ovládacího prvku, který obsahuje trvalá data ovládacího prvku, a to ve formě datového proudu nebo úložiště. Tato data mohla být uložena v předchozí aktivaci klienta. Může obsahovat další data, ale musí mít ukazatel pro čtení i zápis nastavený na první bajt trvalých dat v době `CreateControl`volání. `CFile`

*bStorage*<br/>
Určuje, zda mají být data v *pPersist* interpretována `IStorage` jako `IStream` data. Pokud jsou data v *pPersist* úložiště, *bStorage* by měla být true. Pokud jsou data v *pPersist* datový proud, *bStorage* by měl mít hodnotu false. Výchozí hodnota je FALSE (NEPRAVDA).

*bstrLicKey*<br/>
Volitelná data licenčního klíče. Tato data jsou potřebná jenom pro vytváření ovládacích prvků, které vyžadují licenční klíč za běhu. Pokud ovládací prvek podporuje licencování, je nutné zadat licenční klíč pro vytvoření ovládacího prvku, který má být úspěšný. Výchozí hodnota je NULL.

*ppt*<br/>
Ukazatel na `POINT` strukturu, která obsahuje levý horní roh ovládacího prvku. Velikost ovládacího prvku je určena hodnotou *psize*. Hodnoty *PPT* a *psize* jsou volitelnou metodou určení velikosti a umístění OPF ovládacího prvku.

*psize*<br/>
Ukazatel na `SIZE` strukturu, která obsahuje velikost ovládacího prvku. Levý horní roh je určen hodnotou *PPT*. Hodnoty *PPT* a *psize* jsou volitelnou metodou určení velikosti a umístění OPF ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

V`CreateControl`systému je podporována pouze podmnožina příznaků Windows *dwStyle* :

- WS_VISIBLE vytvoří okno, které je zpočátku viditelné. Vyžaduje se, pokud chcete, aby byl ovládací prvek viditelný hned, například v běžných oknech.

- WS_DISABLED vytvoří okno, které je zpočátku zakázané. Zakázané okno nemůže přijmout vstup od uživatele. Lze nastavit, pokud má ovládací prvek vlastnost Enabled.

- WS_BORDER vytvoří okno s ohraničením tenké čáry. Lze nastavit, pokud má ovládací prvek vlastnost BorderStyle.

- WS_GROUP Určuje první ovládací prvek skupiny ovládacích prvků. Uživatel může změnit fokus klávesnice z jednoho ovládacího prvku ve skupině na další pomocí směrových kláves. Všechny ovládací prvky definované pomocí stylu WS_GROUP po prvním ovládacím prvku patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP ukončí skupinu a spustí další skupinu.

- WS_TABSTOP určuje ovládací prvek, který může obdržet fokus klávesnice, když uživatel stiskne klávesu TAB. Stisknutí klávesy TAB změní fokus klávesnice na další ovládací prvek WS_TABSTOP stylu.

Pomocí druhého přetížení vytvořte ovládací prvky výchozí velikosti.

##  <a name="destroycontrol"></a>COleControlSite::D estroyControl

`COleControlSite` Odstraní objekt.

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak 0.

### <a name="remarks"></a>Poznámky

Po dokončení je objekt uvolněn z paměti a všechny ukazatele na tento objekt již nejsou platné.

##  <a name="doverb"></a>  COleControlSite::DoVerb

Provede zadanou operaci.

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>Parametry

*nVerb*<br/>
Určuje operaci, která má být provedena. Může zahrnovat jednu z následujících možností:

|Value|Význam|Písmeno|
|-----------|-------------|------------|
|0|primární požadavek|OLEIVERB_PRIMARY|
|-1|Sekundární příkaz|NTato|
|1|Zobrazí objekt pro úpravy.|OLEIVERB_SHOW|
|-2|Upraví položku v samostatném okně.|OLEIVERB_OPEN|
|-3|Skryje objekt.|OLEIVERB_HIDE|
|-4|Aktivuje ovládací prvek místně.|OLEIVERB_UIACTIVATE|
|-5|Aktivuje ovládací prvek místně bez dalších prvků uživatelského rozhraní.|OLEIVERB_INPLACEACTIVATE|
|-7|Zobrazí vlastnosti ovládacího prvku.|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
Ukazatel na zprávu, která způsobila aktivaci položky.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce přímo volá `IOleObject` rozhraní ovládacího prvku a spustí určenou operaci. Pokud je vyvolána výjimka jako výsledek tohoto volání funkce, vrátí se kód chyby HRESULT.

Další informace najdete v tématu [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v Windows SDK.

##  <a name="enabledsc"></a>COleControlSite::EnableDSC

Povoluje pro lokalitu ovládacího prvku datový původ.

```
virtual void EnableDSC();
```

### <a name="remarks"></a>Poznámky

Volá se rozhraním, aby se povolil a inicializoval původ dat pro řídicí lokalitu. Přepsáním této funkce zajistíte vlastní chování.

##  <a name="enablewindow"></a>COleControlSite::EnableWindow

Povolí nebo zakáže vstup myší a klávesnicí do webu ovládacího prvku.

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, jestli se má povolit nebo zakázat okno: TRUE, pokud je povoleno zadání okna, jinak FALSE.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo okno dříve zakázáno, jinak 0.

##  <a name="freezeevents"></a>COleControlSite:: Freezeevents.

Určuje, zda bude web ovládacího prvku zpracovávat nebo ignorovat události vyvolané ovládacím prvkem.

```
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bFreeze*<br/>
Určuje, zda web ovládacího prvku chce zastavit přijímání událostí. Nenulové, pokud ovládací prvek nepřijímá události; jinak nula.

### <a name="remarks"></a>Poznámky

Pokud má *bFreeze* hodnotu true, řídicí lokalita požádá ovládací prvek o zastavení událostí olemování. Pokud je *BFREEZE* false, řídicí lokalita požádá ovládací prvek, aby pokračoval v Vyvolávání událostí.

> [!NOTE]
>  Ovládací prvek není požadován k zastavení vypálení událostí, pokud je požadováno webovým serverem ovládacího prvku. Může pokračovat v napálení, ale všechny následné události bude lokalita ovládacího prvku ignorovat.

##  <a name="getcontrolinfo"></a>COleControlSite::GetControlInfo

Načte informace o ovládacích symbolech klávesnice a chování klávesnice ovládacího prvku.

```
void GetControlInfo();
```

### <a name="remarks"></a>Poznámky

Informace jsou uloženy v [COleControlSite:: m_ctlInfo](#m_ctlinfo).

##  <a name="getdefbtncode"></a>COleControlSite::GetDefBtnCode

Určuje, zda je ovládací prvek výchozím tlačítkem pro vložení.

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>Návratová hodnota

Může to být jedna z následujících hodnot:

- Ovládací prvek DLGC_DEFPUSHBUTTON je výchozí tlačítko v dialogovém okně.

- Ovládací prvek DLGC_UNDEFPUSHBUTTON není výchozím tlačítkem v dialogovém okně.

- **0** ovládací prvek není tlačítko.

##  <a name="getdlgctrlid"></a>COleControlSite::GetDlgCtrlID

Načte identifikátor ovládacího prvku.

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor položky dialogového okna ovládacího prvku

##  <a name="geteventiid"></a>COleControlSite::GetEventIID

Načte ukazatel na výchozí rozhraní události ovládacího prvku.

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>Parametry

*piid*<br/>
Ukazatel na ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak 0. V případě úspěchu obsahuje *PIID* ID rozhraní pro výchozí rozhraní události ovládacího prvku.

##  <a name="getexstyle"></a>COleControlSite::GetExStyle

Načte rozšířené styly okna.

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Rozšířené styly okna ovládacího prvku.

### <a name="remarks"></a>Poznámky

Chcete-li načíst běžné styly, zavolejte [COleControlSite:: GetStyle](#getstyle).

##  <a name="getproperty"></a>COleControlSite:: GetProperty

Získá vlastnost ovládacího prvku určenou parametrem *dwDispID*.

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje ID odeslání vlastnosti, které se nachází ve výchozím `IDispatch` rozhraní ovládacího prvku, které se má načíst.

*vtProp*<br/>
Určuje typ vlastnosti, která má být načtena. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvProp*<br/>
Adresa proměnné, která bude přijímat hodnotu vlastnosti. Musí odpovídat typu zadanému parametrem *vtProp*.

### <a name="remarks"></a>Poznámky

Hodnota je vrácena prostřednictvím *pvProp*.

##  <a name="getstyle"></a>COleControlSite:: GetStyle

Načte styly webu ovládacího prvku.

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Styly okna.

### <a name="remarks"></a>Poznámky

Seznam možných hodnot naleznete v tématu [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles). Chcete-li načíst rozšířené styly webu ovládacího prvku, zavolejte [COleControlSite:: GetExStyle](#getexstyle).

##  <a name="getwindowtext"></a>COleControlSite::GetWindowText

Načte aktuální text ovládacího prvku.

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na `CString` objekt, který obsahuje aktuální text ovládacího prvku.

### <a name="remarks"></a>Poznámky

Pokud ovládací prvek podporuje skladovou vlastnost Caption, je tato hodnota vrácena. Pokud není vlastnost Caption titulku podporovaná, vrátí se hodnota vlastnosti text.

##  <a name="invokehelper"></a>COleControlSite:: InvokeHelper

Vyvolá metodu nebo vlastnost určenou v *dwDispID*v kontextu určeném parametrem *wFlags*.

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
Určuje ID odeslání vlastnosti nebo metody, která je nalezena v `IDispatch` rozhraní ovládacího prvku, který má být vyvolán.

*wFlags*<br/>
Příznaky popisující kontext volání metody IDispatch:: Invoke. Možné hodnoty *wFlags* naleznete v části `IDispatch::Invoke` v Windows SDK.

*vtRet*<br/>
Určuje typ vrácené hodnoty. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Adresa proměnné, která bude přijímat hodnotu vlastnosti nebo návratovou hodnotu. Musí odpovídat typu zadanému parametrem *vtRet*.

*pbParamInfo*<br/>
Ukazatel na řetězec zakončený hodnotou NULL bajtů, který určuje typy parametrů následující po *pbParamInfo*. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Seznam proměnných parametrů typu určených v *pbParamInfo*.

### <a name="remarks"></a>Poznámky

Parametr *pbParamInfo* určuje typy parametrů předaných metodě nebo vlastnosti. Seznam proměnných argumentů je reprezentován... v deklaraci syntaxe.

Tato funkce převede parametry na hodnoty VARIANTARG a poté vyvolá `IDispatch::Invoke` metodu na ovládacím prvku. Pokud volání `IDispatch::Invoke` selže, tato funkce vyvolá výjimku. Pokud `IDispatch::Invoke` je `DISP_E_EXCEPTION`stavový kód vrácený funkcí `COleDispatchException` , tato funkce vyvolá objekt, jinak vyvolá `COleException`.

##  <a name="invokehelperv"></a>COleControlSite::InvokeHelperV

Vyvolá metodu nebo vlastnost určenou v *dwDispID*v kontextu určeném parametrem *wFlags*.

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
Určuje ID odeslání vlastnosti nebo metody, která je nalezena v `IDispatch` rozhraní ovládacího prvku, který má být vyvolán.

*wFlags*<br/>
Příznaky popisující kontext volání metody IDispatch:: Invoke.

*vtRet*<br/>
Určuje typ vrácené hodnoty. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Adresa proměnné, která bude přijímat hodnotu vlastnosti nebo návratovou hodnotu. Musí odpovídat typu zadanému parametrem *vtRet*.

*pbParamInfo*<br/>
Ukazatel na řetězec zakončený hodnotou NULL bajtů, který určuje typy parametrů následující po *pbParamInfo*. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argList*<br/>
Ukazatel na seznam argumentů proměnné.

### <a name="remarks"></a>Poznámky

Parametr *pbParamInfo* určuje typy parametrů předaných metodě nebo vlastnosti. Další parametry pro vyvolanou metodu nebo vlastnost lze předat pomocí parametru *va_list* .

Obvykle je tato funkce volána nástrojem `COleControlSite::InvokeHelper`.

##  <a name="isdefaultbutton"></a>COleControlSite::IsDefaultButton

Určuje, zda je ovládací prvek výchozím tlačítkem.

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je ovládací prvek výchozím tlačítkem v okně, jinak nula.

##  <a name="iswindowenabled"></a>COleControlSite::IsWindowEnabled

Určuje, zda je povolen web ovládacího prvku.

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je ovládací prvek povolený, jinak nula.

### <a name="remarks"></a>Poznámky

Hodnota je načtena z vlastnosti akcií s povoleným ovládacím prvkem.

##  <a name="m_biswindowless"></a>COleControlSite::m_bIsWindowless

Určuje, zda je objekt ovládacím prvkem bez okna.

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>Poznámky

Nenulové, pokud ovládací prvek nemá žádné okno, jinak nula.

##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo

Informace o tom, jak je vstup z klávesnice zpracováván ovládacím prvkem.

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>Poznámky

Tyto informace jsou uloženy ve struktuře [CONTROLINFO](/windows/win32/api/ocidl/ns-ocidl-controlinfo) .

##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink

Obsahuje soubor cookie bodu připojení z jímky událostí ovládacího prvku.

```
DWORD m_dwEventSink;
```

##  <a name="m_dwmiscstatus"></a>COleControlSite::m_dwMiscStatus

Obsahuje různé informace o ovládacím prvku.

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)v Windows SDK.

##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink

Obsahuje soubor cookie [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

```
DWORD m_dwPropNotifySink;
```

##  <a name="m_dwstyle"></a>COleControlSite::m_dwStyle

Obsahuje styly oken ovládacího prvku.

```
DWORD m_dwStyle;
```

##  <a name="m_hwnd"></a>COleControlSite::m_hWnd

Obsahuje HWND ovládacího prvku nebo NULL, pokud ovládací prvek není bez okna.

```
HWND m_hWnd;
```

##  <a name="m_iidevents"></a>COleControlSite::m_iidEvents

Obsahuje ID rozhraní výchozího rozhraní jímky událostí ovládacího prvku.

```
IID m_iidEvents;
```

##  <a name="m_nid"></a>COleControlSite::m_nID

Obsahuje ID položky dialogového okna ovládacího prvku.

```
UINT m_nID;
```

##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject

Obsahuje rozhraní [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) ovládacího prvku.

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont

Obsahuje kontejner ovládacího prvku (reprezentující formulář).

```
COleControlContainer* m_pCtrlCont;
```

##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject

Obsahuje rozhraní IOleInPlaceObject ovládacího prvku. [](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) `IOleInPlaceObject`

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

##  <a name="m_pobject"></a>  COleControlSite::m_pObject

`IOleObjectInterface` Obsahuje rozhraní ovládacího prvku.

```
LPOLEOBJECT m_pObject;
```

##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject

Obsahuje rozhraní IOleInPlaceObjectWindowless ovládacího prvku. [](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) `IOleInPlaceObjectWindowless`

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

##  <a name="m_pwndctrl"></a>COleControlSite::m_pWndCtrl

Obsahuje ukazatel na `CWnd` objekt, který reprezentuje samotný ovládací prvek.

```
CWnd* m_pWndCtrl;
```

##  <a name="m_rect"></a>COleControlSite::m_rect

Obsahuje meze ovládacího prvku vzhledem k oknu kontejneru.

```
CRect m_rect;
```

##  <a name="modifystyle"></a>COleControlSite::ModifyStyle

Upraví styly ovládacího prvku.

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*dwRemove*<br/>
Styly, které mají být odebrány z aktuálního stylu okna.

*dwAdd*<br/>
Styly, které mají být přidány z aktuálního stylu okna.

*nFlags*<br/>
Příznaky umístění okna. Seznam možných hodnot naleznete v tématu funkce [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se změní styly, jinak nula.

### <a name="remarks"></a>Poznámky

Vlastnost s povolenými zásobami ovládacího prvku se upraví tak, aby odpovídala nastavení pro WS_DISABLED. Vlastnost stylu burzovního ohraničení ovládacího prvku se upraví tak, aby odpovídala požadovanému nastavení pro WS_BORDER. Všechny ostatní styly jsou použity přímo v popisovači okna ovládacího prvku, pokud je k dispozici.

Upraví styly oken ovládacího prvku. Styly, které mají být přidány nebo odebrány, lze kombinovat pomocí operátoru OR &#124; (). Informace o dostupných stylech oken najdete v Windows SDK funkce [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) .

Pokud *nFlags* není nula, `ModifyStyle` volá funkci `SetWindowPos`Win32 a znovu vykreslí okno kombinací *nFlags* s následujícími čtyřmi příznaky:

- SWP_NOSIZE zachová aktuální velikost.

- SWP_NOMOVE zachová aktuální pozici.

- SWP_NOZORDER zachová aktuální pořadí Z.

- SWP_NOACTIVATE neaktivuje okno.

Chcete-li upravit rozšířené styly okna, zavolejte [ModifyStyleEx](#modifystyleex).

##  <a name="modifystyleex"></a>COleControlSite::ModifyStyleEx

Upraví rozšířené styly ovládacího prvku.

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*dwRemove*<br/>
Rozšířené styly, které mají být odebrány z aktuálního stylu okna.

*dwAdd*<br/>
Rozšířené styly, které mají být přidány z aktuálního stylu okna.

*nFlags*<br/>
Příznaky umístění okna. Seznam možných hodnot naleznete v tématu funkce [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se změní styly, jinak nula.

### <a name="remarks"></a>Poznámky

Vlastnost vzhledu akcie ovládacího prvku se upraví tak, aby odpovídala nastavení pro WS_EX_CLIENTEDGE. Všechny ostatní styly rozšířeného okna jsou aplikovány přímo na popisovač okna ovládacího prvku, pokud je k dispozici.

Změní rozšířené styly okna objektu ovládacího prvku. Styly, které mají být přidány nebo odebrány, lze kombinovat pomocí operátoru OR &#124; (). Další informace o dostupných stylech oken najdete v Windows SDK funkci [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) .

Pokud *nFlags* není nula, `ModifyStyleEx` volá funkci `SetWindowPos`Win32 a znovu vykreslí okno kombinací *nFlags* s následujícími čtyřmi příznaky:

- SWP_NOSIZE zachová aktuální velikost.

- SWP_NOMOVE zachová aktuální pozici.

- SWP_NOZORDER zachová aktuální pořadí Z.

- SWP_NOACTIVATE neaktivuje okno.

Chcete-li upravit rozšířené styly okna, zavolejte [ModifyStyle](#modifystyle).

##  <a name="movewindow"></a>COleControlSite::MoveWindow

Změní pozici ovládacího prvku.

```
virtual void MoveWindow(
    int x,
    int y,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Nová pozice levé strany okna

*y*<br/>
Nová pozice horní části okna.

*nWidth*<br/>
Nová šířka okna

*nHeight*<br/>
Nová výška okna

##  <a name="quickactivate"></a>COleControlSite::QuickActivate

Rychle aktivuje obsažený ovládací prvek.

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla lokalita ovládacího prvku aktivována, jinak nula.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána pouze v případě, že uživatel Přepisuje proces vytvoření ovládacího prvku.

Metody `IPersist*::Load` a`IPersist*::InitNew` by měly být volány poté, co dojde k rychlé aktivaci. Ovládací prvek by měl během rychlé aktivace vytvořit připojení ke jímka kontejneru. Tato připojení jsou ale neživá, dokud `IPersist*::Load` nebo `IPersist*::InitNew` nebudou volána.

##  <a name="safesetproperty"></a>COleControlSite::SafeSetProperty

Nastaví vlastnost ovládacího prvku určenou parametrem *dwDispID*.

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje ID odeslání vlastnosti nebo metody, která se nachází v `IDispatch` rozhraní ovládacího prvku, které má být nastaveno.

*vtProp*<br/>
Určuje typ vlastnosti, která se má nastavit. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Jeden parametr typu určený parametrem *vtProp*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Na rozdíl `SetProperty` od `SetPropertyV`a, pokud dojde k chybě (například pokus o nastavení neexistující vlastnosti), není vyvolána žádná výjimka.

##  <a name="setdefaultbutton"></a>COleControlSite::SetDefaultButton

Nastaví ovládací prvek jako výchozí tlačítko.

```
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*bDefault*<br/>
Nenulové, pokud by se měl ovládací prvek stát výchozím tlačítkem; jinak nula.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Ovládací prvek musí mít nastaven bit stavu OLEMISC_ACTSLIKEBUTTON.

##  <a name="setdlgctrlid"></a>COleControlSite::SetDlgCtrlID

Změní hodnotu identifikátoru položky dialogového okna ovládacího prvku.

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Nová hodnota identifikátoru.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu předchozí identifikátor položky dialogového okna tohoto okna; v opačném případě 0.

### <a name="remarks"></a>Poznámky

##  <a name="setfocus"></a>COleControlSite:: SetFocus

Nastaví fokus na ovládací prvek.

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>Parametry

*lpmsg*<br/>
Ukazatel na [strukturu zprávy](/windows/win32/api/winuser/ns-winuser-msg). Tato struktura obsahuje zprávu Windows, která aktivuje `SetFocus` požadavek na ovládací prvek obsažený v aktuálním řídicím webu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno, které dříve mělo fokus.

##  <a name="setproperty"></a>COleControlSite:: SetProperty

Nastaví vlastnost ovládacího prvku určenou parametrem *dwDispID*.

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje ID odeslání vlastnosti nebo metody, která se nachází v `IDispatch` rozhraní ovládacího prvku, které má být nastaveno.

*vtProp*<br/>
Určuje typ vlastnosti, která se má nastavit. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Jeden parametr typu určený parametrem *vtProp*.

### <a name="remarks"></a>Poznámky

Pokud `SetProperty` dojde k chybě, je vyvolána výjimka.

Typ výjimky je určen návratovou hodnotou pokusu o nastavení vlastnosti nebo metody. Pokud je `DISP_E_EXCEPTION`vrácená hodnota, `COleException`je vyvolána `COleDispatchExcpetion` , a v opačném případě.

##  <a name="setpropertyv"></a>COleControlSite::SetPropertyV

Nastaví vlastnost ovládacího prvku určenou parametrem *dwDispID*.

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje ID odeslání vlastnosti nebo metody, která se nachází v `IDispatch` rozhraní ovládacího prvku, které má být nastaveno.

*vtProp*<br/>
Určuje typ vlastnosti, která se má nastavit. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argList*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Další parametry pro vyvolanou metodu nebo vlastnost lze passeed pomocí parametru *arg_list* . Pokud `SetProperty` dojde k chybě, je vyvolána výjimka.

Typ výjimky je určen návratovou hodnotou pokusu o nastavení vlastnosti nebo metody. Pokud je `DISP_E_EXCEPTION`vrácená hodnota, `COleException`je vyvolána `COleDispatchExcpetion` , a v opačném případě.

##  <a name="setwindowpos"></a>COleControlSite::SetWindowPos

Nastaví velikost, umístění a pořadí Z lokality ovládacího prvku.

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

*pWndInsertAfter*<br/>
Ukazatel na okno.

*x*<br/>
Nová pozice levé strany okna

*y*<br/>
Nová pozice horní části okna.

*cx*<br/>
Nová šířka okna

*kr*<br/>
Nová výška okna

*nFlags*<br/>
Určuje velikost okna a příznaky pro umístění. Možné hodnoty naleznete v části poznámky pro [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak nula.

##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText

Nastaví text pro řídicí lokalitu.

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
Ukazatel na řetězec zakončený hodnotou null, který bude použit jako nový název nebo text ovládacího prvku.

### <a name="remarks"></a>Poznámky

Tato funkce se nejdřív pokusí nastavit vlastnost titulku. Pokud není vlastnost text titulku podporovaná, je místo toho nastavena vlastnost text.

##  <a name="showwindow"></a>COleControlSite::: ShowWindow

Nastaví stav zobrazení okna.

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parametry

*nCmdShow*<br/>
Určuje způsob zobrazení lokality ovládacího prvku. Musí to být jedna z následujících hodnot:

- SW_HIDE skrývá toto okno a předá aktivaci do jiného okna.

- SW_MINIMIZE minimalizuje okno a aktivuje okno nejvyšší úrovně v seznamu systému.

- SW_RESTORE aktivuje a zobrazuje okno. Pokud je okno minimalizované nebo maximalizované, Windows ho obnoví do původní velikosti a pozice.

- SW_SHOW aktivuje okno a zobrazí ho v aktuální velikosti a pozici.

- SW_SHOWMAXIMIZED aktivuje okno a zobrazí ho jako maximalizované okno.

- SW_SHOWMINIMIZED aktivuje okno a zobrazí ho jako ikonu.

- SW_SHOWMINNOACTIVE zobrazí okno jako ikonu. Okno, které je aktuálně aktivní, zůstává aktivní.

- SW_SHOWNA zobrazí okno v aktuálním stavu. Okno, které je aktuálně aktivní, zůstává aktivní.

- SW_SHOWNOACTIVATE zobrazí okno v jeho poslední velikosti a umístění. Okno, které je aktuálně aktivní, zůstává aktivní.

- SW_SHOWNORMAL aktivuje a zobrazí okno. Pokud je okno minimalizované nebo maximalizované, Windows ho obnoví do původní velikosti a pozice.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo okno dříve viditelné; 0, pokud bylo okno dříve skryto.

## <a name="see-also"></a>Viz také:

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer – třída](../../mfc/reference/colecontrolcontainer-class.md)
