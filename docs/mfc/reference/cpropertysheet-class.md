---
title: Cpropertysheet – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
dev_langs:
- C++
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2e9e13f7b5838cb13497dd874f7f0cf42f34e98
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200143"
---
# <a name="cpropertysheet-class"></a>Cpropertysheet – třída

Představuje seznam vlastností, označovaný také jako dialogová okna Karta.

## <a name="syntax"></a>Syntaxe

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Vytvoří `CPropertySheet` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPropertySheet::AddPage](#addpage)|Na stránce se přidá do seznamu vlastností.|
|[CPropertySheet::Construct](#construct)|Vytvoří `CPropertySheet` objektu.|
|[CPropertySheet::Create](#create)|Zobrazí nemodálního seznamu vlastností.|
|[CPropertySheet::DoModal](#domodal)|Zobrazí modální seznam vlastností.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Označuje, zda seznam vlastností používá skládaný nebo posouvání karty.|
|[CPropertySheet::EndDialog](#enddialog)|Ukončí seznam vlastností.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Načte index active stránky vlastností.|
|[CPropertySheet::GetActivePage](#getactivepage)|Vrátí objekt aktivní stránkou.|
|[CPropertySheet::GetPage](#getpage)|Načte ukazatel na zadanou stránku.|
|[CPropertySheet::GetPageCount](#getpagecount)|Získá počet stránek v seznamu vlastností.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Načte index zadané stránky vlastností.|
|[CPropertySheet::GetTabControl](#gettabcontrol)|Načte ukazatel na ovládací prvek karty.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Převede jednotkách dialogového okna obdélník na obrazovce jednotky.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Přepsání pro rozšíření Inicializace seznamu vlastností.|
|[CPropertySheet::PressButton](#pressbutton)|Simuluje volba od určeného tlačítka v seznamu vlastností.|
|[CPropertySheet::RemovePage](#removepage)|Odebere stránku ze seznamu vlastností.|
|[CPropertySheet::SetActivePage](#setactivepage)|Prostřednictvím kódu programu nastaví objekt aktivní stránkou.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Nastaví text pro tlačítko pro dokončení.|
|[CPropertySheet::SetTitle](#settitle)|Nastaví popisek seznamu vlastností.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Umožňuje Průvodce tlačítka.|
|[CPropertySheet::SetWizardMode](#setwizardmode)|Povolí režim průvodce.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Windows [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2) struktury. Poskytuje přístup k základní vlastnost seznamu parametrů.|

## <a name="remarks"></a>Poznámky

Seznam vlastností se skládá z `CPropertySheet` objekt a jeden nebo více [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objekty. Seznam vlastností zobrazí rozhraní jako okno se sadou kartu indexy a oblasti, která obsahuje aktuálně vybrané stránky. Uživatel přejde na určitou stránku pomocí příslušné karty.

`CPropertySheet` poskytuje podporu pro rozbalených [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2) struktura zavedená ve Windows 98 a Windows NT 2000. Struktura obsahuje další příznaky a členy, které podporují použití rastrový obrázek pozadí "vodoznak".

K těmto novým obrázkům zobrazení automaticky v váš objekt seznamu vlastností, předejte platné hodnoty pro Image rastrového obrázku a palety volání [CPropertySheet::Construct](#construct) nebo [CPropertySheet::CPropertySheet](#cpropertysheet).

I když `CPropertySheet` není odvozen od [CDialog](../../mfc/reference/cdialog-class.md)Správa `CPropertySheet` objektu je třeba pro správu `CDialog` objektu. Příklad vytvoření seznamu vlastností vyžaduje skládá ze dvou částí: volání konstruktoru a následně zavolat [DoModal](#domodal) pro modální seznam vlastností nebo [vytvořit](#create) pro nemodálního seznamu vlastností. `CPropertySheet` má dva typy konstruktorů: [CPropertySheet::Construct](#construct) a [CPropertySheet::CPropertySheet](#cpropertysheet).

Při sestavování `CPropertySheet` objektu některé [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) může způsobit, že první odpovídající výjimce dojde k. Výsledkem pokusu o změnu stylu seznam vlastností, před vytvořením listu systému. Chcete-li předejít této výjimce, ujistěte se, že jste nastavili následující styly při vytváření vašeho `CPropertySheet`:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Tyto styly jsou volitelné a nesmí způsobit, že první odpovídající výjimce:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Jakýkoli jiný `Window Styles` jsou zakázané a neměli byste je povolit.

Výměna dat mezi `CPropertySheet` objekt a externí objekt je podobný výměna dat se `CDialog` objektu. Podstatným rozdílem je, že nastavení vlastností jsou obvykle členské proměnné `CPropertyPage` objekty, nikoli z `CPropertySheet` samotného objektu.

Můžete vytvořit typ dialogové okno Karta nazývá průvodce, který se skládá z seznam vlastností s posloupnost stránky vlastností, které provedou uživatele kroky operace, jako je například nastavení zařízení nebo vytváření bulletinu. V dialogovém okně wizard-type. karta na stránkách vlastností nemají karty a pouze jednu vlastnost stránka není viditelná v čase. Také, namísto toho, aby **OK** a **použít** má dialogové okno Karta wizard-type. tlačítka, **zpět** tlačítko, **Další** nebo  **Dokončit** tlačítko, **zrušit** tlačítko a **pomáhají** tlačítko.

Vytvoření dialogového okna typ průvodce, postupujte podle stejných kroků, které byste použili k vytvoření standardní vlastností, ale volání [SetWizardMode](#setwizardmode) před voláním [DoModal](#domodal). Chcete-li povolit Průvodce tlačítka, zavolejte [SetWizardButtons](#setwizardbuttons), pomocí příznaků přizpůsobit jejich funkce a vzhledu. Povolit **Dokončit** tlačítko, volání [SetFinishText](#setfinishtext) poté, co uživatel má provést akce na poslední stránce průvodce.

Další informace o tom, jak používat `CPropertySheet` objekty, najdete v článku [seznamy vlastností a stránky vlastností](../../mfc/property-sheets-and-property-pages-in-mfc.md). Také, najdete v článku znalostní báze Q146916: postupy: vytvoření cpropertysheet – nemodální pomocí standardní tlačítka a článek Q300606: postupy: návrh možností změny velikosti vlastností knihovny MFC.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

##  <a name="addpage"></a>  CPropertySheet::AddPage

Přidá zadaný stránku s kartou úplně vpravo v seznamu vlastností.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*Fyzická_stránka*  
Odkazuje na stránku chcete přidat do seznamu vlastností. Nemůže mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Přidání stránek do seznamu vlastností v pořadí zleva doprava, že chcete, aby se mohly zobrazit.

`AddPage` Přidá [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) objektu `CPropertySheet` objektu v seznamu stránek, ale ve skutečnosti nevytváří v okně na stránce. Rozhraní framework odloží vytváření okna pro na stránce, až uživatel vybere tuto stránku.

Po přidání vlastností stránky pomocí `AddPage`, `CPropertySheet` je nadřazeného člena `CPropertyPage`. Chcete-li získat přístup k seznamu vlastností na stránce vlastností, zavolejte [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).

Není nutné čekat až do vytvoření okna listu vlastností pro volání `AddPage`. Obvykle budete volat `AddPage` před voláním [DoModal](#domodal) nebo [vytvořit](#create).

Při volání `AddPage` po zobrazení stránky vlastností, bude odrážet řádku kartu nově přidané stránky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>  CPropertySheet::Construct

Vytvoří `CPropertySheet` objektu.

```
void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);


void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);


void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);


void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>Parametry

*nIDCaption*  
ID popisku se použije pro seznam vlastností.

*pParentWnd*  
Ukazatel do nadřazeného okna vlastností. Pokud má hodnotu NULL, bude nadřazené okno hlavní okno aplikace.

*iSelectPage*  
Index, který bude zpočátku v horní části stránky. Výchozí hodnota je první stránka Přidat do listu.

*pszCaption*  
Ukazatel na řetězec, který obsahuje popisek, který má být použit pro seznam vlastností. Nemůže mít hodnotu NULL.

*hbmWatermark*  
Popisovač rastrový obrázek vodoznaku stránky vlastností.

*hpalWatermark*  
Popisovač na paletě rastrový obrázek vodoznaku a/nebo rastrový obrázek záhlaví.

*hbmHeader*  
Popisovač rastrový obrázek záhlaví stránky vlastností.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce, pokud jeden z konstruktorů třídy již nebyla volána. Například volání `Construct` při deklaraci nebo přidělit pole `CPropertySheet` objekty. V případě pole, je nutné volat `Construct` pro každého člena v poli.

Chcete-li zobrazit seznam vlastností, zavolejte [DoModal](#domodal) nebo [vytvořit](#create). Řetězec obsažený v první parametr bude umístěn v záhlaví pro seznam vlastností.

Můžete zobrazit vodoznak a/nebo hlavičce bitové kopie automaticky používáte třetí a čtvrtý prototypů `Construct`, uvedené výše a předejte platné hodnoty *hbmWatermark*, *hpalWatermark* , a/nebo *hbmHeader* parametry.

### <a name="example"></a>Příklad

Následující příklad ukazuje, v části Co je okolností by volat `Construct`.

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

##  <a name="cpropertysheet"></a>  CPropertySheet::CPropertySheet

Vytvoří `CPropertySheet` objektu.

```
CPropertySheet();


explicit CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);


explicit CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);


CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);


CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>Parametry

*nIDCaption*  
ID popisku se použije pro seznam vlastností.

*pParentWnd*  
Body do nadřazeného okna vlastností. Pokud má hodnotu NULL, bude nadřazené okno hlavní okno aplikace.

*iSelectPage*  
Index, který bude zpočátku v horní části stránky. Výchozí hodnota je první stránka Přidat do listu.

*pszCaption*  
Odkazuje na řetězec, který obsahuje popisek, který má být použit pro seznam vlastností. Nemůže mít hodnotu NULL.

*hbmWatermark*  
Popisovač vlastností rastrového obrázku na pozadí.

*hpalWatermark*  
Popisovač na paletě rastrový obrázek vodoznaku a/nebo rastrový obrázek záhlaví.

*hbmHeader*  
Popisovač rastrový obrázek záhlaví stránky vlastností.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit seznam vlastností, zavolejte [DoModal](#domodal) nebo [vytvořit](#create). Řetězec obsažený v první parametr bude umístěn v záhlaví pro seznam vlastností.

Pokud máte více parametrů (například, pokud používáte pole), použijte [vytvořit](#construct) místo `CPropertySheet`.

Můžete zobrazit vodoznak a/nebo hlavičce bitové kopie automaticky používáte třetí a čtvrtý prototypů `CPropertySheet`výše, a předejte platné hodnoty *hbmWatermark*, *hpalWatermark*, a / nebo *hbmHeader* parametry.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>  CPropertySheet::Create

Zobrazí nemodálního seznamu vlastností.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*  
Body do nadřazeného okna. Pokud má hodnotu NULL, nadřazený prvek je ploše.

*dwStyle*  
Styly oken pro seznam vlastností. Úplný seznam dostupných stylů, najdete v části [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*  
Rozšířené styly oken pro seznam vlastností. Úplný seznam dostupných stylů, najdete v části [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud úspěšně; vytvoření seznamu vlastností jinak 0.

### <a name="remarks"></a>Poznámky

Volání `Create` může být v rámci konstruktoru, nebo je můžete volat po vyvolání konstruktoru.

Výchozí styl, vyjádřené předáním -1 jako *dwStyle*, je ve skutečnosti WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE. Výchozí hodnota rozšířený styl okna, vyjádřené jako 0 předáním *dwExStyle*, je ve skutečnosti WS_EX_DLGMODALFRAME.

`Create` Členská funkce vrátí ihned po vytvoření seznamu vlastností. Chcete-li zničit seznam vlastností, zavolejte [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).

Modeless – seznam vlastností zobrazuje voláním `Create` nemají tlačítka OK, zrušení, použít a pomoc, stejně jako modální dialogové okno vlastností. Požadované tlačítka musí být vytvořený uživatelem.

Chcete-li zobrazit modální seznam vlastností, zavolejte [DoModal](#domodal) místo.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>  CPropertySheet::DoModal

Zobrazí modální seznam vlastností.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL byla-li funkce úspěšná; v opačném případě 0 nebo -1. Pokud seznam vlastností se vytvořilo jako průvodce (viz [SetWizardMode](#setwizardmode)), `DoModal` vrátí ID_WIZFINISH nebo IDCANCEL.

### <a name="remarks"></a>Poznámky

Návratová hodnota odpovídá ID ovládacího prvku, který zavření seznamu vlastností. Po návratu tato funkce windows odpovídající seznam vlastností a všechny stránky budou zničení. Samotných objektech budou i nadále existovat. Obvykle se načtou data z [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objekty po `DoModal` vrátí IDOK.

Chcete-li zobrazit nemodálního seznamu vlastností, zavolejte [vytvořit](#create) místo.

Když se vytvoří jeho odpovídající prostředek dialogového okna stránky vlastností, může to způsobit první odpovídající výjimce. To vyplývá z vlastností změnu stylu prostředku dialogového okna na požadovaný styl předtím, než se vytvoří na stránce. Protože prostředky jsou obecně jen pro čtení, tím dojde k výjimce. Systém zpracovává výjimku a vytvoří kopii tohoto změněného prostředku. První odpovídající výjimce se proto dá ignorovat.

> [!NOTE]
>  Operační systém musí zpracovat tuto výjimku při kompilaci s modelem asynchronní zpracování výjimek. Další informace o modelech zpracování výjimek naleznete v tématu [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md). V takovém případě není obalují volání `CPropertySheet::DoModal` pomocí bloku try-catch C++ ve kterém catch zpracovává všechny výjimky, například `catch (...)`. Tento blok by zpracovat výjimku určené pro operační systém a příčinu nepředvídatelné chování. Zpracování typů specifickou výjimku nebo strukturované zpracování výjimek, kde se výjimka narušení přístupu předává do operačního systému výjimek jazyka C++ však můžete bez obav použít.

Aby nedošlo k vygenerování této první odpovídající výjimce, můžete ručně zaručit, že seznam vlastností má správný [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). Je nutné nastavit následující styly pro seznam vlastností:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Můžete použít následující volitelné styly bez způsobení první odpovídající výjimce:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Všechny další styly Windows zakážete, protože nejsou kompatibilní s vlastností. Toto doporučení se nevztahuje na rozšířené styly. Nastavení těchto standardní stylů odpovídajícím způsobem zaručí, že seznam vlastností není potřeba změnit a zabrání generování první odpovídající výjimce.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet::AddPage](#addpage).

##  <a name="enablestackedtabs"></a>  CPropertySheet::EnableStackedTabs

Označuje, zda zásobníku řádků karet v seznamu vlastností.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parametry

*bStacked*  
Označuje, zda jsou povoleny skládaný karty v seznamu vlastností. Zakázat skládaný řádky značek nastavením *bStacked* na hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení Pokud má více záložek, než se vejde v jediném řádku na šířku vlastností, seznamu vlastností se karty zásobníku z více řádků. Místo překrývání karet použít posouvání karty, volání `EnableStackedTabs` s *bStacked* nastavena na hodnotu FALSE před voláním [DoModal](#domodal) nebo [vytvořit](#create).

Je nutné volat `EnableStackedTabs` při vytváření modální nebo nemodálního seznamu vlastností. Tento styl v začlenit `CPropertySheet`-odvozené třídy, zápis obslužné rutiny zpráv pro WM_CREATE. V přepsaného verzi [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), volání `EnableStackedTabs( FALSE )` před voláním implementaci základní třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>  CPropertySheet::EndDialog

Ukončí seznam vlastností.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parametry

*nEndID*  
Identifikátor, který se použije jako návratovou hodnotu vlastností.

### <a name="remarks"></a>Poznámky

Tato členská funkce je voláno rozhraním, když se stiskne OK, zrušit nebo tlačítko Zavřít. Volání, že tato členská funkce, pokud dojde k události, která by se měla zavřít okno vlastností.

Tato členská funkce používá jenom s modální dialogové okno.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet::PressButton](#pressbutton).

##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex

Získá číslo indexu stránky aktivní okno seznam vlastností a použije je jako parametr pro vrácený číslo indexu `GetPage`.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Indexové číslo aktivní stránkou.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage

Načte aktivní stránkou. okna List vlastností.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní stránkou.

### <a name="remarks"></a>Poznámky

Tuto funkci člena můžete použijte k provedení nějaké akce na aktivní stránce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>  CPropertySheet::GetPage

Vrací ukazatel na zadanou stránku v tomto seznamu vlastností.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parametry

*nPage*  
Index požadovanou stránku začínajícím hodnotou 0. Musí být mezi 0 a menší než počet stránek v seznamu vlastností (včetně).

### <a name="return-value"></a>Návratová hodnota

Ukazatel na odpovídající stránku na *nPage* parametru.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount

Určuje, kolik stránek se nyní v seznamu vlastností.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet stránek v seznamu vlastností.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpageindex"></a>  CPropertySheet::GetPageIndex

Načte index zadané stránky v seznamu vlastností.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*Fyzická_stránka*  
Odkazuje na stránku s indexem nalezen. Nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Indexové číslo stránky.

### <a name="remarks"></a>Poznámky

Například byste použili `GetPageIndex` získat index stránky, chcete-li použít [SetActivePage](#setactivepage) nebo [GetPage](#getpage).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl

Načte ukazatel na něco specifické pro ovládací prvek karty ovládacího prvku karta (to znamená, že k používání některé z rozhraní API v [atributu CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací prvek karty.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce, například pokud chcete přidat rastrových obrázků na každé kartě během inicializace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>  CPropertySheet::m_psh

Strukturu, jejíž členové uložení vlastnosti [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2).

### <a name="remarks"></a>Poznámky

Tuto strukturu použít pro inicializaci vzhled seznamu vlastností po je vytvořena, ale než se zobrazí s [DoModal](#domodal) členskou funkci. Například nastavit *dwSize* člen `m_psh` velikosti chcete mít seznam vlastností.

Další informace o této struktuře, včetně seznamu členů naleznete v tématu PROPSHEETHEADER v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect

Převede jednotkách dialogového okna obdélník na obrazovce jednotky.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lprect –*  
Odkazuje na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje – dialogové okno koordinuje má být převeden.

### <a name="remarks"></a>Poznámky

Jsou dialogového okna jednotky vyjádřený jako aktuální základní jednotku dialogového okna odvozený od průměrné šířku a výšku znaků v písmo použité pro text dialogového okna. Jedna jednotka na vodorovné čtvrtinu jednotku base šířky dialogového okna a jedna jednotka na svislé je 28 jedné jednotky základní výška dialogového okna.

[GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) vrátí informace o velikosti písma systému Windows, můžete ale zadat písmo pro každý seznam vlastností použití stylu DS_SETFONT v souboru definice prostředků. [MapDialogRect](/windows/desktop/api/winuser/nf-winuser-mapdialogrect) funkce Windows, je popsáno v sadě Windows SDK, používá odpovídající písmo pro toto dialogové okno.

`MapDialogRect` Členskou funkci nahrazuje jednotky dialogového okna v *lprect –* s obrazovky jednotek (v pixelech) tak, že obdélník lze použít k vytvoření dialogového nebo umístit ovládací prvek v poli.

##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog

Přepsání pro rozšíření Inicializace seznamu vlastností.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Určuje, zda v aplikaci je nastaven vstupní fokus na některý ovládací prvky v seznamu vlastností. Pokud `OnInitDialog` vrátí nenulovou hodnotu, Windows nastaví zaměření pro vstup na první prvek v seznamu vlastností. Aplikace může vrátit 0 pouze v případě, že je explicitně nastaveno zaměření pro vstup na jeden z ovládacích prvků v seznamu vlastností.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána v reakci na nezavěsíte zprávu. Tato zpráva se pošle do seznamu vlastností během [vytvořit](#create) nebo [DoModal](#domodal) volání, ke kterým dochází, bezprostředně před zobrazením seznamu vlastností je.

Tato členská funkce přepište, pokud je třeba provést zvláštní zpracování při inicializaci vlastností. Přepsané verze nejprve volat základní třídy `OnInitDialog` ale ignorovat jeho návratovou hodnotu. Obvykle se vrací TRUE, z vaší funkce přepsanému členu.

Není nutné položka mapy zpráv pro tuto členskou funkci.

##  <a name="pressbutton"></a>  CPropertySheet::PressButton

Simuluje volba od určeného tlačítka v seznamu vlastností.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parametry

*nButton*  
nButton: identifikuje tlačítko, aby se aktivovala. Tento parametr může být jeden z následujících hodnot:

- PSBTN_BACK klikne na tlačítko Zpět.

- PSBTN_NEXT klikne na tlačítko Další.

- PSBTN_FINISH klikne na tlačítko Dokončit.

- PSBTN_OK klikne na tlačítko OK.

- PSBTN_APPLYNOW zvolí tlačítko použít.

- PSBTN_CANCEL klikne na tlačítko Storno.

- PSBTN_HELP klikne na tlačítko Nápověda.

### <a name="remarks"></a>Poznámky

Zobrazit [PSM_PRESSBUTTON](/windows/desktop/Controls/psm-pressbutton) Další informace o zprávě Windows SDK Pressbutton.

Volání `PressButton` nebudou odesílat [PSN_APPLY](/windows/desktop/Controls/psn-apply) oznámení ze stránky vlastností rozhraní Framework. Chcete-li/nepošle toto oznámení, zavolejte [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>  CPropertySheet::RemovePage

Odebere stránku ze seznamu vlastností a odstraní přidružené okno.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*Fyzická_stránka*  
Odkazuje na stránku, kde odeberou ze seznamu vlastností. Nemůže mít hodnotu NULL.

*nPage*  
Index stránky k odebrání. Musí být mezi 0 a menší než počet stránek v seznamu vlastností (včetně).

### <a name="remarks"></a>Poznámky

[CPropertyPage](../../mfc/reference/cpropertypage-class.md) samotného objektu není zničen až vlastník `CPropertySheet` zavření časového intervalu.

##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage

Mění aktivní stránkou.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*nPage*  
Index stránky lze nastavit. Musí být mezi 0 a menší než počet stránek v seznamu vlastností (včetně).

*Fyzická_stránka*  
Odkazuje na stránku nastavení v seznamu vlastností. Nemůže být NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se úspěšně; aktivuje seznam vlastností jinak 0.

### <a name="remarks"></a>Poznámky

Například použít `SetActivePage` Pokud akce uživatele na jedné stránce by neměly způsobit jinou stránku stane aktivní stránkou.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText

Nastaví text v příkazové tlačítko Dokončit.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*  
Odkazuje na text, který se zobrazí na příkazové tlačítko Dokončit.

### <a name="remarks"></a>Poznámky

Volání `SetFinishText` zobrazit text na tlačítku pro příkaz Dokončit a po dokončení akce na poslední stránce průvodce uživatel skrýt tlačítka Další a zpět.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>  CPropertySheet::SetTitle

Určuje titulek seznam vlastností (text zobrazený v záhlaví okna rámce).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parametry

*nStyle*  
Určuje styl listu název vlastnosti. Styl musí nastavit na 0 nebo jako PSH_PROPTITLE. Pokud je styl nastavená jako PSH_PROPTITLE, slovo "Properties" se zobrazí po textem zadaným jako popisek. Například volání `SetTitle`("Simple", PSH_PROPTITLE) bude mít za následek titulek list vlastností "Jednoduchých vlastností."

*lpszText*  
Odkazuje na text, který se použije jako popisek v záhlaví okna vlastností.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení používá seznam vlastností titulek parametr v konstruktoru list vlastností.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>  CPropertySheet::SetWizardButtons

Povolí nebo zakáže tlačítko Zpět, další nebo dokončit v seznamu vlastností průvodce.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*dwFlags*  
Sada příznaků, které funkce a vzhled tlačítek průvodce přizpůsobit. Tento parametr může být kombinací následujícího:

- Tlačítko Zpět PSWIZB_BACK

- Tlačítko Další PSWIZB_NEXT

- Tlačítko Dokončit PSWIZB_FINISH

- Tlačítko PSWIZB_DISABLEDFINISH zakázané dokončit

### <a name="remarks"></a>Poznámky

Volání `SetWizardButtons` pouze po otevření; dialogového okna nelze volat `SetWizardButtons` před voláním [DoModal](#domodal). Obvykle byste měli volat `SetWizardButtons` z [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Pokud chcete změnit text na tlačítko Dokončit nebo skrýt další a tlačítka zpět po uživatel dokončí Průvodce volání [SetFinishText](#setfinishtext). Všimněte si, že stejné tlačítko sdílí pro dokončení a další. Můžete zobrazit dokončení nebo na tlačítko Další najednou, ale ne obojí.

### <a name="example"></a>Příklad

A `CPropertySheet` má tři stránky vlastností Průvodce: `CStylePage`, `CColorPage`, a `CShapePage`.  Následující fragment kódu ukazuje, jak povolit a zakázat **zpět** a **Další** tlačítka na stránce průvodce vlastností.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>  CPropertySheet::SetWizardMode

Stránky vlastností se zavádí jako průvodce.

```
void SetWizardMode();
```

### <a name="remarks"></a>Poznámky

Klíčovou charakteristikou stránky průvodce vlastností je, že uživatel přejde pomocí další nebo dokončit, zpět a stornovací tlačítka namísto tabulátorů.

Volání `SetWizardMode` před voláním [DoModal](#domodal). Po zavolání `SetWizardMode`, `DoModal` vrátí ID_WIZFINISH (Pokud je uživatel nezavře pomocí tlačítka pro dokončení) nebo IDCANCEL.

`SetWizardMode` Nastaví příznak PSH_WIZARD.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka CMNCTRL1 knihovny MFC](../../visual-cpp-samples.md)  
[Ukázka CMNCTRL2 knihovny MFC](../../visual-cpp-samples.md)  
[Ukázky knihovny MFC PROPDLG](../../visual-cpp-samples.md)  
[Ukázky knihovny MFC SNAPVW](../../visual-cpp-samples.md)  
[CWnd – třída](../../mfc/reference/cwnd-class.md)  
[Graf hierarchie](../../mfc/hierarchy-chart.md)  
