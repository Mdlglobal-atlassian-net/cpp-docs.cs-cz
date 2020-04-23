---
title: Třída CDHtmlDialog
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
ms.openlocfilehash: e2e4306320c52b8276d915848dfa6e460982c92b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753382"
---
# <a name="cdhtmldialog-class"></a>Třída CDHtmlDialog

Používá se k vytvoření dialogových oken, která k implementaci uživatelského rozhraní používají spíše html než prostředky dialogových oken.

## <a name="syntax"></a>Syntaxe

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|Vytvoří objekt CDHtmlDialog.|
|[CDHtmlDialog::~CDHtmlDialog](#_dtorcdhtmldialog)|Zničí objekt CDHtmlDialog.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Overridable, který je volán jako kontrola přístupu, chcete-li zjistit, zda skriptování objektů na načtené stránce přístup k externí odeslání webu ovládacího prvku. Zkontroluje, zda je odeslání bezpečné pro skriptování nebo aktuální zóna umožňuje objekty, které nejsou bezpečné pro skriptování.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Overridable slouží k vytvoření instance řídicího webu pro hostování ovládacího prvku WebBrowser v dialogovém okně.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Vyměňuje data mezi členskou proměnnou a hodnotou vlastnosti ovládacího prvku ActiveX na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Vyměňuje data mezi členskou proměnnou a zaškrtávacím políčkem na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|Vyměňuje data mezi proměnnou člena a libovolnou vlastností elementu HTML na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|Vyměňuje data mezi členskou proměnnou a přepínacím tlačítkem na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Získá nebo nastaví index seznamu na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|Získá nebo nastaví zobrazovaný text položky seznamu (na základě aktuálního indexu) na stránce HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Získá nebo nastaví hodnotu položky seznamu (na základě aktuálního indexu) na stránce HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Zničí nemodální dialogové okno.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Povolí nemodální dialogová okna.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Umožňuje dialogovému oknu filtrovat datové objekty schránky vytvořené hostovaným prohlížečem.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|Načte `IDispatch` rozhraní v ovládacím prvku ActiveX vloženém do dokumentu HTML.|
|[CDHtmlDialog::Vlastnost GetControlProperty](#getcontrolproperty)|Načte požadovanou vlastnost zadaného ovládacího prvku ActiveX.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Načte url jednotného prostředku přidruženého k aktuálnímu dokumentu.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Načte rozhraní IHTMLDocument2 v aktuálně načteném dokumentu HTML.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Volat obsažený webbrowser ovládací prvek, když je používán jako cíl přetažení povolit dialogové okno zadat alternativní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[CDHtmlDialog::GetElement](#getelement)|Získá rozhraní na elementHTML.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|Načte `innerHTML` vlastnost elementu HTML.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Načte požadovaný ukazatel rozhraní z elementu HTML.|
|[CDHtmlDialog::Vlastnost GetElementProperty](#getelementproperty)|Načte hodnotu vlastnosti prvku HTML.|
|[CDHtmlDialog::GetElementText](#getelementtext)|Načte `innerText` vlastnost elementu HTML.|
|[CDHtmlDialog::GetEvent](#getevent)|Získá `IHTMLEventObj` ukazatel na aktuální objekt události.|
|[CDHtmlDialog::GetExternal](#getexternal)|Získá `IDispatch` rozhraní hostitele.|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Načte možnosti ui hostitele.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Načte klíč registru, pod kterým jsou uloženy uživatelské předvolby.|
|[CDHtmlDialog:Hideui](#hideui)|Skryje ui hostitele.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Označuje, zda je `IDispatch` rozhraní hostitele bezpečné pro skriptování.|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|Načte zadaný prostředek do ovládacího prvku WebBrowser.|
|[CDHtmlDialog::Navigace](#navigate)|Přejde na zadanou adresu URL.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Volat rámci před je aktivována navigační událost.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Volat rámci upozornit aplikaci, když dokument dosáhl stavu READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Volat rámci při aktivaci nebo deaktivaci okna dokumentu.|
|[CDHtmlDialog::OnframeWindowActivate](#onframewindowactivate)|Volat rámci při aktivaci nebo deaktivaci okna rámce.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Volána v reakci na zprávu WM_INITDIALOG.|
|[CDHtmlDialog::OnnavigateComplete](#onnavigatecomplete)|Volat rámci po dokončení navigační události.|
|[CDHtmlDialog::Změna velikostiOhraničení](#resizeborder)|Upozorní objekt, který potřebuje ke změně velikosti prostoru ohraničení.|
|[CDHtmlDialog::Vlastnost SetControlProperty](#setcontrolproperty)|Nastaví vlastnost ovládacího prvku ActiveX na novou hodnotu.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|Nastaví `innerHTML` vlastnost elementu HTML.|
|[CDHtmlDialog::Vlastnost SetElementProperty](#setelementproperty)|Nastaví vlastnost prvku HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|Nastaví `innerText` vlastnost elementu HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Nastaví `IDispatch` rozhraní hostitele.|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Nastaví příznaky ui hostitele.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Nazývá se, když se má zobrazit místní nabídka.|
|[CDHtmlDialog::showui](#showui)|Zobrazuje ui hostitele.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Nazývá se zpracování zpráv akcelerátoru menu.|
|[CDHtmlDialog::Přeložiturl](#translateurl)|Nazývá se upravit adresu URL, která má být načtena.|
|[CDHtmlDialog::UpdateUI](#updateui)|Voláno k upozornění hostitele, že se změnil stav příkazu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Označuje, zda se má jako popisek dialogu použít název dokumentu HTML.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|ID prostředku HTML, který má být zobrazen.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Ukazatel na aplikaci webového prohlížeče.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Ukazatel na dokument HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|Aktuální adresa URL.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Řetězcová verze ID prostředku HTML.|

## <a name="remarks"></a>Poznámky

`CDHtmlDialog`můžete načíst HTML, který se zobrazí z prostředku HTML nebo adresy URL.

`CDHtmlDialog`můžete také provést výměnu dat s ovládacími prvky HTML a zpracovávat události z ovládacích prvků HTML, jako jsou kliknutí na tlačítko.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[Cwnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[Cdialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdhtml.h

## <a name="ddx_dhtml-helper-macros"></a><a name="ddx_dhtml_helper_macros"></a>DDX_DHtml pomocná makra

Pomocná makra DDX_DHtml umožňují snadný přístup k běžně používaným vlastnostem ovládacích prvků na stránce HTML.

### <a name="data-exchange-macros"></a>Makra výměny dat

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Nastaví nebo načte vlastnost Value z vybraného ovládacího prvku.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Nastaví nebo načte text mezi počátečními a koncovými značkami aktuálního prvku.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Nastaví nebo načte HTML mezi počáteční a koncovou značkou aktuálního prvku.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Nastaví nebo načte cílovou adresu URL nebo kotevní bod.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Nastaví nebo načte cílové okno nebo rámeček.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Nastaví nebo načte název obrázku nebo videoklipu v dokumentu.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Nastaví nebo načte adresu URL přidruženého rámce.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Nastaví nebo načte adresu URL přidruženého rámce.|

## <a name="cdhtmldialogcanaccessexternal"></a><a name="canaccessexternal"></a>CDHtmlDialog::CanAccessExternal

Overridable, který je volán jako kontrola přístupu, chcete-li zjistit, zda skriptování objektů na načtené stránce přístup k externí odeslání webu ovládacího prvku. Zkontroluje, zda je odeslání bezpečné pro skriptování nebo aktuální zóna umožňuje objekty, které nejsou bezpečné pro skriptování.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="cdhtmldialogcdhtmldialog"></a><a name="cdhtmldialog"></a>CDHtmlDialog::CDHtmlDialog

Vytvoří dynamické dialogové okno HTML založené na prostředcích.

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
Řetězec s ukončeným hodnotou null, který je názvem prostředku šablony dialogového okna.

*szHtmlResID*<br/>
Řetězec ukončený hodnotou null, který je názvem prostředku HTML.

*pParentWnd*<br/>
Ukazatel na nadřazený objekt okna nebo objekt okna vlastníka (typu [CWnd),](../../mfc/reference/cwnd-class.md)ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno objektu dialogu je nastaveno na hlavní okno aplikace.

*nIDŠablona*<br/>
Obsahuje id číslo prostředku šablony dialogového okna.

*nHtmlResID*<br/>
Obsahuje id číslo prostředku HTML.

### <a name="remarks"></a>Poznámky

Druhá forma konstruktoru poskytuje přístup k prostředku dialogu prostřednictvím názvu šablony. Třetí forma konstruktoru poskytuje přístup k prostředku dialogu prostřednictvím ID šablony prostředku. ID obvykle začíná předponou **IDD_.**

## <a name="cdhtmldialogcdhtmldialog"></a><a name="_dtorcdhtmldialog"></a>CDHtmlDialog::~CDHtmlDialog

Zničí objekt CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Poznámky

Členská funkce [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) musí být použita ke zničení nemodálních dialogových oken vytvořených [cDialog::Create](../../mfc/reference/cdialog-class.md#create).

## <a name="cdhtmldialogcreatecontrolsite"></a><a name="createcontrolsite"></a>CDHtmlDialog::CreateControlSite

Overridable slouží k vytvoření instance řídicího webu pro hostování ovládacího prvku WebBrowser v dialogovém okně.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parametry

*pKontejner*<br/>
Ukazatel na objekt [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)

*ppSite*<br/>
Ukazatel na ukazatel [cOleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tuto členovou funkci můžete přepsat a vrátit tak instanci vlastní třídy řídicího webu.

## <a name="cdhtmldialogddx_dhtml_axcontrol"></a><a name="ddx_dhtml_axcontrol"></a>CDHtmlDialog::DDX_DHtml_AxControl

Vyměňuje data mezi členskou proměnnou a hodnotou vlastnosti ovládacího prvku ActiveX na stránce HTML.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Hodnota parametru ID značky objektu ve zdroji HTML ovládacího prvku ActiveX.

*Dispid*<br/>
ID odeslání vlastnosti, se kterou chcete vyměňovat data.

*szPropName*<br/>
Název vlastnosti

*var*<br/>
Datový člen typu VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md)nebo [CComVariant](../../atl/reference/ccomvariant-class.md), který obsahuje hodnotu vyměněnou s vlastností ovládacího prvku ActiveX.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

## <a name="cdhtmldialogddx_dhtml_checkbox"></a><a name="ddx_dhtml_checkbox"></a>CDHtmlDialog::DDX_DHtml_CheckBox

Vyměňuje data mezi členskou proměnnou a zaškrtávacím políčkem na stránce HTML.

```cpp
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která je vyměňována.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

## <a name="cdhtmldialogddx_dhtml_elementtext"></a><a name="ddx_dhtml_elementtext"></a>CDHtmlDialog::DDX_DHtml_ElementText

Vyměňuje data mezi proměnnou člena a libovolnou vlastností elementu HTML na stránce HTML.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*Dispid*<br/>
ID odeslání prvku HTML, se kterým chcete vyměňovat data.

*value*<br/>
Hodnota, která je vyměňována.

## <a name="cdhtmldialogddx_dhtml_radio"></a><a name="ddx_dhtml_radio"></a>CDHtmlDialog::DDX_DHtml_Radio

Vyměňuje data mezi členskou proměnnou a přepínacím tlačítkem na stránce HTML.

```cpp
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která je vyměňována.

## <a name="cdhtmldialogddx_dhtml_selectindex"></a><a name="ddx_dhtml_selectindex"></a>CDHtmlDialog::DDX_DHtml_SelectIndex

Získá nebo nastaví index seznamu na stránce HTML.

```cpp
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Hodnota, kterou jste zadali pro `id` parametr ovládacího prvku HTML.

*value*<br/>
Hodnota, která je vyměňována.

## <a name="cdhtmldialogddx_dhtml_selectstring"></a><a name="ddx_dhtml_selectstring"></a>CDHtmlDialog::DDX_DHtml_SelectString

Získá nebo nastaví zobrazovaný text položky seznamu (na základě aktuálního indexu) na stránce HTML.

```cpp
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která je vyměňována.

## <a name="cdhtmldialogddx_dhtml_selectvalue"></a><a name="ddx_dhtml_selectvalue"></a>CDHtmlDialog::DDX_DHtml_SelectValue

Získá nebo nastaví hodnotu položky seznamu (na základě aktuálního indexu) na stránce HTML.

```cpp
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*value*<br/>
Hodnota, která je vyměňována.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

## <a name="cdhtmldialogdestroymodeless"></a><a name="destroymodeless"></a>CDHtmlDialog::DestroyModeless

Odpojí nemodlavé `CDHtmlDialog` dialogové okno od objektu a zničí objekt.

```cpp
void DestroyModeless();
```

## <a name="cdhtmldialogenablemodeless"></a><a name="enablemodeless"></a>CDHtmlDialog::EnableModeless

Povolí nemodální dialogová okna.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parametry

*fPo*<br/>
Viz *fEnable* v [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialogfilterdataobject"></a><a name="filterdataobject"></a>CDHtmlDialog::FilterDataObject

Umožňuje dialogovému oknu filtrovat datové objekty schránky vytvořené hostovaným prohlížečem.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parametry

*Chop*<br/>
Viz *pDO* v [iDocHostUIHandler::FilterDataDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) v sdk systému Windows.

*ppDORet*<br/>
Viz *ppDORet* v `IDocHostUIHandler::FilterDataObject` sada Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::FilterDataDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialoggetcontroldispatch"></a><a name="getcontroldispatch"></a>CDHtmlDialog::GetControlDispatch

Načte `IDispatch` rozhraní ovládacího prvku ActiveX vloženého do dokumentu HTML vráceného [službou GetDHtmlDocument](#getdhtmldocument).

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parametry

*szId*<br/>
ID HTML ovládacího prvku ActiveX.

*ppdisp*<br/>
Rozhraní `IDispatch` ovládacího prvku, pokud je nalezen na webové stránce.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cdhtmldialoggetcontrolproperty"></a><a name="getcontrolproperty"></a>CDHtmlDialog::Vlastnost GetControlProperty

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
Ukazatel `IDispatch` ovládacího prvku ActiveX.

*Dispid*<br/>
ID odeslání vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Varianta obsahující požadovanou vlastnost nebo prázdnou variantu, pokud ovládací prvek nebo vlastnost nebyla nalezena.

### <a name="remarks"></a>Poznámky

Přetížení jsou uvedeny z nejméně efektivní v horní části na nejúčinnější v dolní části.

## <a name="cdhtmldialoggetcurrenturl"></a><a name="getcurrenturl"></a>CDHtmlDialog::GetCurrentUrl

Načte url jednotného prostředku přidruženého k aktuálnímu dokumentu.

```cpp
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parametry

*szUrl*<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující adresu URL načíst.

## <a name="cdhtmldialoggetdhtmldocument"></a><a name="getdhtmldocument"></a>CDHtmlDialog::GetDHtmlDocument

Načte rozhraní [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) v aktuálně načteném dokumentu HTML.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parametry

* \* \** Ukazatel na ukazatel na dokument HTML.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT. Vrátí S_OK v případě úspěchu.

## <a name="cdhtmldialoggetdroptarget"></a><a name="getdroptarget"></a>CDHtmlDialog::GetDropTarget

Volat obsažený webbrowser ovládací prvek, když je používán jako cíl přetažení povolit dialogové okno zadat alternativní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parametry

*pDropTarget*<br/>
Viz *pDropTarget* v [iDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) v sadě Windows SDK.

*ppDropTarget*<br/>
Viz *ppDropTarget* v `IDocHostUIHandler::GetDropTarget` sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialoggetelement"></a><a name="getelement"></a>CDHtmlDialog::GetElement

Vrátí rozhraní prvku HTML určeného *parametrem szElementId*.

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
ID prvku HTML.

*ppdisp*<br/>
Ukazatel `IDispatch` na požadovaný prvek nebo kolekci prvků.

*pbKolekce*<br/>
A BOOL označující, zda objekt reprezentovaný *ppdisp* je jeden prvek nebo kolekce prvků.

*pphtmlElement*<br/>
Ukazatel `IHTMLElement` na požadovaný prvek.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

První přetížení použijte, pokud potřebujete zpracovat podmínky, ve kterých může být více než jeden prvek se zadaným ID. Pomocí posledního parametru můžete zjistit, zda je vrácený ukazatel rozhraní do kolekce nebo jedné položky. Pokud je ukazatel rozhraní v kolekci, `IHTMLElementCollection` můžete dotaz `item` pro a použít jeho vlastnost odkazovat na prvky podle ordinální pozice.

Druhé přetížení se nezdaří, pokud je více než jeden prvek se stejným ID na stránce.

## <a name="cdhtmldialoggetelementhtml"></a><a name="getelementhtml"></a>CDHtmlDialog::GetElementHtml

Načte `innerHTML` vlastnost elementu HTML identifikovaného *szElementId*.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID prvku HTML.

### <a name="return-value"></a>Návratová hodnota

Vlastnost `innerHTML` elementu HTML identifikovaného *szElementId* nebo NULL, pokud prvek nebyl nalezen.

## <a name="cdhtmldialoggetelementinterface"></a><a name="getelementinterface"></a>CDHtmlDialog::GetElementInterface

Načte požadovaný ukazatel rozhraní z elementu HTML identifikovaného *szElementId*.

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
ID prvku HTML.

*ppvObj*<br/>
Adresa ukazatele, který bude vyplněn požadovaným ukazatelem rozhraní, pokud je prvek nalezen a dotaz je úspěšný.

*refiid*<br/>
ID rozhraní (IID) požadovaného rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

## <a name="cdhtmldialoggetelementproperty"></a><a name="getelementproperty"></a>CDHtmlDialog::Vlastnost GetElementProperty

Načte hodnotu vlastnosti identifikované *dispId* z elementu HTML identifikovaného *szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID prvku HTML.

*Dispid*<br/>
ID odeslání vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Hodnota vlastnosti nebo prázdné varianty, pokud vlastnost nebo prvek nebyl nalezen.

## <a name="cdhtmldialoggetelementtext"></a><a name="getelementtext"></a>CDHtmlDialog::GetElementText

Načte `innerText` vlastnost elementu HTML identifikovaného *szElementId*.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID prvku HTML.

### <a name="return-value"></a>Návratová hodnota

Vlastnost `innerText` elementu HTML identifikovaného *szElementId* nebo NULL, pokud vlastnost nebo prvek nebyl nalezen.

## <a name="cdhtmldialoggetevent"></a><a name="getevent"></a>CDHtmlDialog::GetEvent

Vrátí `IHTMLEventObj` ukazatel na aktuální objekt události.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parametry

*ppEventObj*<br/>
Adresa ukazatele, který bude vyplněn `IHTMLEventObj` ukazatelem rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána pouze z obslužné rutiny události DHTML.

## <a name="cdhtmldialoggetexternal"></a><a name="getexternal"></a>CDHtmlDialog::GetExternal

Získá `IDispatch` rozhraní hostitele.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parametry

*ppOdeslání*<br/>
Viz *ppDispatch* v [iDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo E_NOTIMPL na neúspěch.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialoggethostinfo"></a><a name="gethostinfo"></a>CDHtmlDialog::GetHostInfo

Načte možnosti ui hostitele.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parametry

*pInformace*<br/>
Viz *pInfo* v [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) v sdk windows sdk.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialoggetoptionkeypath"></a><a name="getoptionkeypath"></a>CDHtmlDialog::GetOptionKeyPath

Načte klíč registru, pod kterým jsou uloženy uživatelské předvolby.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pchKey*<br/>
Viz *pchKey* v [iDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) v sadě Windows SDK.

*Dw*<br/>
Viz *dw* in `IDocHostUIHandler::GetOptionKeyPath` v sdk systému Windows.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialoghideui"></a><a name="hideui"></a>CDHtmlDialog:Hideui

Skryje ui hostitele.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialogisexternaldispatchsafe"></a><a name="isexternaldispatchsafe"></a>CDHtmlDialog::IsExternalDispatchSafe

Označuje, zda je `IDispatch` rozhraní hostitele bezpečné pro skriptování.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu NEPRAVDA.

## <a name="cdhtmldialogloadfromresource"></a><a name="loadfromresource"></a>CDHtmlDialog::LoadFromResource

Načte zadaný prostředek do ovládacího prvku WebBrowser v dialogovém okně DHTML.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Parametry

*lpszZdroj*<br/>
Ukazatel na řetězec obsahující název prostředku, který má být načíst.

*nRes*<br/>
ID prostředku k načtení.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

## <a name="cdhtmldialogm_busehtmltitle"></a><a name="m_busehtmltitle"></a>CDHtmlDialog::m_bUseHtmlTitle

Označuje, zda se má jako popisek dialogu použít název dokumentu HTML.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Poznámky

Pokud je **m**_ **bUseHtmlTitle** TRUE, je titulek dialogu nastaven na název dokumentu HTML; v opačném případě se použije titulek v prostředku dialogu.

## <a name="cdhtmldialogm_nhtmlresid"></a><a name="m_nhtmlresid"></a>CDHtmlDialog::m_nHtmlResID

ID prostředku HTML, který má být zobrazen.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

## <a name="cdhtmldialogm_pbrowserapp"></a><a name="m_pbrowserapp"></a>CDHtmlDialog::m_pBrowserApp

Ukazatel na aplikaci webového prohlížeče.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

## <a name="cdhtmldialogm_sphtmldoc"></a><a name="m_sphtmldoc"></a>CDHtmlDialog::m_spHtmlDoc

Ukazatel na dokument HTML.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

## <a name="cdhtmldialogm_strcurrenturl"></a><a name="m_strcurrenturl"></a>CDHtmlDialog::m_strCurrentUrl

Aktuální adresa URL.

```
CString m_strCurrentUrl;
```

## <a name="cdhtmldialogm_szhtmlresid"></a><a name="m_szhtmlresid"></a>CDHtmlDialog::m_szHtmlResID

Řetězcová verze ID prostředku HTML.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

## <a name="cdhtmldialognavigate"></a><a name="navigate"></a>CDHtmlDialog::Navigace

Přejde na prostředek identifikovaný adresou URL určenou *parametrem lpszURL*.

```cpp
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
Ukazatel na řetězec obsahující adresu URL, na kterou má být cílit.

*dwFlags*<br/>
Příznaky proměnné, která určuje, zda má být prostředek přidat do seznamu historie, zda se má číst do mezipaměti nebo zapisovat z mezipaměti a zda má být prostředek zobrazen v novém okně. Proměnná může být kombinací hodnot definovaných výčtu [BrowserNavConstants.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\))

*lpszTargetFrameName*<br/>
Ukazatel na řetězec, který obsahuje název rámce, ve kterém chcete zobrazit prostředek.

*lpszZáhlaví*<br/>
Ukazatel na hodnotu, která určuje hlavičky PROTOKOLU HTTP, které mají být odeslány na server. Tato záhlaví jsou přidána do výchozích záhlaví aplikace Internet Explorer. Záhlaví mohou určit takové informace, jako je akce požadovaná od serveru, typ dat předávaných serveru nebo stavový kód. Tento parametr je ignorován, pokud adresa URL není adresa URL HTTP.

*lpvPostData*<br/>
Ukazatel na data, která mají být odeslána s transakcí HTTP POST. Transakce POST se například používá k odesílání dat shromážděných formulářem HTML. Pokud tento parametr neurčuje žádná `Navigate` data příspěvku, vydá transakci HTTP GET. Tento parametr je ignorován, pokud adresa URL není adresa URL HTTP.

*dwPostDataLen*<br/>
Data, která mají být odeslána s transakcí HTTP POST. Transakce POST se například používá k odesílání dat shromážděných formulářem HTML. Pokud tento parametr neurčuje žádná `Navigate` data příspěvku, vydá transakci HTTP GET. Tento parametr je ignorován, pokud adresa URL není adresa URL HTTP.

## <a name="cdhtmldialogonbeforenavigate"></a><a name="onbeforenavigate"></a>CDHtmlDialog::OnBeforeNavigate

Volat rámci způsobit událost požáru před dojde k navigaci.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel na `IDispatch` objekt.

*szUrl*<br/>
Ukazatel na řetězec obsahující adresu URL, na kterou chcete přejít.

## <a name="cdhtmldialogondocumentcomplete"></a><a name="ondocumentcomplete"></a>CDHtmlDialog::OnDocumentComplete

Volat rámci upozornit aplikace, pokud dokument dosáhl stavu READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel na `IDispatch` objekt.

*szUrl*<br/>
Ukazatel na řetězec obsahující adresu URL, na kterou byl navigován.

## <a name="cdhtmldialogondocwindowactivate"></a><a name="ondocwindowactivate"></a>CDHtmlDialog::OnDocWindowActivate

Volat rámci při aktivaci nebo deaktivaci okna dokumentu.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fAktivace*<br/>
Viz *viz fAktivace* v [iDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialogonframewindowactivate"></a><a name="onframewindowactivate"></a>CDHtmlDialog::OnframeWindowActivate

Volat rámci při aktivaci nebo deaktivaci okna rámce.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fAktivace*<br/>
Viz *fActivate* in [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) in the Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialogoninitdialog"></a><a name="oninitdialog"></a>CDHtmlDialog::OnInitDialog

Volána v reakci na zprávu WM_INITDIALOG.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Tato zpráva je odeslána do `Create` `CreateIndirect`dialogového `DoModal` okna během volání , nebo volání, ke kterým dojde bezprostředně před zobrazením dialogového okna.

Přepište tuto členovou funkci, pokud potřebujete provést speciální zpracování při inicializování dialogového okna. V přepsané verzi nejprve volat `OnInitDialog` základní třídy, ale ignorovat jeho vrácená hodnota. Z potlačené členské funkce obvykle vrátíte hodnotu PRAVDA.

Systém Windows `OnInitDialog` volá funkci prostřednictvím standardního globálního dialogového okna, který je společný pro všechna dialogová okna knihovny tříd aplikace Microsoft Foundation, nikoli prostřednictvím mapy zpráv, takže pro tuto členskou funkci nepotřebujete položku mapy zpráv.

## <a name="cdhtmldialogonnavigatecomplete"></a><a name="onnavigatecomplete"></a>CDHtmlDialog::OnnavigateComplete

Volat rámci po dokončení navigace na zadanou adresu URL.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel na `IDispatch` objekt.

*szUrl*<br/>
Ukazatel na řetězec obsahující adresu URL, na kterou byl navigován.

## <a name="cdhtmldialogresizeborder"></a><a name="resizeborder"></a>CDHtmlDialog::Změna velikostiOhraničení

Upozorní objekt, který potřebuje ke změně velikosti prostoru ohraničení.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parametry

*prcHranice*<br/>
Viz *prcBorder* v [iDocHostUIHandler::ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) v sdk windows sdk.

*pUIOkno*<br/>
Viz *pUIWindow* v `IDocHostUIHandler::ResizeBorder` sadě Windows SDK.

*fFrameWindow*<br/>
Viz *fFrameWindow* v `IDocHostUIHandler::ResizeBorder` sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

## <a name="cdhtmldialogsetcontrolproperty"></a><a name="setcontrolproperty"></a>CDHtmlDialog::Vlastnost SetControlProperty

Nastaví vlastnost ovládacího prvku ActiveX na novou hodnotu.

```cpp
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

*Dispid*<br/>
ID odeslání vlastnosti nastavit.

*pVar*<br/>
Ukazatel na VARIANT obsahující novou hodnotu vlastnosti.

*pdispControl*<br/>
Ukazatel na rozhraní ovládacího `IDispatch` prvku ActiveX.

*szPropName*<br/>
Řetězec obsahující název vlastnosti nastavit.

## <a name="cdhtmldialogsetelementhtml"></a><a name="setelementhtml"></a>CDHtmlDialog::SetElementHtml

Nastaví `innerHTML` vlastnost elementu HTML.

```cpp
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID prvku HTML.

*bstrText*<br/>
Nová hodnota vlastnosti. `innerHTML`

*punkElem*<br/>
Ukazatel `IUnknown` prvku HTML.

## <a name="cdhtmldialogsetelementproperty"></a><a name="setelementproperty"></a>CDHtmlDialog::Vlastnost SetElementProperty

Nastaví vlastnost prvku HTML.

```cpp
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID prvku HTML.

*Dispid*<br/>
ID odeslání vlastnosti nastavit.

*pVar*<br/>
Nová hodnota vlastnosti.

## <a name="cdhtmldialogsetelementtext"></a><a name="setelementtext"></a>CDHtmlDialog::SetElementText

Nastaví `innerText` vlastnost elementu HTML.

```cpp
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
ID prvku HTML.

*bstrText*<br/>
Nová hodnota vlastnosti. `innerText`

*punkElem*<br/>
Ukazatel `IUnknown` prvku HTML.

## <a name="cdhtmldialogsetexternaldispatch"></a><a name="setexternaldispatch"></a>CDHtmlDialog::SetExternalDispatch

Nastaví `IDispatch` rozhraní hostitele.

```cpp
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parametry

*pdispExterní*<br/>
Nové `IDispatch` rozhraní.

## <a name="cdhtmldialogsethostflags"></a><a name="sethostflags"></a>CDHtmlDialog::SetHostFlags

Nastaví příznaky hostitelského uznatí.

```cpp
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Možné hodnoty naleznete [v tématu DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) v sadě Windows SDK.

## <a name="cdhtmldialogshowcontextmenu"></a><a name="showcontextmenu"></a>CDHtmlDialog::ShowContextMenu

Nazývá se, když se má zobrazit místní nabídka.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parametry

*dwID*<br/>
Viz *dwID* v [iDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) v sdk systému Windows.

*Ppt*<br/>
Viz *ppt* v `IDocHostUIHandler::ShowContextMenu` sadě Windows SDK.

*pcmdtVyhrazeno*<br/>
Viz *pcmdtReserved* in `IDocHostUIHandler::ShowContextMenu` v sadě Windows SDK.

*pdispReserved*<br/>
Viz *pdispReserved* in `IDocHostUIHandler::ShowContextMenu` in the Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialogshowui"></a><a name="showui"></a>CDHtmlDialog::showui

Zobrazuje ui hostitele.

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
Viz *dwID* v [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) v sdk windows sdk.

*pActiveObject*<br/>
Viz *d pActiveObject* v `IDocHostUIHandler::ShowUI` sadě Windows SDK.

*pCommandTarget*<br/>
Viz *pCommandTarget* v `IDocHostUIHandler::ShowUI` souboru Windows SDK.

*pRám*<br/>
Viz *pFrame* in `IDocHostUIHandler::ShowUI` v sadě Windows SDK.

*pDoc*<br/>
Viz *pDoc* in `IDocHostUIHandler::ShowUI` v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialogtranslateaccelerator"></a><a name="translateaccelerator"></a>CDHtmlDialog::TranslateAccelerator

Nazývá se zpracování zpráv akcelerátoru menu.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parametry

*lpMsg*<br/>
Viz *lpMsg* v [iDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) v sdk systému Windows.

*pguidCmdGroup*<br/>
Viz *pguidCmdGroup* v `IDocHostUIHandler::TranslateAccelerator` sadě Windows SDK.

*nCmdID*<br/>
Viz *nCmdID* v `IDocHostUIHandler::TranslateAccelerator` sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialogtranslateurl"></a><a name="translateurl"></a>CDHtmlDialog::Přeložiturl

Nazývá se upravit adresu URL, která má být načtena.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parametry

*dwPřeložit*<br/>
Viz *dwTranslate* v [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) v sdk systému Windows.

*pchURLIn*<br/>
Viz *pchURLIn* v `IDocHostUIHandler::TranslateUrl` sadě Windows SDK.

*ppchURLOut*<br/>
Viz *ppchURLOut* v `IDocHostUIHandler::TranslateUrl` sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="cdhtmldialogupdateui"></a><a name="updateui"></a>CDHtmlDialog::UpdateUI

Voláno k upozornění hostitele, že se změnil stav příkazu.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementací [cdhtmldialog iDocHostUIHandler::UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), jak je popsáno v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC DHtmlExplore](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml pomocná makra](#ddx_dhtml_helper_macros)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
