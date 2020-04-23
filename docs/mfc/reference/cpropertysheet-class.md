---
title: CPropertySheet – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: e8ab91b9a6fe76070d79ea2eee2e5765db2e99e3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750969"
---
# <a name="cpropertysheet-class"></a>CPropertySheet – třída

Představuje seznamy vlastností, označované také jako dialogová okna karet.

## <a name="syntax"></a>Syntaxe

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Vytvoří `CPropertySheet` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPropertySheet::AddPage](#addpage)|Přidá stránku do seznamu vlastností.|
|[CPropertySheet::Konstrukce](#construct)|Vytvoří `CPropertySheet` objekt.|
|[CPropertySheet::Vytvořit](#create)|Zobrazí nemodlavý seznam vlastností.|
|[CPropertySheet::DoModální](#domodal)|Zobrazí seznam modálních vlastností.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Označuje, zda seznam vlastností používá skládané nebo rolovací tabulátory.|
|[CPropertySheet::EndDialog](#enddialog)|Ukončí seznam vlastností.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Načte index aktivní stránky seznamu vlastností.|
|[CPropertySheet::GetActivePage](#getactivepage)|Vrátí aktivní objekt stránky.|
|[CPropertySheet::GetPage](#getpage)|Načte ukazatel na zadanou stránku.|
|[CPropertySheet::GetPageCount](#getpagecount)|Načte počet stránek v seznamu vlastností.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Načte index zadané stránky seznamu vlastností.|
|[CPropertySheet::GetTabControl](#gettabcontrol)|Načte ukazatel ovládacího prvku tabulátoru.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Převede jednotky dialogového okna obdélníku na jednotky obrazovky.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Přepsání pro rozšíření inicializace seznamu vlastností.|
|[CPropertySheet::PressButton](#pressbutton)|Simuluje volbu zadaného tlačítka v seznamu vlastností.|
|[CPropertySheet::RemovePage](#removepage)|Odebere stránku z seznamu vlastností.|
|[CPropertySheet::SetActivePage](#setactivepage)|Programově nastaví aktivní objekt stránky.|
|[CPropertySheet:SetFinishText](#setfinishtext)|Nastaví text tlačítka Dokončit.|
|[CPropertySheet:SetTitle](#settitle)|Nastaví titulek seznamu vlastností.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Povolí tlačítka průvodce.|
|[CPropertySheet::SetWizardMode](#setwizardmode)|Povolí režim průvodce.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Struktura WINDOWS [PROPSHEETHEADER.](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) Poskytuje přístup k základním parametrům seznamu vlastností.|

## <a name="remarks"></a>Poznámky

Seznam vlastností se `CPropertySheet` skládá z objektu a jednoho nebo více objektů [CPropertyPage.](../../mfc/reference/cpropertypage-class.md) Rámec zobrazí seznam vlastností jako okno se sadou indexů karet a oblastí, která obsahuje aktuálně vybranou stránku. Uživatel přejde na určitou stránku pomocí příslušné karty.

`CPropertySheet`Poskytuje podporu pro rozšířenou strukturu [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) zavedenou v systémech Windows 98 a Windows NT 2000. Struktura obsahuje další příznaky a členy, které podporují pomocí bitmapy pozadí "vodoznak".

Chcete-li tyto nové obrazy zobrazit automaticky v objektu seznamu vlastností, předejte platné hodnoty bitmapových a paletových obrazů při volání [CPropertySheet::Construct](#construct) nebo [CPropertySheet::CPropertySheet](#cpropertysheet).

I `CPropertySheet` když není odvozen z [CDialog](../../mfc/reference/cdialog-class.md), správa `CPropertySheet` `CDialog` objektu je jako správa objektu. Například vytvoření seznamu vlastností vyžaduje dvoudílnou konstrukci: volání konstruktoru a potom volání [DoModal](#domodal) pro modální seznam vlastností nebo [Vytvořit](#create) pro seznam nemodálnívlastností. `CPropertySheet`má dva typy konstruktorů: [CPropertySheet::Construct](#construct) a [CPropertySheet::CPropertySheet](#cpropertysheet).

Při vytváření `CPropertySheet` objektu mohou některé [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) způsobit výjimku první šance. To vyplývá ze systému se snaží změnit styl seznamu vlastností před vytvořením listu. Chcete-li se této výjimce vyhnout, nastavte `CPropertySheet`při vytváření aplikace následující styly:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Následující styly jsou volitelné a nezpůsobí výjimku první šance:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Ostatní `Window Styles` jsou zakázány a neměli byste je povolit.

Výměna dat mezi `CPropertySheet` objektem a externím objektem je `CDialog` podobná výměně dat s objektem. Důležitým rozdílem je, že nastavení seznamu vlastností jsou `CPropertyPage` obvykle členské proměnné `CPropertySheet` objektů, nikoli samotného objektu.

Můžete vytvořit typ dialogového okna karty s názvem Průvodce, který se skládá z seznamu vlastností s posloupností stránek vlastností, které uživatele provedou kroky operace, například nastavením zařízení nebo vytvořením bulletinu. V dialogovém okně karta typ průvodce stránky vlastností nemají karty a současně je zobrazena pouze jedna stránka vlastností. Namísto tlačítek **OK** a **Použít nyní** má dialogové okno karty typu průvodce také tlačítko **Zpět,** tlačítko **Další** nebo **Dokončit,** tlačítko **Storno** a tlačítko **Nápověda.**

Chcete-li vytvořit dialogové okno typu průvodce, postupujte stejným způsobem, který byste postupovali podle pokynů k vytvoření standardního seznamu vlastností, ale před voláním [domodálního režimu](#domodal)volejte [Příkaz SetWizardMode](#setwizardmode) . Chcete-li povolit tlačítka průvodce, volejte [Tlačítka SetWizardButton](#setwizardbuttons)pomocí příznaků k přizpůsobení jejich funkce a vzhledu. Chcete-li povolit tlačítko **Dokončit,** zavolejte [SetFinishText](#setfinishtext) poté, co uživatel provedl akci na poslední stránce průvodce.

Další informace o použití `CPropertySheet` objektů naleznete v článku [Seznamy vlastností a Stránky vlastností](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="cpropertysheetaddpage"></a><a name="addpage"></a>CPropertySheet::AddPage

Přidá dodanou stránku s záložkou zcela vpravo v seznamu vlastností.

```cpp
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pStránka*<br/>
Odkazuje na stránku, která má být přidána do seznamu vlastností. Nemůže být null.

### <a name="remarks"></a>Poznámky

Přidejte stránky do seznamu vlastností v pořadí zleva doprava, které chcete zobrazit.

`AddPage`přidá objekt [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) `CPropertySheet` do seznamu stránek objektu, ale ve skutečnosti nevytvoří okno stránky. Rozhraní framework odkládá vytvoření okna pro stránku, dokud uživatel vybere tuto stránku.

Když přidáte stránku `AddPage`vlastností `CPropertySheet` pomocí , `CPropertyPage`je nadřazená . Chcete-li získat přístup k seznamu vlastností ze stránky vlastností, zavolejte [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).

Není nutné čekat, až vytvoření okna seznamu `AddPage`vlastností volat . Obvykle budete volat `AddPage` před [voláním DoModal](#domodal) nebo [Vytvořit](#create).

Pokud zavoláte `AddPage` po zobrazení stránky vlastností, řádek karty bude odrážet nově přidanou stránku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

## <a name="cpropertysheetconstruct"></a><a name="construct"></a>CPropertySheet::Konstrukce

Vytvoří `CPropertySheet` objekt.

```cpp
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

*nIDTitulek*<br/>
ID titulku, který má být použit pro seznam vlastností.

*pParentWnd*<br/>
Ukazatel na nadřazené okno seznamu vlastností. Pokud null, nadřazené okno bude hlavní okno aplikace.

*iSelectPage*<br/>
Index stránky, která bude zpočátku nahoře. Výchozí je první stránka přidaná do listu.

*pszCaption pszCaption pszCaption psz*<br/>
Ukazatel na řetězec obsahující titulek, který má být použit pro seznam vlastností. Nemůže být null.

*hbmVodoznačka*<br/>
Zpracovat bitmapu vodoznaku stránky vlastností.

*hpalWatermark*<br/>
Zpracovat paletu bitmapy nebo bitmapy záhlaví vodoznaku.

*hbmHeader*<br/>
Zpracovat bitmapu záhlaví stránky vlastností.

### <a name="remarks"></a>Poznámky

Volání této členské funkce, pokud jeden z konstruktorů třídy již nebyla volána. Například volání `Construct` při deklarování `CPropertySheet` nebo přidělovat pole objektů. V případě polí je nutné `Construct` volat pro každého člena v poli.

Chcete-li zobrazit seznam vlastností, zavolejte [DoModal](#domodal) nebo [Create](#create). Řetězec obsažený v prvním parametru bude umístěn do pruhu titulků pro seznam vlastností.

Obrázky vodoznaků a/nebo záhlaví můžete zobrazit automaticky, `Construct`pokud použijete třetí nebo čtvrtý prototyp y , uvedenývýše, a předáte platné hodnoty pro parametry *hbmWatermark*, *hpalWatermark*a/nebo *hbmHeader.*

### <a name="example"></a>Příklad

Následující příklad ukazuje, za jakých `Construct`okolností byste volat .

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

## <a name="cpropertysheetcpropertysheet"></a><a name="cpropertysheet"></a>CPropertySheet::CPropertySheet

Vytvoří `CPropertySheet` objekt.

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

*nIDTitulek*<br/>
ID titulku, který má být použit pro seznam vlastností.

*pParentWnd*<br/>
Odkazuje na nadřazené okno seznamu vlastností. Pokud null, nadřazené okno bude hlavní okno aplikace.

*iSelectPage*<br/>
Index stránky, která bude zpočátku nahoře. Výchozí je první stránka přidaná do listu.

*pszCaption pszCaption pszCaption psz*<br/>
Odkazuje na řetězec obsahující titulek, který má být použit pro seznam vlastností. Nemůže být null.

*hbmVodoznačka*<br/>
Úchyt k rastrové mapě pozadí seznamu vlastností.

*hpalWatermark*<br/>
Úchyt palety bitmapy nebo bitmapy záhlaví vodoznaku.

*hbmHeader*<br/>
Úchyt k bitmapu záhlaví stránky vlastností.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit seznam vlastností, zavolejte [DoModal](#domodal) nebo [Create](#create). Řetězec obsažený v prvním parametru bude umístěn do pruhu titulků pro seznam vlastností.

Pokud máte více parametrů (například pokud používáte pole), použijte `CPropertySheet` [Construct](#construct) místo .

Obrázky vodoznaků a/nebo záhlaví můžete zobrazit automaticky, `CPropertySheet`pokud použijete třetí nebo čtvrtý prototyp výše a předáte platné hodnoty pro parametry *hbmWatermark*, *hpalWatermark*a/nebo *hbmHeader.*

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

## <a name="cpropertysheetcreate"></a><a name="create"></a>CPropertySheet::Vytvořit

Zobrazí nemodlavý seznam vlastností.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Odkazuje na nadřazené okno. Pokud null, nadřazený je plocha.

*dwStyl*<br/>
Styly oken pro seznam vlastností. Úplný seznam dostupných stylů naleznete v [tématu Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyl*<br/>
Rozšířené styly oken pro seznam vlastností. Úplný seznam dostupných stylů najdete [v tématu Rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je seznam vlastností úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Volání `Create` může být uvnitř konstruktoru, nebo jej můžete volat po vyvolání konstruktoru.

Výchozí styl, vyjádřený předáním -1 jako *dwStyle*, je ve skutečnosti WS_SYSMENU&#124;WS_POPUP&#124;&#124;&#124;WS_CAPTION&#124;&#124;DS_MODALFRAME DS_MODALFRAME&#124;&#124;DS_CONTEXTHELP WS_VISIBLE. Výchozí rozšířený styl okna, vyjádřený předáním 0 jako *dwExStyle*, je ve skutečnosti WS_EX_DLGMODALFRAME.

Členská `Create` funkce se vrátí ihned po vytvoření seznamu vlastností. Chcete-li zničit seznam vlastností, volejte [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).

Nemodální seznamy vlastností `Create` zobrazené s voláním nemají OK, Zrušit, Použít nyní a Nápověda tlačítka jako modální seznamy vlastností. Požadovaná tlačítka musí být vytvořena uživatelem.

Chcete-li zobrazit seznam modálních vlastností, zavolejte místo toho [DoModal.](#domodal)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

## <a name="cpropertysheetdomodal"></a><a name="domodal"></a>CPropertySheet::DoModální

Zobrazí seznam modálních vlastností.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL, pokud byla funkce úspěšná; jinak 0 nebo -1. Pokud byl seznam vlastností vytvořen jako průvodce (viz [SetWizardMode](#setwizardmode)), `DoModal` vrátí buď ID_WIZFINISH nebo IDCANCEL.

### <a name="remarks"></a>Poznámky

Vrácená hodnota odpovídá ID ovládacího prvku, který uzavřel seznam vlastností. Po vrácení této funkce budou zničena okna odpovídající seznamu vlastností a všechny stránky. Samotné objekty budou stále existovat. Obvykle načtete data z objektů [CPropertyPage](../../mfc/reference/cpropertypage-class.md) po `DoModal` vrátí IDOK.

Chcete-li zobrazit nemodlavý seznam vlastností, zavolejte místo toho [vytvořit.](#create)

Když je stránka vlastností vytvořena z odpovídajícího prostředku dialogu, může způsobit výjimku první šance. Výsledkem je změna stylu prostředku dialogu na požadovaný styl před vytvořením stránky. Vzhledem k tomu, že prostředky jsou obecně jen pro čtení, to způsobí výjimku. Systém zpracovává výjimku a vytvoří kopii upraveného prostředku. Výjimka první šance proto může být ignorována.

> [!NOTE]
> Tato výjimka musí být zpracována operačním systémem, pokud se stavusizujete s modelem zpracování asynchronní výjimky. Další informace o modelech zpracování výjimek naleznete [v tématu /EH (Model zpracování výjimek).](../../build/reference/eh-exception-handling-model.md) V tomto případě nezalamujte volání `CPropertySheet::DoModal` s c++ try-catch bloku, ve kterém catch `catch (...)`zpracovává všechny výjimky, například . Tento blok by zpracovat výjimku určenou pro operační systém a způsobit nepředvídatelné chování. Můžete však bezpečně použít zpracování výjimek jazyka C++ s určitými typy výjimek nebo strukturovaným zpracováním výjimek, kde je výjimka narušení přístupu předána operačnímu systému.

Chcete-li se vyhnout generování této výjimky první šance, můžete ručně zaručit, že seznam vlastností má správné [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). Pro seznam vlastností je třeba nastavit následující styly:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Můžete použít následující volitelné styly, aniž by došlo k první šanci výjimku:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Zakažte všechny ostatní styly systému Windows, protože nejsou kompatibilní s listy vlastností. Tato rada se nevztahuje na rozšířené styly. Nastavení těchto standardních stylů odpovídajícím způsobem zaručí, že seznam vlastností nemusí být změněn a zabrání generování výjimky první šance.

### <a name="example"></a>Příklad

Viz příklad [pro CPropertySheet::AddPage](#addpage).

## <a name="cpropertysheetenablestackedtabs"></a><a name="enablestackedtabs"></a>CPropertySheet::EnableStackedTabs

Označuje, zda se mají řádky tabulátorů skládat do seznamu vlastností.

```cpp
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parametry

*bStohovaná*<br/>
Označuje, zda jsou v seznamu vlastností povoleny skládané karty. Zakažte skládané řádky tagů nastavením *bStacked* to FALSE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, pokud seznam vlastností obsahuje více karet, než se vejde do jednoho řádku v šířce seznamu vlastností, budou tabulátory stohovat ve více řádcích. Chcete-li místo stohování karet použít `EnableStackedTabs` rolovací karty, zavolejte s *bStacked nastavenou* na HODNOTU FALSE před [voláním DoModal](#domodal) nebo [Create](#create).

Musíte volat `EnableStackedTabs` při vytváření modální nebo nemodální seznam vlastností. Chcete-li tento `CPropertySheet`styl začlenit do odvozené třídy, napište obslužnou rutinu zprávy pro WM_CREATE. V přepsané verzi [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate) `EnableStackedTabs( FALSE )` , volání před voláním implementace základní třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

## <a name="cpropertysheetenddialog"></a><a name="enddialog"></a>CPropertySheet::EndDialog

Ukončí seznam vlastností.

```cpp
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parametry

*nEndID*<br/>
Identifikátor, který má být použit jako vrácená hodnota seznamu vlastností.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rámci při stisknutí tlačítka OK, Cancel nebo Close. Volání této členské funkce, pokud dojde k události, která by měla zavřít seznam vlastností.

Tato členská funkce se používá pouze s modálním dialogovým oknem.

### <a name="example"></a>Příklad

Viz příklad [cPropertySheet::PressButton](#pressbutton).

## <a name="cpropertysheetgetactiveindex"></a><a name="getactiveindex"></a>CPropertySheet::GetActiveIndex

Získá číslo indexu aktivní stránky okna seznamu vlastností a potom použije vrácené číslo indexu jako parametr pro `GetPage`.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo indexu aktivní stránky.

### <a name="example"></a>Příklad

Viz příklad [pro CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetgetactivepage"></a><a name="getactivepage"></a>CPropertySheet::GetActivePage

Načte aktivní stránku okna seznamu vlastností.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní stránku.

### <a name="remarks"></a>Poznámky

Tato členská funkce slouží k provedení určité akce na aktivní stránce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

## <a name="cpropertysheetgetpage"></a><a name="getpage"></a>CPropertySheet::GetPage

Vrátí ukazatel na zadanou stránku v tomto seznamu vlastností.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parametry

*nStránka*<br/>
Index požadované stránky začínající na 0. Musí být mezi 0 a jedním menší než počet stránek v seznamu vlastností včetně.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na stránku odpovídající parametru *nPage.*

### <a name="example"></a>Příklad

Viz příklad [cPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpagecount"></a><a name="getpagecount"></a>CPropertySheet::GetPageCount

Určuje počet stránek, které jsou aktuálně v seznamu vlastností.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet stránek v seznamu vlastností.

### <a name="example"></a>Příklad

Viz příklad [cPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpageindex"></a><a name="getpageindex"></a>CPropertySheet::GetPageIndex

Načte číslo indexu zadané stránky v seznamu vlastností.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pStránka*<br/>
Odkazuje na stránku s indexem, který se nachází. Nemůže být null.

### <a name="return-value"></a>Návratová hodnota

Číslo indexu stránky.

### <a name="remarks"></a>Poznámky

Například byste použít `GetPageIndex` k získání indexu stránky, aby bylo možné použít [SetActivePage](#setactivepage) nebo [GetPage](#getpage).

### <a name="example"></a>Příklad

Viz příklad [pro CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetgettabcontrol"></a><a name="gettabcontrol"></a>CPropertySheet::GetTabControl

Načte ukazatel na ovládací prvek tabulátoru, aby bylo možné provést něco specifického pro ovládací prvek tabulátoru (to znamená použít libovolné z těchto api v [klávesách CTabCtrl).](../../mfc/reference/ctabctrl-class.md)

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací prvek tabulátoru.

### <a name="remarks"></a>Poznámky

Například volání této členské funkce, pokud chcete přidat bitmapy na každé z karet během inicializace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

## <a name="cpropertysheetm_psh"></a><a name="m_psh"></a>CPropertySheet::m_psh

Struktura, jejíž členové ukládají charakteristiky [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2).

### <a name="remarks"></a>Poznámky

Pomocí této struktury inicializovat vzhled seznamu vlastností po jeho vytvoření, ale před zobrazením s [DoModal](#domodal) členské funkce. Například nastavte člen *dwSize* `m_psh` na velikost, kterou má mít seznam vlastností.

Další informace o této struktuře, včetně výpisu jejích členů, naleznete v tématu PROPSHEETHEADER v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

## <a name="cpropertysheetmapdialogrect"></a><a name="mapdialogrect"></a>CPropertySheet::MapDialogRect

Převede jednotky dialogového okna obdélníku na jednotky obrazovky.

```cpp
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje dialogové okno souřadnice, které mají být převedeny.

### <a name="remarks"></a>Poznámky

Jednotky dialogového okna jsou uvedeny jako aktuální základní jednotka dialogového okna odvozená od průměrné šířky a výšky znaků v písmu použitém pro text dialogového okna. Jedna vodorovná jednotka je jedna čtvrtina jednotky základní šířky dialogového okna a jedna svislá jednotka je jedna osmina základní výškové jednotky dialogového okna.

Funkce Systému Windows [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) vrátí informace o velikosti systémového písma, ale pokud použijete styl DS_SETFONT v souboru definice prostředku, můžete pro každý seznam vlastností určit jiné písmo. Funkce Systému Windows [MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) popsaná v sadě Windows SDK používá příslušné písmo pro toto dialogové okno.

Členská `MapDialogRect` funkce nahradí jednotky dialogového okna v *lpRect* jednotkami obrazovky (pixely), takže obdélník lze použít k vytvoření dialogového okna nebo umístění ovládacího prvku v poli.

## <a name="cpropertysheetoninitdialog"></a><a name="oninitdialog"></a>CPropertySheet::OnInitDialog

Přepíše pro zvětšení inicializace seznamu vlastností.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Určuje, zda aplikace nastavila vstupní fokus na jeden z ovládacích prvků v seznamu vlastností. Pokud `OnInitDialog` vrátí nenulovou, systém Windows nastaví vstupní fokus na první ovládací prvek v seznamu vlastností. Aplikace může vrátit 0 pouze v případě, že explicitně nastavila vstupní fokus na jeden z ovládacích prvků v seznamu vlastností.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána jako odpověď na zprávu WM_INITDIALOG. Tato zpráva je odeslána do seznamu vlastností během [create](#create) nebo [DoModal](#domodal) volání, ke kterým dochází bezprostředně před zobrazením seznamu vlastností.

Přepište tuto členovou funkci, pokud potřebujete provést speciální zpracování při inicializování seznamu vlastností. V přepsané verzi nejprve volat `OnInitDialog` základní třídy, ale ignorovat jeho vrácená hodnota. Z potlačené členské funkce obvykle vrátíte hodnotu PRAVDA.

Pro tuto členskou funkci nepotřebujete položku mapy zpráv.

## <a name="cpropertysheetpressbutton"></a><a name="pressbutton"></a>CPropertySheet::PressButton

Simuluje volbu zadaného tlačítka v seznamu vlastností.

```cpp
void PressButton(int nButton);
```

### <a name="parameters"></a>Parametry

*nTlačítko*<br/>
nButton : Identifikuje stisknuté tlačítko. Tento parametr může být jedna z následujících hodnot:

- PSBTN_BACK Zvolte tlačítko Zpět.

- PSBTN_NEXT vybere tlačítko Další.

- PSBTN_FINISH Vybere tlačítko Dokončit.

- PSBTN_OK Zvolte tlačítko OK.

- PSBTN_APPLYNOW zvolí tlačítko Použít nyní.

- PSBTN_CANCEL Vybere tlačítko Storno.

- PSBTN_HELP Vybere tlačítko Nápověda.

### <a name="remarks"></a>Poznámky

Další informace o tiskové zprávě sady Windows SDK naleznete v [PSM_PRESSBUTTON.](/windows/win32/Controls/psm-pressbutton)

Volání `PressButton` neodešle [oznámení PSN_APPLY](/windows/win32/Controls/psn-apply) ze stránky vlastností do rámce. Chcete-li odeslat toto oznámení, zavolejte [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

## <a name="cpropertysheetremovepage"></a><a name="removepage"></a>CPropertySheet::RemovePage

Odebere stránku z seznamu vlastností a zničí přidružené okno.

```cpp
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*pStránka*<br/>
Odkazuje na stránku, která má být odebrána z seznamu vlastností. Nemůže být null.

*nStránka*<br/>
Index stránky, která má být odebrána. Musí být mezi 0 a jedním menší než počet stránek v seznamu vlastností včetně.

### <a name="remarks"></a>Poznámky

Samotný objekt [CPropertyPage](../../mfc/reference/cpropertypage-class.md) není zničen, dokud `CPropertySheet` není vlastník okna uzavřen.

## <a name="cpropertysheetsetactivepage"></a><a name="setactivepage"></a>CPropertySheet::SetActivePage

Změní aktivní stránku.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*nStránka*<br/>
Index stránky nastavit. Musí být mezi 0 a jedním menší než počet stránek v seznamu vlastností včetně.

*pStránka*<br/>
Odkazuje na stránku, kterou chcete nastavit v seznamu vlastností. Nemůže být null.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je seznam vlastností úspěšně aktivován; jinak 0.

### <a name="remarks"></a>Poznámky

Použijte `SetActivePage` například, pokud akce uživatele na jedné stránce by měla způsobit, že se aktivní stránkou stane jiná stránka.

### <a name="example"></a>Příklad

Viz příklad [pro CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetsetfinishtext"></a><a name="setfinishtext"></a>CPropertySheet:SetFinishText

Nastaví text v příkazovém tlačítku Dokončit.

```cpp
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Odkazuje na text, který se má zobrazit na příkazovém tlačítku Dokončit.

### <a name="remarks"></a>Poznámky

Volání `SetFinishText` zobrazítext na příkazovém tlačítku Dokončit a skryje tlačítko Další a Zpět po dokončení akce uživatele na poslední stránce průvodce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsettitle"></a><a name="settitle"></a>CPropertySheet:SetTitle

Určuje titulek seznamu vlastností (text zobrazený v záhlaví okna rámečku).

```cpp
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parametry

*nStyl*<br/>
Určuje styl názvu seznamu vlastností. Styl musí být zadán na 0 nebo jako PSH_PROPTITLE. Pokud je styl nastaven jako PSH_PROPTITLE, za textem určeným jako titulek se zobrazí slovo "Vlastnosti". Například volání `SetTitle`("Jednoduché", PSH_PROPTITLE) bude mít za následek popisek seznamu vlastností "Jednoduché vlastnosti."

*lpszText*<br/>
Odkazuje na text, který má být použit jako titulek v záhlaví seznamu vlastností.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení používá seznam vlastností parametr titulku v konstruktoru seznamu vlastností.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

## <a name="cpropertysheetsetwizardbuttons"></a><a name="setwizardbuttons"></a>CPropertySheet::SetWizardButtons

Povolí nebo zakáže tlačítko Zpět, Další nebo Dokončit v seznamu vlastností průvodce.

```cpp
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Sada příznaků, které přizpůsobují funkci a vzhled tlačítek průvodce. Tento parametr může být kombinací následujících hodnot:

- PSWIZB_BACK tlačítko Zpět

- tlačítko PSWIZB_NEXT Další

- tlačítko dokončit PSWIZB_FINISH

- PSWIZB_DISABLEDFINISH Zakázané dokončení, tlačítko

### <a name="remarks"></a>Poznámky

Volání `SetWizardButtons` pouze po otevření dialogového okna; před voláním `SetWizardButtons` [domodálního volání](#domodal)nelze volat. Obvykle byste měli `SetWizardButtons` volat z [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Pokud chcete změnit text na tlačítku Dokončit nebo skrýt tlačítka Další a Zpět po dokončení průvodce uživatelem, zavolejte [SetFinishText](#setfinishtext). Všimněte si, že stejné tlačítko je sdíleno pro dokončení a další. Můžete zobrazit tlačítko Dokončit nebo Další najednou, ale ne obojí.

### <a name="example"></a>Příklad

A `CPropertySheet` má tři stránky `CStylePage` `CColorPage`vlastností `CShapePage`průvodce: , a .  Následující fragment kódu ukazuje, jak povolit a zakázat tlačítka **Zpět** a **Další** na stránce vlastností průvodce.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsetwizardmode"></a><a name="setwizardmode"></a>CPropertySheet::SetWizardMode

Vytvoří stránku vlastností jako průvodce.

```cpp
void SetWizardMode();
```

### <a name="remarks"></a>Poznámky

Klíčovou vlastností stránky vlastností průvodce je, že uživatel naviguje pomocí tlačítek Další nebo Dokončit, Zpět a Storno místo karet.

Volání `SetWizardMode` před [voláním DoModal](#domodal). Po volání `SetWizardMode` `DoModal` vrátí buď ID_WIZFINISH (pokud se uživatel zavře tlačítkem Dokončit) nebo IDCANCEL.

`SetWizardMode`nastaví příznak PSH_WIZARD.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Vzorek mfc PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
