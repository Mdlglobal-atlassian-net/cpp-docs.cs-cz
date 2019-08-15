---
title: CDHtmlDialog – třída
ms.date: 03/27/2019
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: ec424e433dc84bf4188e349eb6450888aeeeb463
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506902"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog – třída

Slouží k vytváření dialogových oken, která používají jazyk HTML místo prostředků dialogu k implementaci jejich uživatelského rozhraní.

## <a name="syntax"></a>Syntaxe

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|Vytvoří objekt CDHtmlDialog.|
|[CDHtmlDialog::~CDHtmlDialog](#_dtorcdhtmldialog)|Odstraní objekt CDHtmlDialog.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Overridable, která je volána jako kontrola přístupu, chcete-li zjistit, zda objekty skriptování na načtené stránce mají přístup k externímu odeslání lokality ovládacího prvku. Kontroluje, zda je odesílání buď bezpečné pro skriptování, nebo současná zóna umožňuje objektům, které nejsou bezpečné pro skriptování.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Přepsatelné slouží k vytvoření instance řídicího webu pro hostování ovládacího prvku WebBrowser v dialogovém okně.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Vyměňuje data mezi členskou proměnnou a hodnotou vlastnosti ovládacího prvku ActiveX na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Vyměňuje data mezi členskou proměnnou a zaškrtávacím políčkem na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|Vyměňuje data mezi členskou proměnnou a libovolnou vlastností elementu HTML na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|Vyměňuje data mezi členskou proměnnou a přepínačem na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Získá nebo nastaví index pole seznamu na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|Získá nebo nastaví zobrazovaný text položky seznamu (na základě aktuálního indexu) na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Získá nebo nastaví hodnotu položky seznamu (na základě aktuálního indexu) na stránce HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Odstraní nemodální dialogové okno.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Umožňuje používat nemodální dialogová okna.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Umožňuje dialogovému oknu filtrovat datové objekty schránky vytvořené hostovaným prohlížečem.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|`IDispatch` Načte rozhraní ovládacího prvku ActiveX vloženého v dokumentu HTML.|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|Načte požadovanou vlastnost zadaného ovládacího prvku ActiveX.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Načte adresu URL (Uniform Resource Locator), která je přidružená k aktuálnímu dokumentu.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Načte rozhraní IHTMLDocument2 v aktuálně načteném dokumentu HTML.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Volá se ovládacím prvkem obsaženým v ovládacím prvku WebBrowser, když se používá jako cíl přetažení, aby dialog mohl poskytovat alternativní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[CDHtmlDialog::GetElement](#getelement)|Načte rozhraní elementu HTML.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|`innerHTML` Načte vlastnost elementu HTML.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Načte požadovaný ukazatel rozhraní z elementu HTML.|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|Načte hodnotu vlastnosti elementu HTML.|
|[CDHtmlDialog::GetElementText](#getelementtext)|`innerText` Načte vlastnost elementu HTML.|
|[CDHtmlDialog::GetEvent](#getevent)|`IHTMLEventObj` Získá ukazatel na aktuální objekt události.|
|[CDHtmlDialog::GetExternal](#getexternal)|Získá `IDispatch` rozhraní hostitele.|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Načte možnosti uživatelského rozhraní hostitele.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Načte klíč registru, ve kterém jsou uložené předvolby uživatele.|
|[CDHtmlDialog::HideUI](#hideui)|Skryje uživatelské rozhraní hostitele.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Označuje, zda je `IDispatch` rozhraní hostitele bezpečné pro skriptování.|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|Načte zadaný prostředek do ovládacího prvku WebBrowser.|
|[CDHtmlDialog::Navigate](#navigate)|Přejde na zadanou adresu URL.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Volá se rozhraním, než se aktivuje událost navigace.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Volá se rozhraním, aby se aplikace upozornila na to, že dokument dosáhl stavu READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Volá se rozhraním, když se aktivuje nebo deaktivuje okno dokumentu.|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Volá se v reakci na zprávu WM_INITDIALOG.|
|[CDHtmlDialog:: OnNavigateComplete](#onnavigatecomplete)|Volá se rozhraním po dokončení události navigace.|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|Upozorní objekt, že potřebuje změnit velikost prostoru ohraničení.|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|Nastaví vlastnost ovládacího prvku ActiveX na novou hodnotu.|
|[CDHtmlDialog:: SetElementHtml](#setelementhtml)|`innerHTML` Nastaví vlastnost elementu HTML.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Nastaví vlastnost elementu HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|`innerText` Nastaví vlastnost elementu HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Nastaví `IDispatch` rozhraní hostitele.|
|[CDHtmlDialog:: SetHostFlags](#sethostflags)|Nastaví příznaky uživatelského rozhraní hostitele.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Volá se, když se zobrazí místní nabídka.|
|[CDHtmlDialog::ShowUI](#showui)|Zobrazuje uživatelské rozhraní hostitele.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Volá se, aby se zprávy klíče akcelerátoru v nabídce procesu.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Volá se, aby se změnila adresa URL, která se má načíst.|
|[CDHtmlDialog::UpdateUI](#updateui)|Volá se, aby se hostiteli informovalo, že se změnil stav příkazu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Označuje, zda se má jako titulek k dialogovému oknu použít název dokumentu HTML.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|ID prostředku prostředku HTML, který se má zobrazit|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Ukazatel na aplikaci webového prohlížeče.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Ukazatel na dokument HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|Aktuální adresa URL.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Verze řetězce ID prostředku HTML.|

## <a name="remarks"></a>Poznámky

`CDHtmlDialog`může načíst kód HTML, který se bude zobrazovat buď z prostředku HTML, nebo z adresy URL.

`CDHtmlDialog`může také provádět výměnu dat s ovládacími prvky HTML a zpracovávat události z ovládacích prvků HTML, například kliknutím na tlačítko.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>Požadavky

**Header:** afxdhtml.h

##  <a name="ddx_dhtml_helper_macros"></a>Makra pomocníka DDX_DHtml

Pomocná makra DDX_DHtml umožňují snadný přístup k běžně používaným vlastnostem ovládacích prvků na stránce HTML.

### <a name="data-exchange-macros"></a>Makra výměny dat

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Nastaví nebo načte vlastnost Value z vybraného ovládacího prvku.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Nastaví nebo načte text mezi počátečními a koncovými značkami aktuálního prvku.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Nastaví nebo načte kód HTML mezi počátečními a koncovými značkami aktuálního prvku.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Nastaví nebo načte cílovou adresu URL nebo kotvicí bod.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Nastaví nebo načte cílové okno nebo rámec.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Nastaví nebo načte název obrázku nebo videoklipu v dokumentu.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Nastaví nebo načte adresu URL přidruženého rámce.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Nastaví nebo načte adresu URL přidruženého rámce.|

##  <a name="canaccessexternal"></a>  CDHtmlDialog::CanAccessExternal

Overridable, která je volána jako kontrola přístupu, chcete-li zjistit, zda objekty skriptování na načtené stránce mají přístup k externímu odeslání lokality ovládacího prvku. Kontroluje, zda je odesílání buď bezpečné pro skriptování, nebo současná zóna umožňuje objektům, které nejsou bezpečné pro skriptování.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="cdhtmldialog"></a>CDHtmlDialog:: CDHtmlDialog

Vytvoří dialogové okno dynamického HTML založeného na prostředku.

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Řetězec zakončený hodnotou null, který je názvem prostředku šablony dialogového okna.

*szHtmlResID*<br/>
Řetězec zakončený hodnotou null, který je názvem prostředku HTML.

*pParentWnd*<br/>
Ukazatel na objekt okna nadřazeného objektu nebo vlastníka (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke kterému patří objekt dialogu. Pokud má hodnotu NULL, je nadřazené okno objektu dialogového okna nastaveno na hlavní okno aplikace.

*nIDTemplate*<br/>
Obsahuje číslo ID prostředku šablony dialogového okna.

*nHtmlResID*<br/>
Obsahuje číslo ID prostředku HTML.

### <a name="remarks"></a>Poznámky

Druhá forma konstruktoru poskytuje přístup k prostředku dialogového okna prostřednictvím názvu šablony. Třetí forma konstruktoru poskytuje přístup k prostředku dialogového okna prostřednictvím ID šablony prostředků. ID začíná obvykle předponou **IDD_** .

##  <a name="_dtorcdhtmldialog"></a>CDHtmlDialog:: ~ CDHtmlDialog

Odstraní objekt CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Poznámky

Členské funkce [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow) je nutné použít ke zničení nemodálních dialogových oken, které jsou vytvořeny pomocí funkce [CDialog:: Create](../../mfc/reference/cdialog-class.md#create).

##  <a name="createcontrolsite"></a>CDHtmlDialog:: CreateControlSite

Přepsatelné slouží k vytvoření instance řídicího webu pro hostování ovládacího prvku WebBrowser v dialogovém okně.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parametry

*pContainer*<br/>
Ukazatel na objekt [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)

*ppSite*<br/>
Ukazatel na ukazatel na [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci můžete přepsat tak, aby vracela instanci třídy webu vlastního ovládacího prvku.

##  <a name="ddx_dhtml_axcontrol"></a>  CDHtmlDialog::DDX_DHtml_AxControl

Vyměňuje data mezi členskou proměnnou a hodnotou vlastnosti ovládacího prvku ActiveX na stránce HTML.

```
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*szId*<br/>
Hodnota parametru ID značky objektu ve zdroji HTML pro ovládací prvek ActiveX.

*dispId*<br/>
ID odeslání vlastnosti, se kterou chcete vyměňovat data.

*szPropName*<br/>
Název vlastnosti

*var*<br/>
Datový člen typu VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md)nebo [CComVariant](../../atl/reference/ccomvariant-class.md), který obsahuje hodnotu vyměňované vlastností ovládacího prvku ActiveX.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>  CDHtmlDialog::DDX_DHtml_CheckBox

Vyměňuje data mezi členskou proměnnou a zaškrtávacím políčkem na stránce HTML.

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která se má vyměňovat

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>  CDHtmlDialog::DDX_DHtml_ElementText

Vyměňuje data mezi členskou proměnnou a libovolnou vlastností elementu HTML na stránce HTML.

```
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*dispId*<br/>
ID odeslání elementu HTML, se kterým chcete vyměňovat data.

*value*<br/>
Hodnota, která se má vyměňovat

##  <a name="ddx_dhtml_radio"></a>  CDHtmlDialog::DDX_DHtml_Radio

Vyměňuje data mezi členskou proměnnou a přepínačem na stránce HTML.

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která se má vyměňovat

##  <a name="ddx_dhtml_selectindex"></a>CDHtmlDialog::D DX_DHtml_SelectIndex

Získá nebo nastaví index pole seznamu na stránce HTML.

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*szId*<br/>
Hodnota, kterou jste zadali pro `id` parametr ovládacího prvku HTML.

*value*<br/>
Hodnota, která se má vyměňovat

##  <a name="ddx_dhtml_selectstring"></a>CDHtmlDialog::D DX_DHtml_SelectString

Získá nebo nastaví zobrazovaný text položky seznamu (na základě aktuálního indexu) na stránce HTML.

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která se má vyměňovat

##  <a name="ddx_dhtml_selectvalue"></a>  CDHtmlDialog::DDX_DHtml_SelectValue

Získá nebo nastaví hodnotu položky seznamu (na základě aktuálního indexu) na stránce HTML.

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která se má vyměňovat

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>  CDHtmlDialog::DestroyModeless

Odpojí nemodální dialogové okno od `CDHtmlDialog` objektu a odstraní objekt.

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>CDHtmlDialog:: EnableModeless

Umožňuje používat nemodální dialogová okna.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parametry

*fEnable*<br/>
Viz *fEnable* v [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="filterdataobject"></a>CDHtmlDialog:: FilterDataObject

Umožňuje dialogovému oknu filtrovat datové objekty schránky vytvořené hostovaným prohlížečem.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parametry

*pDO*<br/>
Viz *CHOP* v [IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) v Windows SDK.

*ppDORet*<br/>
Viz *ppDORet* v `IDocHostUIHandler::FilterDataObject` tématu Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="getcontroldispatch"></a>CDHtmlDialog:: GetControlDispatch

Načte rozhraní v ovládacím prvku ActiveX vloženém do dokumentu HTML vráceného funkcí [GetDHtmlDocument.](#getdhtmldocument) `IDispatch`

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parametry

*szId*<br/>
ID HTML ovládacího prvku ActiveX.

*ppdisp*<br/>
`IDispatch` Rozhraní ovládacího prvku, pokud je nalezeno na webové stránce.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="getcontrolproperty"></a>CDHtmlDialog:: GetControlProperty

Načte požadovanou vlastnost zadaného ovládacího prvku ActiveX.

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>Parametry

*szId*<br/>
ID HTML ovládacího prvku ActiveX.

*szPropName*<br/>
Název vlastnosti ve výchozím národním prostředí aktuálního uživatele.

*pdispControl*<br/>
`IDispatch` Ukazatel ovládacího prvku ActiveX.

*dispId*<br/>
ID odeslání vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Varianta obsahující požadovanou vlastnost nebo prázdnou variantu v případě, že nebyl nalezen ovládací prvek nebo vlastnost.

### <a name="remarks"></a>Poznámky

Přetížení jsou v dolní části uvedená v horní části nejefektivnější.

##  <a name="getcurrenturl"></a>  CDHtmlDialog::GetCurrentUrl

Načte adresu URL (Uniform Resource Locator), která je přidružená k aktuálnímu dokumentu.

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parametry

*szUrl*<br/>
Objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující adresu URL, která má být načtena.

##  <a name="getdhtmldocument"></a>CDHtmlDialog:: GetDHtmlDocument

Načte rozhraní [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) v aktuálně načteném dokumentu HTML.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parametry

pphtmlDoc ukazatel na ukazatel na dokument HTML.  *\* \**

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. Vrátí S_OK, pokud bylo úspěšné.

##  <a name="getdroptarget"></a>CDHtmlDialog:: GetDropTarget

Volá se ovládacím prvkem obsaženým v ovládacím prvku WebBrowser, když se používá jako cíl přetažení, aby dialog mohl poskytovat alternativní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parametry

*pDropTarget*<br/>
Viz *pDropTarget* v [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) v Windows SDK.

*ppDropTarget*<br/>
Viz *ppDropTarget* v `IDocHostUIHandler::GetDropTarget` tématu Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="getelement"></a>CDHtmlDialog:: Get– element

Vrátí rozhraní na elementu HTML určeném parametrem *szElementId*.

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

*ppdisp*<br/>
`IDispatch` Ukazatel na požadovaný prvek nebo kolekci prvků.

*pbCollection*<br/>
LOGICKÁ hodnota označující, zda je objekt reprezentovaný prvkem *ppDisp* jediným prvkem nebo kolekcí prvků.

*pphtmlElement*<br/>
`IHTMLElement` Ukazatel na požadovaný element.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

První přetížení použijte v případě, že potřebujete zpracovat podmínky, ve kterých může být více než jeden prvek se zadaným ID. Pomocí posledního parametru můžete zjistit, zda je ukazatel rozhraní vrácen do kolekce nebo jedné položky. Pokud je ukazatel rozhraní v kolekci, můžete zadat dotaz `IHTMLElementCollection` na a použít jeho `item` vlastnost pro odkazování na prvky podle pořadového čísla.

Druhé přetížení selže, pokud je na stránce více než jeden prvek se stejným ID.

##  <a name="getelementhtml"></a>CDHtmlDialog:: GetElementHtml

Načte vlastnost elementu HTML identifikovaného parametrem *szElementId.* `innerHTML`

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

### <a name="return-value"></a>Návratová hodnota

Vlastnost elementu HTML identifikovaného parametrem szElementId nebo null, pokud nebyl nalezen prvek. `innerHTML`

##  <a name="getelementinterface"></a>  CDHtmlDialog::GetElementInterface

Načte požadovaný ukazatel rozhraní z elementu HTML identifikovaného pomocí *szElementId*.

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

*ppvObj*<br/>
Adresa ukazatele, který bude vyplněn požadovaným ukazatelem rozhraní, pokud je nalezen element a dotaz je úspěšný.

*refiid*<br/>
IDENTIFIKÁTOR rozhraní (IID) požadovaného rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>CDHtmlDialog:: GetElementProperty

Načte hodnotu vlastnosti identifikované identifikátorem *dispId* z elementu HTML identifikovaného parametrem *szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

*dispId*<br/>
ID odeslání vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Hodnota vlastnosti nebo prázdné varianty, pokud nebyla nalezena vlastnost nebo element.

##  <a name="getelementtext"></a>  CDHtmlDialog::GetElementText

Načte vlastnost elementu HTML identifikovaného parametrem *szElementId.* `innerText`

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

### <a name="return-value"></a>Návratová hodnota

Vlastnost elementu HTML identifikovaného parametrem szElementId nebo null, pokud nebyla nalezena vlastnost nebo element. `innerText`

##  <a name="getevent"></a>CDHtmlDialog:: getsudý

`IHTMLEventObj` Vrátí ukazatel na aktuální objekt události.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parametry

*ppEventObj*<br/>
Adresa ukazatele, který bude vyplněn `IHTMLEventObj` ukazatelem rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána pouze v rámci obslužné rutiny události DHTML.

##  <a name="getexternal"></a>CDHtmlDialog:: getexternal

Získá `IDispatch` rozhraní hostitele.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parametry

*ppDispatch*<br/>
Viz *ppDispatch* v [IDocHostUIHandler:: getexternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK při úspěchu nebo E_NOTIMPL při selhání.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: getexternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="gethostinfo"></a>  CDHtmlDialog::GetHostInfo

Načte možnosti uživatelského rozhraní hostitele.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Viz *pInfo* v [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="getoptionkeypath"></a>CDHtmlDialog:: GetOptionKeyPath

Načte klíč registru, ve kterém jsou uložené předvolby uživatele.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pchKey*<br/>
Viz *pchKey* v [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) v Windows SDK.

*dw*<br/>
Viz *DW* v `IDocHostUIHandler::GetOptionKeyPath` v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="hideui"></a>CDHtmlDialog:: HideUI

Skryje uživatelské rozhraní hostitele.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="isexternaldispatchsafe"></a>  CDHtmlDialog::IsExternalDispatchSafe

Označuje, zda je `IDispatch` rozhraní hostitele bezpečné pro skriptování.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu FALSE.

##  <a name="loadfromresource"></a>CDHtmlDialog:: LoadFromResource

Načte zadaný prostředek do ovládacího prvku WebBrowser v dialogovém okně DHTML.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Parametry

*lpszResource*<br/>
Ukazatel na řetězec obsahující název prostředku, který se má načíst.

*nRes*<br/>
ID prostředku, který se má načíst

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

##  <a name="m_busehtmltitle"></a>CDHtmlDialog:: m_bUseHtmlTitle

Označuje, zda se má jako titulek k dialogovému oknu použít název dokumentu HTML.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Poznámky

Pokud má **m**_ **bUseHtmlTitle** hodnotu true, je titulek dialogového okna nastavený na hodnotu název dokumentu HTML; v opačném případě se použije titulek v prostředku dialogového okna.

##  <a name="m_nhtmlresid"></a>  CDHtmlDialog::m_nHtmlResID

ID prostředku prostředku HTML, který se má zobrazit

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>  CDHtmlDialog::m_pBrowserApp

Ukazatel na aplikaci webového prohlížeče.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

##  <a name="m_sphtmldoc"></a>  CDHtmlDialog::m_spHtmlDoc

Ukazatel na dokument HTML.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

##  <a name="m_strcurrenturl"></a>  CDHtmlDialog::m_strCurrentUrl

Aktuální adresa URL.

```
CString m_strCurrentUrl;
```

##  <a name="m_szhtmlresid"></a>  CDHtmlDialog::m_szHtmlResID

Verze řetězce ID prostředku HTML.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>CDHtmlDialog:: Navigate

Přejde k prostředku identifikovanému adresou URL, která je určena parametrem *lpszURL*.

```
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Ukazatel na řetězec obsahující adresu URL, na kterou se má cílit.

*dwFlags*<br/>
Příznaky proměnné, která určuje, zda se má prostředek přidat do seznamu historie, zda se má číst do mezipaměti nebo zapisovat z mezipaměti a zda se má zobrazit prostředek v novém okně. Proměnná může být kombinací hodnot definovaných výčtem [BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) .

*lpszTargetFrameName*<br/>
Ukazatel na řetězec, který obsahuje název rámce, ve kterém se má zobrazit prostředek.

*lpszHeaders*<br/>
Ukazatel na hodnotu, která určuje hlavičky protokolu HTTP, které se mají odeslat na server. Tato záhlaví jsou přidána do výchozích hlaviček aplikace Internet Explorer. Hlavičky můžou tyto informace určit jako akci nutnou pro server, typ dat předávaný do serveru nebo stavový kód. Tento parametr se ignoruje, pokud adresa URL není adresa URL protokolu HTTP.

*lpvPostData*<br/>
Ukazatel na data, která se mají odeslat pomocí transakce HTTP POST. Například transakce POST slouží k odesílání dat shromážděných formulářem HTML. Pokud tento parametr neurčuje žádná data post, `Navigate` vydá transakce HTTP GET. Tento parametr se ignoruje, pokud adresa URL není adresa URL protokolu HTTP.

*dwPostDataLen*<br/>
Data, která se mají odeslat pomocí transakce HTTP POST Například transakce POST slouží k odesílání dat shromážděných formulářem HTML. Pokud tento parametr neurčuje žádná data post, `Navigate` vydá transakce HTTP GET. Tento parametr se ignoruje, pokud adresa URL není adresa URL protokolu HTTP.

##  <a name="onbeforenavigate"></a>CDHtmlDialog:: OnBeforeNavigate

Volá se rozhraním, aby se vyvolala událost, než dojde k navigaci.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel na `IDispatch` objekt.

*szUrl*<br/>
Ukazatel na řetězec obsahující adresu URL, na kterou se má přejít

##  <a name="ondocumentcomplete"></a>CDHtmlDialog:: OnDocumentComplete

Volá se rozhraním, aby se aplikace upozornila, když dokument splnil stav READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel na `IDispatch` objekt.

*szUrl*<br/>
Ukazatel na řetězec obsahující adresu URL, na kterou byl přesměrován.

##  <a name="ondocwindowactivate"></a>  CDHtmlDialog::OnDocWindowActivate

Volá se rozhraním, když se aktivuje nebo deaktivuje okno dokumentu.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fActivate*<br/>
Viz *fActivate* v [IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="onframewindowactivate"></a>CDHtmlDialog:: OnFrameWindowActivate

Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fActivate*<br/>
Viz *fActivate* v [IDocHostUIHandler:: OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="oninitdialog"></a>CDHtmlDialog:: OnInitDialog

Volá se v reakci na zprávu WM_INITDIALOG.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato zpráva se odešle do dialogového okna během `Create`volání, `CreateIndirect`nebo `DoModal` , která se objeví bezprostředně před zobrazením dialogového okna.

Tuto členskou funkci přepište, pokud potřebujete provést speciální zpracování při inicializaci dialogového okna. V přepsané verzi nejdříve zavolejte základní třídu `OnInitDialog` , ale Nezabereme její návratovou hodnotu. Obvykle se vrátí TRUE z přepsané členské funkce.

Systém Windows volá `OnInitDialog` funkci přes standardní globální proceduru dialogového okna společná pro všechna knihovna Microsoft Foundation Class dialogová okna, nikoli přes mapu zpráv, takže nepotřebujete pro tuto členskou funkci položku mapování zpráv.

##  <a name="onnavigatecomplete"></a>CDHtmlDialog:: OnNavigateComplete

Volá se rozhraním po dokončení navigace na zadanou adresu URL.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel na `IDispatch` objekt.

*szUrl*<br/>
Ukazatel na řetězec obsahující adresu URL, na kterou byl přesměrován.

##  <a name="resizeborder"></a>CDHtmlDialog:: ResizeBorder

Upozorní objekt, že potřebuje změnit velikost prostoru ohraničení.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parametry

*prcBorder*<br/>
Viz *prcBorder* v [IDocHostUIHandler:: ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) v Windows SDK.

*pUIWindow*<br/>
Viz *pUIWindow* v `IDocHostUIHandler::ResizeBorder` tématu Windows SDK.

*fFrameWindow*<br/>
Viz *fFrameWindow* v `IDocHostUIHandler::ResizeBorder` tématu Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

##  <a name="setcontrolproperty"></a>CDHtmlDialog:: SetControlProperty

Nastaví vlastnost ovládacího prvku ActiveX na novou hodnotu.

```
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID HTML ovládacího prvku ActiveX.

*dispId*<br/>
ID odeslání vlastnosti, kterou chcete nastavit.

*pVar*<br/>
Ukazatel na VARIANTu obsahující novou hodnotu vlastnosti.

*pdispControl*<br/>
Ukazatel na `IDispatch` rozhraní ovládacího prvku ActiveX.

*szPropName*<br/>
Řetězec obsahující název vlastnosti, která se má nastavit

##  <a name="setelementhtml"></a>CDHtmlDialog:: SetElementHtml

`innerHTML` Nastaví vlastnost elementu HTML.

```
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

*bstrText*<br/>
Nová hodnota `innerHTML` vlastnosti

*punkElem*<br/>
`IUnknown` Ukazatel prvku jazyka HTML.

##  <a name="setelementproperty"></a>CDHtmlDialog:: SetElementProperty

Nastaví vlastnost elementu HTML.

```
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

*dispId*<br/>
ID odeslání vlastnosti, kterou chcete nastavit.

*pVar*<br/>
Nová hodnota vlastnosti

##  <a name="setelementtext"></a>CDHtmlDialog:: SetElementText

`innerText` Nastaví vlastnost elementu HTML.

```
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

*bstrText*<br/>
Nová hodnota `innerText` vlastnosti

*punkElem*<br/>
`IUnknown` Ukazatel prvku jazyka HTML.

##  <a name="setexternaldispatch"></a>CDHtmlDialog:: SetExternalDispatch

Nastaví `IDispatch` rozhraní hostitele.

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parametry

*pdispExternal*<br/>
Nové `IDispatch` rozhraní.

##  <a name="sethostflags"></a>CDHtmlDialog:: SetHostFlags

Nastaví příznaky uživatelského rozhraní hostitele.

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Možné hodnoty naleznete v tématu [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) v Windows SDK.

##  <a name="showcontextmenu"></a>CDHtmlDialog:: ShowContextMenu

Volá se, když se zobrazí místní nabídka.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parametry

*dwID*<br/>
Viz *dwID* v [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) v Windows SDK.

*ppt*<br/>
Viz *PPT* v `IDocHostUIHandler::ShowContextMenu` v Windows SDK.

*pcmdtReserved*<br/>
Viz *pcmdtReserved* v `IDocHostUIHandler::ShowContextMenu` tématu Windows SDK.

*pdispReserved*<br/>
Viz *pdispReserved* v `IDocHostUIHandler::ShowContextMenu` tématu Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="showui"></a>CDHtmlDialog:: ShowUI

Zobrazuje uživatelské rozhraní hostitele.

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>Parametry

*dwID*<br/>
Viz *dwID* v [IDocHostUIHandler:: showUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) v Windows SDK.

*pActiveObject*<br/>
Podívejte se na téma `IDocHostUIHandler::ShowUI` *d pActiveObject* v tématu Windows SDK.

*pCommandTarget*<br/>
Viz *pCommandTarget* v `IDocHostUIHandler::ShowUI` tématu Windows SDK.

*pFrame*<br/>
Viz *pFrame* v `IDocHostUIHandler::ShowUI` tématu Windows SDK.

*pDoc*<br/>
Viz *pDoc* v `IDocHostUIHandler::ShowUI` tématu Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: showUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="translateaccelerator"></a>CDHtmlDialog:: TranslateAccelerator

Volá se, aby se zprávy klíče akcelerátoru v nabídce procesu.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parametry

*lpMsg*<br/>
Viz *lpMsg* v [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) v Windows SDK.

*pguidCmdGroup*<br/>
Viz *pguidCmdGroup* v `IDocHostUIHandler::TranslateAccelerator` tématu Windows SDK.

*nCmdID*<br/>
Viz *nCmdID* v `IDocHostUIHandler::TranslateAccelerator` tématu Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="translateurl"></a>CDHtmlDialog:: TranslateUrl

Volá se, aby se změnila adresa URL, která se má načíst.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parametry

*dwTranslate*<br/>
Viz *dwTranslate* v [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) v Windows SDK.

*pchURLIn*<br/>
Viz *pchURLIn* v `IDocHostUIHandler::TranslateUrl` tématu Windows SDK.

*ppchURLOut*<br/>
Viz *ppchURLOut* v `IDocHostUIHandler::TranslateUrl` tématu Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), jak je popsáno v Windows SDK.

##  <a name="updateui"></a>CDHtmlDialog:: UpdateUI

Volá se, aby se hostiteli informovalo, že se změnil stav příkazu.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je CDHtmlDialog implementace [IDocHostUIHandler:: UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), jak je popsáno v Windows SDK.

## <a name="see-also"></a>Viz také:

[DHtmlExplore Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[Makra pomocné rutiny DDX_DHtml](#ddx_dhtml_helper_macros)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
