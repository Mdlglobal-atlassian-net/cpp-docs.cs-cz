---
title: CPropertySheet – – třída
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
ms.openlocfilehash: 23d17aee2aacbc1484c0f3e181bc824546ab49a2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502827"
---
# <a name="cpropertysheet-class"></a>CPropertySheet – – třída

Představuje seznamy vlastností, označované také jako dialogová okna karty.

## <a name="syntax"></a>Syntaxe

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|`CPropertySheet` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPropertySheet::AddPage](#addpage)|Přidá stránku do seznamu vlastností.|
|[CPropertySheet::Construct](#construct)|`CPropertySheet` Vytvoří objekt.|
|[CPropertySheet::Create](#create)|Zobrazí nemodální seznam vlastností.|
|[CPropertySheet::DoModal](#domodal)|Zobrazí modální seznam vlastností.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Označuje, zda seznam vlastností používá karty skládaného nebo posunutí.|
|[CPropertySheet::EndDialog](#enddialog)|Ukončí seznam vlastností.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Načte index aktivní stránky seznamu vlastností.|
|[CPropertySheet::GetActivePage](#getactivepage)|Vrátí objekt aktivní stránky.|
|[CPropertySheet::GetPage](#getpage)|Načte ukazatel na určenou stránku.|
|[CPropertySheet::GetPageCount](#getpagecount)|Načte počet stránek v seznamu vlastností.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Načte index zadané stránky seznamu vlastností.|
|[CPropertySheet::GetTabControl](#gettabcontrol)|Načte ukazatel na ovládací prvek karta.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Převede jednotky dialogového okna obdélníku na jednotky obrazovky.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Přepsání pro rozšíření Inicializace seznamu vlastností.|
|[CPropertySheet::PressButton](#pressbutton)|Simuluje výběr zadaného tlačítka v seznamu vlastností.|
|[CPropertySheet::RemovePage](#removepage)|Odebere stránku ze seznamu vlastností.|
|[CPropertySheet::SetActivePage](#setactivepage)|Programově nastavuje objekt aktivní stránky.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Nastaví text pro tlačítko Dokončit.|
|[CPropertySheet –:: SetTitle](#settitle)|Nastaví titulek seznamu vlastností.|
|[CPropertySheet –:: SetWizardButtons](#setwizardbuttons)|Povolí tlačítka průvodce.|
|[CPropertySheet::SetWizardMode](#setwizardmode)|Povolí režim průvodce.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Struktura [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) systému Windows. Poskytuje přístup k základním parametrům seznamu vlastností.|

## <a name="remarks"></a>Poznámky

Seznam vlastností se skládá z `CPropertySheet` objektu a jednoho nebo více objektů [CPropertyPage –](../../mfc/reference/cpropertypage-class.md) . Rozhraní zobrazí seznam vlastností jako okno se sadou indexů karet a oblastí, která obsahuje aktuálně vybranou stránku. Uživatel přejde na konkrétní stránku pomocí příslušné karty.

`CPropertySheet`poskytuje podporu pro rozšířenou strukturu [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) představenou ve Windows 98 a windows NT 2000. Struktura obsahuje další příznaky a členy, které podporují použití rastrového obrázku pozadí vodoznaku.

Chcete-li tyto nové obrázky zobrazit automaticky v objektu seznamu vlastností, předejte platné hodnoty imagí rastrového obrázku a palety ve volání metody [CPropertySheet –:: Construct](#construct) nebo [CPropertySheet –:: CPropertySheet –](#cpropertysheet).

I když `CPropertySheet` není odvozen z [CDialog](../../mfc/reference/cdialog-class.md), Správa `CPropertySheet` objektu je jako správa `CDialog` objektu. Například vytvoření seznamu vlastností vyžaduje konstrukci dvou částí: volejte konstruktor a potom zavolejte [DoModal](#domodal) pro modální seznam vlastností nebo [vytvořte](#create) pro nemodální seznam vlastností. `CPropertySheet`má dva typy konstruktorů: [CPropertySheet –:: Construct](#construct) a [CPropertySheet –:: CPropertySheet –](#cpropertysheet).

Při vytváření `CPropertySheet` objektu mohou některé [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) způsobit výskyt výjimky s první pravděpodobností. Výsledkem je systém, který se pokouší změnit styl seznamu vlastností před vytvořením listu. Chcete-li se této výjimce vyhnout, nezapomeňte při vytváření `CPropertySheet`těchto stylů nastavit následující styly:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Následující styly jsou volitelné a nezpůsobí se tím první výjimka:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Jakékoli jiné `Window Styles` jsou zakázané a neměli byste je povolit.

Výměna dat mezi `CPropertySheet` objektem a externím objektem je podobná výměně dat `CDialog` s objektem. Důležitým rozdílem je, že nastavení seznamu vlastností jsou obvykle členské proměnné `CPropertyPage` objektů namísto `CPropertySheet` samotného objektu.

Můžete vytvořit typ dialogového okna karta s názvem průvodce, který se skládá ze seznamu vlastností se sekvencí stránek vlastností, které provedou uživatele prostřednictvím kroků operace, jako je například nastavení zařízení nebo vytvoření bulletinu. V dialogovém okně Průvodce – typ karty stránky vlastností nejsou karty a v jednu chvíli je viditelná jenom jedna stránka vlastností. Místo toho, abyste měli tlačítka **OK** a **použít nyní** , má dialogové okno Karta typ průvodce tlačítko **zpět** , tlačítko **Další** nebo **Dokončit** , tlačítko **Storno** a tlačítko **help** .

Chcete-li vytvořit dialogové okno typu průvodce, postupujte podle kroků, které byste měli provést, abyste vytvořili standardní seznam vlastností, ale zavolejte [SetWizardMode](#setwizardmode) před voláním [DoModal](#domodal). Chcete-li povolit tlačítka průvodce, zavolejte [SetWizardButtons](#setwizardbuttons)pomocí příznaků k přizpůsobení jejich funkcí a vzhledu. Chcete-li povolit tlačítko **Dokončit** , zavolejte [SetFinishText](#setfinishtext) poté, co uživatel provedl akci na poslední stránce průvodce.

Další informace o použití `CPropertySheet` objektů naleznete na stránce vlastností článku a na [stránkách vlastností](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs. h

##  <a name="addpage"></a>CPropertySheet –:: AddPage

Přidá zadanou stránku pomocí karty vpravo v seznamu vlastností.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
Odkazuje na stránku, která má být přidána do seznamu vlastností. Nemůže mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Do seznamu vlastností v levém pořadí přidejte stránky, které chcete zobrazit.

`AddPage`Přidá objekt [CPropertyPage –](../../mfc/reference/cpropertypage-class.md#cpropertypage) do `CPropertySheet` seznamu stránek objektu, ale ve skutečnosti nevytvoří okno pro stránku. Rozhraní odloží vytvoření okna pro stránku, dokud uživatel nevybere tuto stránku.

Když přidáte stránku vlastností pomocí `AddPage` `CPropertySheet` , `CPropertyPage`je nadřazeným prvkem. Chcete-li získat přístup k seznamu vlastností ze stránky vlastností, zavolejte [CWnd:: GetParent](../../mfc/reference/cwnd-class.md#getparent).

Pro volání `AddPage`není nutné čekat na vytvoření okna seznamu vlastností. Obvykle budete volat `AddPage` před voláním [DoModal](#domodal) nebo [Create](#create).

Pokud voláte `AddPage` po zobrazení stránky vlastností, řádek karty bude odrážet nově přidanou stránku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>CPropertySheet –:: Construct

`CPropertySheet` Vytvoří objekt.

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

*nIDCaption*<br/>
ID titulku, který se má použít pro seznam vlastností

*pParentWnd*<br/>
Ukazatel na nadřazené okno seznamu vlastností. Pokud má hodnotu NULL, nadřazené okno bude hlavním oknem aplikace.

*iSelectPage*<br/>
Index stránky, která bude zpočátku nahoře Výchozí je první stránka přidaná do listu.

*pszCaption*<br/>
Ukazatel na řetězec obsahující titulek, který má být použit pro seznam vlastností. Nemůže mít hodnotu NULL.

*hbmWatermark*<br/>
Pořídí rastrový obrázek vodoznaku stránky vlastností.

*hpalWatermark*<br/>
Pořídí paletu rastrového obrázku vodoznaku a/nebo rastrového obrázku záhlaví.

*hbmHeader*<br/>
Zařídí se hlavičkou rastrového obrázku stránky vlastností.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci volejte, pokud některý z konstruktorů třídy již nebyl volán. Například volejte `Construct` , pokud deklarujete nebo přidělíte `CPropertySheet` pole objektů. V případě polí je nutné volat `Construct` pro každého člena v poli.

Chcete-li zobrazit seznam vlastností, zavolejte [DoModal](#domodal) nebo [vytvořte](#create). Řetězec obsažený v prvním parametru bude umístěn v záhlaví seznamu vlastností.

Obrázky vodoznaku a/nebo hlavičky můžete zobrazit `Construct`automaticky, pokud použijete třetí nebo čtvrtý prototypy, které jsou uvedené výše, a předáte platné hodnoty pro parametry *hbmWatermark*, *hpalWatermark*a/nebo *hbmHeader* .

### <a name="example"></a>Příklad

Následující příklad ukazuje, za jakých okolností byste volali `Construct`.

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

##  <a name="cpropertysheet"></a>CPropertySheet –:: CPropertySheet –

`CPropertySheet` Vytvoří objekt.

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

*nIDCaption*<br/>
ID titulku, který se má použít pro seznam vlastností

*pParentWnd*<br/>
Odkazuje na nadřazené okno seznamu vlastností. Pokud má hodnotu NULL, nadřazené okno bude hlavním oknem aplikace.

*iSelectPage*<br/>
Index stránky, která bude zpočátku nahoře Výchozí je první stránka přidaná do listu.

*pszCaption*<br/>
Odkazuje na řetězec obsahující titulek, který se má použít pro seznam vlastností. Nemůže mít hodnotu NULL.

*hbmWatermark*<br/>
Popisovač rastrového obrázku pozadí seznamu vlastností.

*hpalWatermark*<br/>
Popisovač palety rastrového obrázku vodoznaku nebo rastrového obrázku záhlaví.

*hbmHeader*<br/>
Popisovač rastrového obrázku stránky vlastností.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit seznam vlastností, zavolejte [DoModal](#domodal) nebo [vytvořte](#create). Řetězec obsažený v prvním parametru bude umístěn v záhlaví seznamu vlastností.

Máte-li více parametrů (například pokud používáte pole), použijte spíše [konstrukce](#construct) namísto `CPropertySheet`.

Obrázky vodoznaku a/nebo hlavičky můžete zobrazit automaticky, pokud používáte `CPropertySheet`třetí nebo čtvrtý prototypy, výše a předáte platné hodnoty pro parametry *hbmWatermark*, *hpalWatermark*a/nebo *hbmHeader* .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>CPropertySheet –:: Create

Zobrazí nemodální seznam vlastností.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Odkazuje na nadřazené okno. Pokud má hodnotu NULL, nadřazený objekt je plocha.

*dwStyle*<br/>
Styly oken pro seznam vlastností Úplný seznam dostupných stylů naleznete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*<br/>
Rozšířené styly oken pro seznam vlastností Úplný seznam dostupných stylů najdete v tématu [Rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je seznam vlastností úspěšně vytvořen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Volání `Create` může být uvnitř konstruktoru nebo může být voláno po vyvolání konstruktoru.

Výchozí styl vyjádřený předáním-1 jako *dwStyle*je vlastně WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE. Výchozí rozšířený styl okna vyjádřený předáním 0 jako *dwExStyle*je vlastně WS_EX_DLGMODALFRAME.

Členská funkce se `Create` vrátí hned po vytvoření seznamu vlastností. Chcete-li zničit seznam vlastností, zavolejte [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow).

Nemodální seznamy vlastností zobrazené s voláním `Create` nejsou k dispozici tlačítka OK, zrušit, použít nyní a pomáhat jako modální seznamy vlastností. Požadovaná tlačítka musí uživatel vytvořit.

Chcete-li zobrazit modální seznam vlastností, zavolejte místo toho [DoModal](#domodal) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>  CPropertySheet::DoModal

Zobrazí modální seznam vlastností.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL, pokud byla funkce úspěšná; v opačném případě 0 nebo-1. Pokud seznam vlastností byl vytvořen jako průvodce (viz [SetWizardMode](#setwizardmode)), vrátí buď ID_WIZFINISH `DoModal` , nebo IDCANCEL.

### <a name="remarks"></a>Poznámky

Vrácená hodnota odpovídá ID ovládacího prvku, který zavřel seznam vlastností. Až tato funkce vrátí, okna odpovídající seznamu vlastností a všem stránkám budou zničeny. Objekty, které jsou v takovém případě, stále existují. Data se obvykle načítají z objektů [CPropertyPage –](../../mfc/reference/cpropertypage-class.md) po `DoModal` návratu IDOK.

Chcete-li zobrazit nemodální seznam vlastností, zavolejte místo toho příkaz [Create](#create) .

Když je vytvořena stránka vlastností z odpovídajícího prostředku dialogu, může to způsobit výjimku s první pravděpodobností. Výsledkem je stránka vlastností, která mění styl prostředku dialogového okna na požadovaný styl před vytvořením stránky. Vzhledem k tomu, že prostředky jsou obecně jen pro čtení, způsobuje výjimku. Systém zpracuje výjimku a vytvoří kopii upraveného prostředku. Výjimku první pravděpodobnost lze proto ignorovat.

> [!NOTE]
>  Tato výjimka musí být zpracována operačním systémem, pokud kompilujete s modelem zpracování asynchronních výjimek. Další informace o modelech zpracování výjimek naleznete v tématu [/EH (model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md). V takovém případě nezalomí volání do `CPropertySheet::DoModal` bloku C++ try-catch, ve kterém catch zpracovává všechny výjimky `catch (...)`, například. Tento blok by zpracovával výjimku, která je určená pro operační systém, a způsobuje nepředvídatelné chování. Můžete však bezpečně použít C++ zpracování výjimek s konkrétními typy výjimek nebo strukturované zpracování výjimek, kde je výjimka narušení přístupu předána do operačního systému.

Chcete-li se vyhnout generování této výjimky s první pravděpodobností, můžete ručně zaručit, že seznam vlastností má správné [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). Pro seznam vlastností musíte nastavit následující styly:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Můžete použít následující volitelné styly, aniž by došlo k výjimce s první pravděpodobností:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Zakáže všechny ostatní styly Windows, protože nejsou kompatibilní s seznamy vlastností. Tato doporučení neplatí pro rozšířené styly. Pokud tyto standardní styly nastavíte správně, bude zárukou, že seznam vlastností nebude nutné upravovat a vyhněte se generování první výjimky.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet –:: addPage](#addpage).

##  <a name="enablestackedtabs"></a>CPropertySheet –:: EnableStackedTabs

Označuje, zda se mají v seznamu vlastností skládat řádky karet.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parametry

*bStacked*<br/>
Určuje, zda jsou v seznamu vlastností povoleny skládané karty. Zakažte skládané řádky značek nastavením *bStacked* na hodnotu false.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, pokud má seznam vlastností více karet, než se vejde do jednoho řádku na šířku seznamu vlastností, karty budou vyvrstveny ve více řádcích. Chcete-li použít tabulátory pro posouvání místo skládání karet `EnableStackedTabs` , zavolejte *bStacked* nastaven na false před voláním [DoModal](#domodal) nebo [Create](#create).

Je nutné zavolat `EnableStackedTabs` při vytváření modálního nebo nemodálního seznamu vlastností. Chcete `CPropertySheet`-li začlenit tento styl do odvozené třídy, zapište obslužnou rutinu zprávy pro WM_CREATE. V přepsané verzi [CWnd:: Create](../../mfc/reference/cwnd-class.md#oncreate)volejte `EnableStackedTabs( FALSE )` před voláním implementace základní třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>  CPropertySheet::EndDialog

Ukončí seznam vlastností.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parametry

*nEndID*<br/>
Identifikátor, který má být použit jako návratová hodnota seznamu vlastností.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním, když je stisknuto tlačítko OK, zrušit nebo zavřít. Pokud dojde k události, která by měla zavřít seznam vlastností, zavolejte tuto členskou funkci.

Tato členská funkce se používá jenom s modálním dialogovým oknem.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet –::P ressbutton](#pressbutton).

##  <a name="getactiveindex"></a>CPropertySheet –:: GetActiveIndex

Získá číslo indexu aktivní stránky okna seznamu vlastností a potom použije vrácené číslo indexu jako parametr pro `GetPage`.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo indexu aktivní stránky.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet –:: GetActivePage](#getactivepage).

##  <a name="getactivepage"></a>CPropertySheet –:: GetActivePage

Načte aktivní stránku okna seznamu vlastností.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní stránku.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte k provedení některé akce na aktivní stránce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>CPropertySheet –:: GetPage

Vrátí ukazatel na určenou stránku v tomto seznamu vlastností.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
Index požadované stránky, počínaje hodnotou 0 Hodnota musí být mezi 0 a menší než počet stránek v seznamu vlastností (včetně).

### <a name="return-value"></a>Návratová hodnota

Ukazatel na stránku odpovídající parametru *nPage* .

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertyPage –:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount

Určuje počet stránek, které jsou aktuálně v seznamu vlastností.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet stránek v seznamu vlastností.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertyPage –:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpageindex"></a>CPropertySheet –:: GetPageIndex

Načte číslo indexu zadané stránky v seznamu vlastností.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
Odkazuje na stránku s indexem, který se má najít. Nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Číslo indexu stránky

### <a name="remarks"></a>Poznámky

Například můžete použít `GetPageIndex` k získání indexu stránky, aby bylo možné použít [SetActivePage](#setactivepage) nebo GetPage. [](#getpage)

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet –:: GetActivePage](#getactivepage).

##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl

Načte ukazatel na ovládací prvek karta a provede něco konkrétního ovládacího prvku karta (to znamená, aby bylo možné použít kterékoli rozhraní API v [atributu CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací prvek karta.

### <a name="remarks"></a>Poznámky

Například volejte tuto členskou funkci, pokud chcete přidat rastrové obrázky na každou kartu během inicializace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>  CPropertySheet::m_psh

Struktura, jejíž členové ukládají vlastnosti [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2).

### <a name="remarks"></a>Poznámky

Tuto strukturu použijte k inicializaci vzhledu seznamu vlastností po jeho vytvoření, ale před jeho zobrazením s členskou funkcí [DoModal](#domodal) . Například nastavte člena `m_psh` *nenulového dwSize funkci* na velikost, kterou má mít seznam vlastností.

Další informace o této struktuře, včetně výpisu jejích členů, najdete v tématu PROPSHEETHEADER v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>CPropertySheet –:: MapDialogRect

Převede jednotky dialogového okna obdélníku na jednotky obrazovky.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) nebo objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který obsahuje souřadnice dialogových oken, které mají být převedeny.

### <a name="remarks"></a>Poznámky

Jednotky dialogového okna jsou uvedeny ve smyslu aktuální základní jednotky dialogového okna odvozené od průměrné šířky a výšky znaků v písmu použitém pro text dialogového okna. Jedna vodorovná jednotka je jednou ze čtvrté jednotky základní šířky dialogového okna a jedna svislá jednotka je o jednu osmina jednotky základní výšky dialogového okna.

Funkce [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) systému Windows vrací informace o velikosti systémového písma, ale pro každý seznam vlastností lze zadat jiné písmo, pokud použijete styl DS_SETFONT v souboru definice prostředků. Funkce [MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) systému Windows, která je popsána v Windows SDK, používá vhodná písma pro toto dialogové okno.

Členská funkce nahradí jednotky dialogového okna v lpRect s jednotkami obrazovky (pixely) tak, aby obdélník mohl být použit k vytvoření dialogového okna nebo umístění ovládacího prvku v rámci pole. `MapDialogRect`

##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog

Přepsání pro rozšíření Inicializace seznamu vlastností.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Určuje, zda aplikace nastavila vstupní fokus na jeden z ovládacích prvků v seznamu vlastností. Pokud `OnInitDialog` vrátí nenulovou hodnotu, systém Windows nastaví fokus vstupu na první ovládací prvek v seznamu vlastností. Aplikace může vrátit 0 pouze v případě, že explicitně nastaví fokus vstupu na jeden z ovládacích prvků v seznamu vlastností.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá v reakci na zprávu WM_INITDIALOG. Tato zpráva se odešle do seznamu vlastností během volání [Create](#create) nebo [DoModal](#domodal) , která se objeví těsně před zobrazením seznamu vlastností.

Tuto členskou funkci přepište, pokud při inicializaci seznamu vlastností potřebujete provést zvláštní zpracování. V přepsané verzi nejdříve zavolejte základní třídu `OnInitDialog` , ale Nezabereme její návratovou hodnotu. Obvykle se vrátí TRUE z přepsané členské funkce.

Pro tuto členskou funkci nepotřebujete položku mapování zpráv.

##  <a name="pressbutton"></a>  CPropertySheet::PressButton

Simuluje výběr zadaného tlačítka v seznamu vlastností.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parametry

*nNový*<br/>
nNový Identifikuje tlačítko, které se má stisknout. Tento parametr může být jedna z následujících hodnot:

- PSBTN_BACK klikne na tlačítko zpět.

- PSBTN_NEXT klepne na tlačítko Další.

- PSBTN_FINISH klikne na tlačítko Dokončit.

- PSBTN_OK klikne na tlačítko OK.

- PSBTN_APPLYNOW klikne na tlačítko použít.

- PSBTN_CANCEL klikne na tlačítko Storno.

- PSBTN_HELP zvolí tlačítko Help.

### <a name="remarks"></a>Poznámky

Další informace o Windows SDK zprávě PressButton najdete v tématu [PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) .

Volání `PressButton` nebudou odesílat oznámení [PSN_APPLY](/windows/win32/Controls/psn-apply) ze stránky vlastností do rozhraní. Chcete-li odeslat toto oznámení, zavolejte [CPropertyPage –:: OnOK –](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>CPropertySheet –:: volat RemovePage

Odebere ze seznamu vlastností stránku a odstraní přidružené okno.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
Odkazuje na stránku, která má být odebrána ze seznamu vlastností. Nemůže mít hodnotu NULL.

*nPage*<br/>
Index stránky, která se má odebrat Hodnota musí být mezi 0 a menší než počet stránek v seznamu vlastností (včetně).

### <a name="remarks"></a>Poznámky

Samotný objekt [CPropertyPage –](../../mfc/reference/cpropertypage-class.md) nebude zničen, dokud není zavřen vlastník `CPropertySheet` okna.

##  <a name="setactivepage"></a>CPropertySheet –:: SetActivePage

Změní aktivní stránku.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
Index stránky, která se má nastavit Musí být mezi 0 a menší než počet stránek v seznamu vlastností (včetně).

*pPage*<br/>
Odkazuje na stránku, která má být nastavena v seznamu vlastností. Nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je seznam vlastností úspěšně aktivován; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Například použijte `SetActivePage` v případě, že akce uživatele na jedné stránce by měla způsobit, že se na aktivní stránce stane jiná stránka.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CPropertySheet –:: GetActivePage](#getactivepage).

##  <a name="setfinishtext"></a>CPropertySheet –:: SetFinishText

Nastaví text na příkazovém tlačítku dokončit.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Odkazuje na text, který se má zobrazit na příkazovém tlačítku pro dokončení.

### <a name="remarks"></a>Poznámky

Voláním `SetFinishText` zobrazíte text na příkazovém tlačítku dokončit a skryjete tlačítko Další a zpět, jakmile uživatel dokončí akci na poslední stránce průvodce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>CPropertySheet –:: SetTitle

Určuje titulek seznamu vlastností (text zobrazený v záhlaví okna rámce).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Určuje styl názvu seznamu vlastností. Styl musí být zadán na hodnotu 0 nebo jako PSH_PROPTITLE. Pokud je styl nastaven jako PSH_PROPTITLE, zobrazí se po textu zadaném jako popisek slovo Properties (vlastnosti). Například volání `SetTitle`("Simple", PSH_PROPTITLE) bude mít za následek nadpis seznamu vlastností "jednoduché vlastnosti".

*lpszText*<br/>
Odkazuje na text, který má být použit jako titulek v záhlaví seznamu vlastností.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení seznam vlastností používá parametr Caption v konstruktoru seznamu vlastností.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>CPropertySheet –:: SetWizardButtons

Povolí nebo zakáže tlačítko zpět, další nebo dokončit v seznamu vlastností průvodce.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Sada příznaků, které přizpůsobují funkce a vzhled tlačítek průvodce. Tento parametr může být kombinací následujících hodnot:

- PSWIZB_BACK – tlačítko zpět

- Tlačítko Další PSWIZB_NEXT

- Tlačítko pro dokončení PSWIZB_FINISH

- PSWIZB_DISABLEDFINISH zakázané tlačítko pro dokončení

### <a name="remarks"></a>Poznámky

Volání `SetWizardButtons` až po otevření dialogového okna; nemůžete volat `SetWizardButtons` před voláním [DoModal](#domodal). Obvykle byste měli zavolat `SetWizardButtons` z [CPropertyPage –:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Pokud chcete změnit text na tlačítku dokončit nebo skrýt tlačítko Další a zpět, jakmile uživatel průvodce dokončí, zavolejte [SetFinishText](#setfinishtext). Všimněte si, že stejné tlačítko je sdíleno pro možnost Dokončit a další. V jednom okamžiku můžete zobrazit tlačítko Dokončit nebo další, ale ne obojí.

### <a name="example"></a>Příklad

Má tři stránky vlastností Průvodce: `CStylePage`, `CColorPage`, a `CShapePage`. `CPropertySheet`  Následující fragment kódu ukazuje, jak povolit a zakázat tlačítka **zpět** a **Další** na stránce vlastností průvodce.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>CPropertySheet –:: SetWizardMode

Vytvoří stránku vlastností jako průvodce.

```
void SetWizardMode();
```

### <a name="remarks"></a>Poznámky

Klíčovou charakteristikou stránky průvodce je, že uživatel přejde pomocí tlačítek Další nebo dokončit, zpět a zrušit místo na kartách.

Zavolejte `SetWizardMode` před voláním [DoModal](#domodal). Po volání `SetWizardMode` `DoModal` vrátí buď ID_WIZFINISH (Pokud uživatel zavírá tlačítko Dokončit), nebo IDCANCEL.

`SetWizardMode`nastaví příznak PSH_WIZARD.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Viz také:

[CMNCTRL1 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CMNCTRL2 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[PROPDLG Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[SNAPVW Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
