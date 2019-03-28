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
ms.openlocfilehash: bda980c26f9791e1d4f03026f7e118e69a4ab881
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565802"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog – třída

Slouží k vytváření dialogových oken používající HTML namísto zdrojů dialogového okna k provedení jejich uživatelské rozhraní.

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

|Název|Popis|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Overridable, která je volána jako kontroly přístupu se, zda skriptovací objekty na stránce načíst přístup k externí odeslání řízení lokality. Kontroluje, abyste měli jistotu, že odesílání je, že buď bezpečné pro skriptování, nebo aktuální zóny umožňuje pro objekty, které nejsou bezpečné pro skriptování.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Overridable umožňuje vytvořit instanci ovládacího prvku serveru pro hostování ovládacího prvku WebBrowser v dialogovém okně.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Výměna dat mezi členské proměnné a hodnotu vlastnosti ovládacího prvku ActiveX na stránku HTML.|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Výměna dat mezi členskou proměnnou a zaškrtávacího políčka na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|Výměna dat mezi členskou proměnnou a všechny vlastnosti elementu HTML na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|Výměna dat mezi členskou proměnnou a přepínač na stránku HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Získá nebo nastaví index založený na seznamu na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|Získá nebo nastaví zobrazení textu položky seznamu pole (podle aktuální index) na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Získá nebo nastaví hodnotu pole položky seznamu (podle aktuální index) na stránce HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Zničí nemodální dialogové okno.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Umožňuje nemodálních dialogových oken.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Umožňuje filtrovat objekty dat schránky vytvořené hostované prohlížečem dialogového okna.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|Načte `IDispatch` rozhraní na ovládací prvek ActiveX vloží do dokumentu HTML.|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|Načte požadované vlastnosti zadaný ovládací prvek ActiveX.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Načte Uniform Resource Locator (URL) přidružené k aktuální dokument.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Načte rozhraní IHTMLDocument2 u aktuálně načtené dokumentu HTML.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Voláno rozhraním obsažený ovládací prvek WebBrowser, když se používá jako cíl přetažení umožňující dialogového okna slouží k poskytování alternativu [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|
|[CDHtmlDialog::GetElement](#getelement)|Získá rozhraní na prvek jazyka HTML.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|Načte `innerHTML` vlastnost elementu HTML.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Načte požadované rozhraní ukazatel z prvku HTML.|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|Načte hodnotu vlastnosti elementu HTML.|
|[CDHtmlDialog::GetElementText](#getelementtext)|Načte `innerText` vlastnost elementu HTML.|
|[CDHtmlDialog::GetEvent](#getevent)|Získá `IHTMLEventObj` ukazatel na aktuální objekt události.|
|[CDHtmlDialog::GetExternal](#getexternal)|Získá hostitele `IDispatch` rozhraní.|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Načte možnosti uživatelského rozhraní hostiteli.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Načte klíče registru, ve kterém jsou uložené předvolby uživatele.|
|[CDHtmlDialog::HideUI](#hideui)|Skryje uživatelské rozhraní hostitele.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Označuje, zda hostitel `IDispatch` rozhraní je bezpečný pro skriptování.|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|Načte zadaný prostředek do ovládacího prvku WebBrowser.|
|[CDHtmlDialog::Navigate](#navigate)|Přejde na zadanou adresu URL.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Volá se rozhraním, než se aktivuje událost navigace.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Volá se rozhraním, aby se aplikaci oznámilo, dokument se dosáhne stavu READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Volá se rozhraním, když se aktivuje nebo deaktivuje okno dokumentu.|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Volá se v reakci na nezavěsíte zprávu.|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|Volá se rozhraním po dokončení navigační události.|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|Upozorní objekt, který je potřeba změnit velikost místa jeho ohraničení.|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|Nastaví vlastnost ovládacího prvku ActiveX na novou hodnotu.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|Nastaví `innerHTML` vlastnost elementu HTML.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Nastaví vlastnost elementu HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|Nastaví `innerText` vlastnost elementu HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Nastaví hostitele `IDispatch` rozhraní.|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Nastaví příznaky uživatelského rozhraní hostiteli.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Volá se, když místní nabídka se nezobrazí.|
|[CDHtmlDialog::ShowUI](#showui)|Zobrazuje uživatelské rozhraní hostitele.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Volá se, aby zpracování nabídky přístupové klíče zpráv.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Volá se, aby změnit adresu URL, který se má načíst.|
|[CDHtmlDialog::UpdateUI](#updateui)|Volá se, aby upozornil hostitele, který se změnil stav příkazu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Označuje, zda chcete použít název dokumentu HTML jako dialogové okno popisek.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|Resource ID HTML prostředek má být zobrazen.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Ukazatel na aplikace webového prohlížeče.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Ukazatel na dokument HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|Aktuální adresa URL.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Řetězec verze ID prostředku HTML.|

## <a name="remarks"></a>Poznámky

`CDHtmlDialog` můžete načíst HTML, který se má zobrazit z buď prostředku HTML nebo adresy URL.

`CDHtmlDialog` Můžete také dat exchange pomocí ovládacích prvků HTML a zpracovávat události z ovládacích prvků HTML, jako je tlačítko klikne.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

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

##  <a name="ddx_dhtml_helper_macros"></a>  Pomocné rutiny Ddx_dhtml

Pomocné rutiny ddx_dhtml umožňují snadný přístup k běžně používaných vlastností ovládacích prvků na stránce HTML.

### <a name="data-exchange-macros"></a>Makra výměny dat

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Nastavuje nebo načítá hodnotu vlastnosti z vybraného ovládacího prvku.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Nastavuje nebo načítá text mezi počáteční a koncovou značku aktuálního prvku.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Nastavuje nebo načítá HTML mezi úvodní a koncovou značkou aktuálního prvku.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Nastavuje nebo načítá cílový bod adresy URL nebo ukotvení.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Nastavuje nebo načítá cílového okna nebo rámce.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Nastavuje nebo načítá název obrázkem nebo videoklipem v dokumentu.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Nastavuje nebo načítá adresy URL přidružené rámce.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Nastavuje nebo načítá adresy URL přidružené rámce.|

##  <a name="canaccessexternal"></a>  CDHtmlDialog::CanAccessExternal

Overridable, která je volána jako kontroly přístupu se, zda skriptovací objekty na stránce načíst přístup k externí odeslání řízení lokality. Kontroluje, abyste měli jistotu, že odesílání je, že buď bezpečné pro skriptování, nebo aktuální zóny umožňuje pro objekty, které nejsou bezpečné pro skriptování.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="cdhtmldialog"></a>  CDHtmlDialog::CDHtmlDialog

Vytvoří pole založené na prostředcích dialogového okna dynamického HTML.

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
Řetězec zakončený hodnotou null, který je název prostředku šablony dialogového okna.

*szHtmlResID*<br/>
Řetězec zakončený hodnotou null, který je název prostředku HTML.

*pParentWnd*<br/>
Ukazatel na objekt okna nadřazené nebo vlastník (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je hodnota NULL, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.

*nIDTemplate*<br/>
Obsahuje identifikační číslo prostředku šablony dialogového okna.

*nHtmlResID*<br/>
Obsahuje identifikační číslo prostředku HTML.

### <a name="remarks"></a>Poznámky

Tedy o druhou podobu konstruktor poskytuje přístup k prostředku dialogového okna pomocí názvu šablony. Třetí forma konstruktor poskytuje přístup k prostředku dialogového okna pomocí ID prostředku šablony. Obvykle ID začíná **IDD_** předponu.

##  <a name="_dtorcdhtmldialog"></a>  CDHtmlDialog::~CDHtmlDialog

Odstraní objekt CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Poznámky

[CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) členská funkce použije ke zničení nemodálních dialogových oken, které jsou vytvořeny pomocí [CDialog::Create](../../mfc/reference/cdialog-class.md#create).

##  <a name="createcontrolsite"></a>  CDHtmlDialog::CreateControlSite

Overridable umožňuje vytvořit instanci ovládacího prvku serveru pro hostování ovládacího prvku WebBrowser v dialogovém okně.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parametry

*pContainer*<br/>
Ukazatel [colecontrolcontainer –](../../mfc/reference/colecontrolcontainer-class.md) objektu

*ppSite*<br/>
Ukazatel na ukazatel [colecontrolsite –](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce vrátit instanci třídy vlastní ovládací prvek webu můžete přepsat.

##  <a name="ddx_dhtml_axcontrol"></a>  CDHtmlDialog::DDX_DHtml_AxControl

Výměna dat mezi členské proměnné a hodnotu vlastnosti ovládacího prvku ActiveX na stránku HTML.

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
Hodnota parametru ID značky object ve zdroji HTML pro ovládací prvek ActiveX.

*dispId*<br/>
ID odbavení vlastnosti, se kterým se má pro výměnu dat.

*szPropName*<br/>
Název vlastnosti

*var*<br/>
Datový člen typu VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md), nebo [CComVariant](../../atl/reference/ccomvariant-class.md), který obsahuje hodnotu vyměněn za vlastnosti ovládacího prvku ActiveX.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>  CDHtmlDialog::DDX_DHtml_CheckBox

Výměna dat mezi členskou proměnnou a zaškrtávacího políčka na stránce HTML.

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
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která se vyměňují.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>  CDHtmlDialog::DDX_DHtml_ElementText

Výměna dat mezi členskou proměnnou a všechny vlastnosti elementu HTML na stránce HTML.

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
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*dispId*<br/>
Dispatch ID elementu HTML, který chcete pro výměnu dat.

*value*<br/>
Hodnota, která se vyměňují.

##  <a name="ddx_dhtml_radio"></a>  CDHtmlDialog::DDX_DHtml_Radio

Výměna dat mezi členskou proměnnou a přepínač na stránku HTML.

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
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která se vyměňují.

##  <a name="ddx_dhtml_selectindex"></a>  CDHtmlDialog::DDX_DHtml_SelectIndex

Získá nebo nastaví index založený na seznamu na stránce HTML.

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
Hodnota, která jste zadali pro ovládací prvek HTML `id` parametru.

*value*<br/>
Hodnota, která se vyměňují.

##  <a name="ddx_dhtml_selectstring"></a>  CDHtmlDialog::DDX_DHtml_SelectString

Získá nebo nastaví zobrazení textu položky seznamu pole (podle aktuální index) na stránce HTML.

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
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která se vyměňují.

##  <a name="ddx_dhtml_selectvalue"></a>  CDHtmlDialog::DDX_DHtml_SelectValue

Získá nebo nastaví hodnotu pole položky seznamu (podle aktuální index) na stránce HTML.

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
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která se vyměňují.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>  CDHtmlDialog::DestroyModeless

Odpojí nemodální dialogové okno z `CDHtmlDialog` objektu a odstraní objekt.

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>  CDHtmlDialog::EnableModeless

Umožňuje nemodálních dialogových oken.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parametry

*fEnable*<br/>
Zobrazit *fEnable* v [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="filterdataobject"></a>  CDHtmlDialog::FilterDataObject

Umožňuje filtrovat objekty dat schránky vytvořené hostované prohlížečem dialogového okna.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parametry

*pDO*<br/>
Zobrazit *pDO* v [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) v sadě Windows SDK.

*ppDORet*<br/>
Zobrazit *ppDORet* v `IDocHostUIHandler::FilterDataObject` v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="getcontroldispatch"></a>  CDHtmlDialog::GetControlDispatch

Načte `IDispatch` rozhraní na ovládací prvek ActiveX vloží do dokumentu HTML vrácené [GetDHtmlDocument](#getdhtmldocument).

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parametry

*szId*<br/>
ID HTML ovládacího prvku ActiveX.

*ppdisp*<br/>
`IDispatch` Rozhraní ovládacího prvku-li najít webové stránce.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="getcontrolproperty"></a>  CDHtmlDialog::GetControlProperty

Načte požadované vlastnosti zadaný ovládací prvek ActiveX.

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
Název vlastnosti ve výchozím nastavení národního prostředí aktuálního uživatele.

*pdispControl*<br/>
`IDispatch` Ukazatel ovládacího prvku ActiveX.

*dispId*<br/>
ID odbavení vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Hodnotu typu variant obsahující požadovaná vlastnost nebo prázdný typ variant, pokud ovládací prvek nebo vlastnost nebyla nalezena.

### <a name="remarks"></a>Poznámky

Přetížení jsou seřazeny od nejméně efektivní v horní části nejúčinnější v dolní části.

##  <a name="getcurrenturl"></a>  CDHtmlDialog::GetCurrentUrl

Načte Uniform Resource Locator (URL) přidružené k aktuální dokument.

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parametry

*szUrl*<br/>
A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje adresu URL pro načtení.

##  <a name="getdhtmldocument"></a>  CDHtmlDialog::GetDHtmlDocument

Načte [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) rozhraní v aktuálně načtených dokumentu HTML.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parametry

*\*\*pphtmlDoc* ukazatel na ukazatel na dokument HTML.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT. Pokud je úspěšná, vrátí hodnotu S_OK.

##  <a name="getdroptarget"></a>  CDHtmlDialog::GetDropTarget

Voláno rozhraním obsažený ovládací prvek WebBrowser, když se používá jako cíl přetažení umožňující dialogového okna slouží k poskytování alternativu [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parametry

*pDropTarget*<br/>
Zobrazit *pDropTarget* v [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) v sadě Windows SDK.

*ppDropTarget*<br/>
Zobrazit *ppDropTarget* v `IDocHostUIHandler::GetDropTarget` v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="getelement"></a>  CDHtmlDialog::GetElement

Vrátí rozhraní na prvku HTML určeného *szElementId*.

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
`IDispatch` Ukazatel na požadovaný element nebo kolekci elementů.

*pbCollection*<br/>
HODNOTU označující, zda objekt reprezentovaný *ppdisp* je jeden element nebo kolekci elementů.

*pphtmlElement*<br/>
`IHTMLElement` Ukazatel na požadovaný element.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

První přetížení použít, pokud je potřeba zpracovat podmínky, ve kterých může být více než jeden element se zadaným ID. Poslední parametr můžete zjistit, zda je vrácený ukazatel rozhraní do kolekce nebo jednu položku. Je-li ukazatel rozhraní na kolekci, můžete zadat dotaz na `IHTMLElementCollection` a použít jeho `item` vlastnost odkazují na prvky podle pořadí.

Druhé přetížení se nezdaří, pokud existuje více než jeden element se stejným ID na stránce.

##  <a name="getelementhtml"></a>  CDHtmlDialog::GetElementHtml

Načte `innerHTML` vlastnost elementu HTML, který je identifikován *szElementId*.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

### <a name="return-value"></a>Návratová hodnota

`innerHTML` Vlastnost elementu HTML, který je identifikován *szElementId* nebo hodnota NULL, pokud element nebyl nalezen.

##  <a name="getelementinterface"></a>  CDHtmlDialog::GetElementInterface

Načte požadované rozhraní ukazatel z prvku HTML, který je identifikován *szElementId*.

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
Adresa ukazatel, který bude vyplněn ukazatel požadované rozhraní Pokud je nalezen element a dotaz bude úspěšná.

*refiid*<br/>
ID rozhraní (IID) požadovaný rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>  CDHtmlDialog::GetElementProperty

Načte hodnotu vlastnosti určený podle *dispId* z prvku HTML, který je identifikován *szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

*dispId*<br/>
ID odbavení vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Hodnota vlastnosti nebo prázdný variant, pokud vlastnost nebo element nebyl nalezen.

##  <a name="getelementtext"></a>  CDHtmlDialog::GetElementText

Načte `innerText` vlastnost elementu HTML, který je identifikován *szElementId*.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID elementu HTML.

### <a name="return-value"></a>Návratová hodnota

`innerText` Vlastnost elementu HTML, který je identifikován *szElementId* nebo hodnota NULL, pokud vlastnost nebo element nebyl nalezen.

##  <a name="getevent"></a>  CDHtmlDialog::GetEvent

Vrátí `IHTMLEventObj` ukazatel na aktuální objekt události.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parametry

*ppEventObj*<br/>
Adresa ukazatel, který bude vyplněn `IHTMLEventObj` ukazatel rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce by měla volat pouze z v rámci obslužné rutiny události DHTML.

##  <a name="getexternal"></a>  CDHtmlDialog::GetExternal

Získá hostitele `IDispatch` rozhraní.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parametry

*ppDispatch*<br/>
Zobrazit *ppDispatch* v [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo E_NOTIMPL při selhání.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="gethostinfo"></a>  CDHtmlDialog::GetHostInfo

Načte možnosti uživatelského rozhraní hostiteli.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Zobrazit *pInfo* v [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="getoptionkeypath"></a>  CDHtmlDialog::GetOptionKeyPath

Načte klíče registru, ve kterém jsou uložené předvolby uživatele.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pchKey*<br/>
Zobrazit *pchKey* v [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) v sadě Windows SDK.

*dw*<br/>
Zobrazit *dw* v `IDocHostUIHandler::GetOptionKeyPath` ve Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="hideui"></a>  CDHtmlDialog::HideUI

Skryje uživatelské rozhraní hostitele.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="isexternaldispatchsafe"></a>  CDHtmlDialog::IsExternalDispatchSafe

Označuje, zda hostitel `IDispatch` rozhraní je bezpečný pro skriptování.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu FALSE.

##  <a name="loadfromresource"></a>  CDHtmlDialog::LoadFromResource

Načte zadaný prostředek do ovládacího prvku WebBrowser v dialogovém okně DHTML.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Parametry

*lpszResource*<br/>
Ukazatel na řetězec obsahující název prostředku, který chcete načíst.

*nRes*<br/>
ID prostředku pro načtení.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; v opačném případě FALSE.

##  <a name="m_busehtmltitle"></a>  CDHtmlDialog::m_bUseHtmlTitle

Označuje, zda chcete použít název dokumentu HTML jako dialogové okno popisek.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Poznámky

Pokud **m**_ **bUseHtmlTitle** má hodnotu TRUE, dialogové okno popisek je nastavena na název dokumentu HTML; v opačném případě se používá titulek v prostředku dialogového okna.

##  <a name="m_nhtmlresid"></a>  CDHtmlDialog::m_nHtmlResID

Resource ID HTML prostředek má být zobrazen.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>  CDHtmlDialog::m_pBrowserApp

Ukazatel na aplikace webového prohlížeče.

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

Řetězec verze ID prostředku HTML.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>  CDHtmlDialog::Navigate

Přejde na prostředku označeném identifikátorem adresu URL, která je určená *lpszURL*.

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
Ukazatel na řetězec obsahující adresu URL, na kterou bude cílit.

*dwFlags*<br/>
Příznaky proměnná, která určuje, zda bude příslušný materiál přidán do seznamu historie, jestli se z mezipaměti zápisu nebo čtení do mezipaměti a jestli se mají zobrazovat prostředku v novém okně. Proměnná může být kombinací hodnot určené [BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) výčtu.

*lpszTargetFrameName*<br/>
Ukazatel na řetězec, který obsahuje název rámce, ve kterém chcete zobrazit zdroj.

*lpszHeaders*<br/>
Ukazatel na hodnotu, která určuje hlavičky protokolu HTTP k odeslání na server. Tyto hlavičky se přidají do výchozí hlavičky aplikace Internet Explorer. Záhlaví můžete zadat tyto informace jako dělat serveru typu dat předávaných do serveru nebo stavovým kódem. Tento parametr je ignorován, pokud adresa URL není adresa URL protokolu HTTP.

*lpvPostData*<br/>
Ukazatel na data k odeslání se transakce HTTP POST. Například transakce POST slouží k odesílání dat shromážděných z formuláře HTML. Pokud tento parametr není zadán všechna data účtovat `Navigate` vydá transakci HTTP GET. Tento parametr je ignorován, pokud adresa URL není adresa URL protokolu HTTP.

*dwPostDataLen*<br/>
Data k odeslání se transakce HTTP POST. Například transakce POST slouží k odesílání dat shromážděných z formuláře HTML. Pokud tento parametr není zadán všechna data účtovat `Navigate` vydá transakci HTTP GET. Tento parametr je ignorován, pokud adresa URL není adresa URL protokolu HTTP.

##  <a name="onbeforenavigate"></a>  CDHtmlDialog::OnBeforeNavigate

Volá se rozhraním, aby událost vyvolána předtím, než dojde k navigaci.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel `IDispatch` objektu.

*szUrl*<br/>
Ukazatel na řetězec obsahující adresu URL přejděte k položce.

##  <a name="ondocumentcomplete"></a>  CDHtmlDialog::OnDocumentComplete

Volá se rozhraním, aby se aplikaci oznámilo, když dokument má dosáhne stavu READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel `IDispatch` objektu.

*szUrl*<br/>
Ukazatel na řetězec obsahující adresu URL, na kterou se přejde.

##  <a name="ondocwindowactivate"></a>  CDHtmlDialog::OnDocWindowActivate

Volá se rozhraním, když se aktivuje nebo deaktivuje okno dokumentu.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fActivate*<br/>
Zobrazit *fActivate* v [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="onframewindowactivate"></a>  CDHtmlDialog::OnFrameWindowActivate

Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fActivate*<br/>
Zobrazit *fActivate* v [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="oninitdialog"></a>  CDHtmlDialog::OnInitDialog

Volá se v reakci na nezavěsíte zprávu.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato zpráva se pošle do dialogového okna průběhu `Create`, `CreateIndirect`, nebo `DoModal` volání, ke kterým dochází, těsně před spuštěním zobrazí dialogové okno.

Tato členská funkce přepište, pokud je třeba provést zvláštní zpracování při inicializaci dialogových oken. Přepsané verze nejprve volat základní třídy `OnInitDialog` ale ignorovat jeho návratovou hodnotu. Obvykle se vrací TRUE, z vaší funkce přepsanému členu.

Volání Windows `OnInitDialog` funkce prostřednictvím standardní globální – dialogové okno postup společné pro všechny dialogová okna knihovny Microsoft Foundation Class, ne přes mapu zpráv, proto není nutné položka mapy zpráv pro tuto funkci člena.

##  <a name="onnavigatecomplete"></a>  CDHtmlDialog::OnNavigateComplete

Volá se rozhraním, až se dokončí přechod na zadané adrese URL.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel `IDispatch` objektu.

*szUrl*<br/>
Ukazatel na řetězec obsahující adresu URL, na kterou se přejde.

##  <a name="resizeborder"></a>  CDHtmlDialog::ResizeBorder

Upozorní objekt, který je potřeba změnit velikost místa jeho ohraničení.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parametry

*prcBorder*<br/>
Zobrazit *prcBorder* v [IDocHostUIHandler::ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) v sadě Windows SDK.

*pUIWindow*<br/>
Zobrazit *pUIWindow* v `IDocHostUIHandler::ResizeBorder` v sadě Windows SDK.

*fFrameWindow*<br/>
Zobrazit *fFrameWindow* v `IDocHostUIHandler::ResizeBorder` v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

##  <a name="setcontrolproperty"></a>  CDHtmlDialog::SetControlProperty

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
ID odbavení vlastnosti chcete nastavit.

*pVar*<br/>
Ukazatel na hodnotu typu VARIANT obsahující hodnota nové vlastnosti.

*pdispControl*<br/>
Ukazatel na ovládací prvek ActiveX `IDispatch` rozhraní.

*szPropName*<br/>
Řetězec obsahující název vlastnosti chcete nastavit.

##  <a name="setelementhtml"></a>  CDHtmlDialog::SetElementHtml

Nastaví `innerHTML` vlastnost elementu HTML.

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
Nová hodnota `innerHTML` vlastnost.

*punkElem*<br/>
`IUnknown` Ukazatel elementu HTML.

##  <a name="setelementproperty"></a>  CDHtmlDialog::SetElementProperty

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
ID odbavení vlastnosti chcete nastavit.

*pVar*<br/>
Nová hodnota vlastnosti.

##  <a name="setelementtext"></a>  CDHtmlDialog::SetElementText

Nastaví `innerText` vlastnost elementu HTML.

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
Nová hodnota `innerText` vlastnost.

*punkElem*<br/>
`IUnknown` Ukazatel elementu HTML.

##  <a name="setexternaldispatch"></a>  CDHtmlDialog::SetExternalDispatch

Nastaví hostitele `IDispatch` rozhraní.

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parametry

*pdispExternal*<br/>
Nové `IDispatch` rozhraní.

##  <a name="sethostflags"></a>  CDHtmlDialog::SetHostFlags

Nastaví hostitele příznaky uživatelského rozhraní.

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Možné hodnoty najdete v části [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) v sadě Windows SDK.

##  <a name="showcontextmenu"></a>  CDHtmlDialog::ShowContextMenu

Volá se, když místní nabídka se nezobrazí.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parametry

*dwID*<br/>
Zobrazit *dwID* v [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) v sadě Windows SDK.

*ppt*<br/>
Zobrazit *ppt* v `IDocHostUIHandler::ShowContextMenu` ve Windows SDK.

*pcmdtReserved*<br/>
Zobrazit *pcmdtReserved* v `IDocHostUIHandler::ShowContextMenu` v sadě Windows SDK.

*pdispReserved*<br/>
Zobrazit *pdispReserved* v `IDocHostUIHandler::ShowContextMenu` v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="showui"></a>  CDHtmlDialog::ShowUI

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
Zobrazit *dwID* v [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) v sadě Windows SDK.

*pActiveObject*<br/>
Zobrazit *d pActiveObject* v `IDocHostUIHandler::ShowUI` v sadě Windows SDK.

*pCommandTarget*<br/>
Zobrazit *pCommandTarget* v `IDocHostUIHandler::ShowUI` v sadě Windows SDK.

*pFrame*<br/>
Zobrazit *pFrame* v `IDocHostUIHandler::ShowUI` v sadě Windows SDK.

*pDoc*<br/>
Zobrazit *pDoc* v `IDocHostUIHandler::ShowUI` v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="translateaccelerator"></a>  CDHtmlDialog::TranslateAccelerator

Volá se, aby zpracování nabídky přístupové klíče zpráv.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parametry

*lpMsg*<br/>
Zobrazit *lpMsg* v [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) v sadě Windows SDK.

*pguidCmdGroup*<br/>
Zobrazit *pguidCmdGroup* v `IDocHostUIHandler::TranslateAccelerator` v sadě Windows SDK.

*nCmdID*<br/>
Zobrazit *nCmdID* v `IDocHostUIHandler::TranslateAccelerator` v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="translateurl"></a>  CDHtmlDialog::TranslateUrl

Volá se, aby změnit adresu URL, který se má načíst.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parametry

*dwTranslate*<br/>
Zobrazit *dwTranslate* v [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) v sadě Windows SDK.

*pchURLIn*<br/>
Zobrazit *pchURLIn* v `IDocHostUIHandler::TranslateUrl` v sadě Windows SDK.

*ppchURLOut*<br/>
Zobrazit *ppchURLOut* v `IDocHostUIHandler::TranslateUrl` v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

##  <a name="updateui"></a>  CDHtmlDialog::UpdateUI

Volá se, aby upozornil hostitele, který se změnil stav příkazu.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementace společnosti CDHtmlDialog [IDocHostUIHandler::UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Ukázka DHtmlExplore knihovny MFC](../../visual-cpp-samples.md)<br/>
[Makra pomocné rutiny DDX_DHtml](#ddx_dhtml_helper_macros)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
