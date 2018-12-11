---
title: Ctoolbar – třída
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: 938df6599ca3bfec3e08e77d7a60106133f54324
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178535"
---
# <a name="ctoolbar-class"></a>Ctoolbar – třída

Ovládací pruhy, které mají řádek tlačítek s rastrovými obrázky a volitelné oddělovače.

## <a name="syntax"></a>Syntaxe

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CToolBar::CToolBar](#ctoolbar)|Vytvoří `CToolBar` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|Vrátí index tlačítko s ID daného příkazu.|
|[CToolBar::Create](#create)|Vytvoří panel nástrojů Windows a připojí ho k `CToolBar` objektu.|
|[CToolBar::CreateEx](#createex)|Vytvoří `CToolBar` objekt s další styly pro vložený `CToolBarCtrl` objektu.|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Načte ID, styl a číslo obrázku tlačítka.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Načte styl tlačítka.|
|[CToolBar::GetButtonText](#getbuttontext)|Načte text, který se zobrazí na tlačítku.|
|[CToolBar::GetItemID](#getitemid)|Vrátí Identifikátor příkazu tlačítka nebo oddělovač v daném indexu.|
|[CToolBar::GetItemRect](#getitemrect)|Načte zobrazovací obdélník pro položku na daném indexu.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Umožňuje přímý přístup k podkladové běžný ovládací prvek.|
|[CToolBar::LoadBitmap](#loadbitmap)|Načte bitovou mapu obsahující obrázky rastrového obrázku tlačítka.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Načte prostředek panelu nástrojů vytvořené pomocí editoru prostředků.|
|[CToolBar::SetBitmap](#setbitmap)|Nastaví obrázek o rastrovými obrázky.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Nastaví ID, styl a číslo obrázku tlačítka.|
|[CToolBar::SetButtons](#setbuttons)|Nastaví tlačítko – styly a indexu obrázky tlačítek v rámci rastrového obrázku.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Nastaví styl tlačítka.|
|[CToolBar::SetButtonText](#setbuttontext)|Nastaví text, který se zobrazí na tlačítku.|
|[CToolBar::SetHeight](#setheight)|Nastaví výšku panelu nástrojů.|
|[CToolBar::SetSizes](#setsizes)|Nastaví velikost tlačítek a jejich rastrových obrázků.|

## <a name="remarks"></a>Poznámky

Tlačítka může sloužit jako tlačítek, tlačítka zaškrtávací políčko nebo přepínací tlačítka. `CToolBar` objekty jsou obvykle vložený členům odvozena od třídy objektů oken s rámečkem [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar::GetToolBarCtrl](#gettoolbarctrl), členské funkce nové knihovny MFC 4.0, vám umožní využít výhod podpory Windows běžné ovládacího prvku pro přizpůsobení panelu nástrojů a další funkce. `CToolBar` Členské funkce vám poskytnou většinu funkcí běžných ovládacích prvků Windows; ale při volání `GetToolBarCtrl`, můžete poskytnout panely nástrojů, ještě více vlastností panely nástrojů Windows 95/98. Při volání `GetToolBarCtrl`, vrátí odkaz na `CToolBarCtrl` objektu. Zobrazit [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) pro další informace o navrhování panely nástrojů, použití běžných ovládacích prvků Windows. Další obecné informace o běžných ovládacích prvků naleznete v tématu [běžné ovládací prvky](/windows/desktop/Controls/common-controls-intro) v sadě Windows SDK.

Visual C++ poskytuje dva způsoby vytvoření panelu nástrojů. Pokud chcete vytvořit prostředek panelu nástrojů editoru prostředků, postupujte takto:

1. Vytvořte prostředek panelu nástrojů.

1. Vytvořit `CToolBar` objektu.

1. Volání [vytvořit](#create) (nebo [CreateEx](#createex)) funkce, která se vytvořit panel nástrojů Windows a připojte ji k `CToolBar` objektu.

1. Volání [LoadToolBar](#loadtoolbar) načíst prostředek panelu nástrojů.

Jinak postupujte podle těchto kroků:

1. Vytvořit `CToolBar` objektu.

1. Volání [vytvořit](#create) (nebo [CreateEx](#createex)) funkce, která se vytvořit panel nástrojů Windows a připojte ji k `CToolBar` objektu.

1. Volání [loadbitmap –](#loadbitmap) načíst rastrový obrázek, který obsahuje obrázky tlačítka panelu nástrojů.

1. Volání [setbuttons –](#setbuttons) nastavit styl tlačítka a přidružení jednotlivá tlačítka s obrázkem rastrového obrázku nastaven.

Všechny obrázky tlačítek na panelu nástrojů pocházejí z jednoho rastrového obrázku, který musí obsahovat jednu image pro každé tlačítko. Všechny bitové kopie musí mít stejnou velikost; Výchozí hodnota je 16 pixelů a 15 pixelů na výšku. Image musí být vedle sebe v rastrového obrázku.

`SetButtons` Funkcí bere ukazatel na pole ID ovládacích prvků a celé číslo určující počet prvků v poli. Funkce nastaví ID každé tlačítko na hodnotu odpovídající prvek pole a přiřadí každé tlačítko index bitové kopie, která určuje umístění obrázku tlačítka rastrového obrázku nastaven. Pokud k elementu pole má hodnotu ID_SEPARATOR, přiřadí se žádný index bitové kopie.

Pořadí imagí v rastrového obrázku je obvykle pořadí, ve kterém jsou vykreslovány na obrazovce, ale můžete použít [SetButtonInfo](#setbuttoninfo) funkce změnit vztah mezi objednávkou image a pořadí vykreslování.

Všechna tlačítka na panelu nástrojů, mají stejnou velikost. Výchozí hodnota je 24 × 22 pixelů, v souladu s maticí *Windows rozhraní pokyny pro návrh softwaru*. Žádné další mezeru mezi rozměry obrázku a tlačítko se používá k vytvoření ohraničení kolem obrázku.

Každé tlačítko má jednu image. Různé stavy tlačítka a styly (disabled, zakázáno dolů a neurčitý při stisknutí tlačítka nahoru, dolů) se generují z této jedné image. Rastrové obrázky mohou být libovolné barvy, lze dosáhnout nejlepších výsledků s obrázky v černé a odstíny šedé.

> [!WARNING]
> `CToolBar` podporuje rastrové obrázky s délkou maximálně 16 barev. Při načítání bitovou kopii do panelu nástrojů editoru sady Visual Studio automaticky převede obrázek na 16 barev rastrový obrázek, v případě potřeby a zobrazí zprávu upozornění, pokud byl převeden na obrázku. Pokud použijete image s více než 16 barev (pomocí externí editor upravit obrázek), může být neočekávané chování aplikace.

Tlačítka panelu nástrojů napodobují tlačítek ve výchozím nastavení. Tlačítka panelu nástrojů můžete však také napodobují tlačítka zaškrtávací políčko nebo přepínací tlačítka. Zaškrtávací políčko tlačítka mají tři stavy: zaškrtnuto, nezaškrtnuté a neurčitý. Přepínací tlačítka mít pouze dva stavy: zaškrtnuto a zrušte zaškrtnutí.

Chcete-li nastavit jednotlivá tlačítka nebo styl oddělovače bez odkazující na pole, volejte [GetButtonStyle](#getbuttonstyle) načtení styl, a poté zavolejte [SetButtonStyle](#setbuttonstyle) místo `SetButtons`. `SetButtonStyle` Pokud chcete změnit styl tohoto tlačítka v době běhu je nejužitečnější.

Chcete-li přiřadit text, který se zobrazí na tlačítku, zavolejte [GetButtonText](#getbuttontext) načíst text, který se zobrazí na tlačítku a poté zavolejte [SetButtonText](#setbuttontext) nastaví text.

Vytvořit tlačítko, zaškrtávací políčko, přiřaďte ji styl TBBS_CHECKBOX nebo používání `CCmdUI` objektu `SetCheck` členské funkce v obslužné rutině ON_UPDATE_COMMAND_UI. Volání `SetCheck` se změní pushbutton tlačítko zaškrtávacího políčka. Předejte `SetCheck` argument 0 pro není zaškrtnuto, 1 pro zaškrtnuté, nebo 2 pro neurčitý.

Chcete-li vytvořit přepínací tlačítko, zavolejte [ccmdui –](../../mfc/reference/ccmdui-class.md) objektu [setradio –](../../mfc/reference/ccmdui-class.md#setradio) členskou funkci ze obslužnou rutinu ON_UPDATE_COMMAND_UI. Předejte `SetRadio` argument 0 není zaškrtnuto nebo nenulovou hodnotu pro zaškrtnutí. Aby bylo možné poskytovat chování vzájemně se vylučující skupiny přepínačů, musí mít ON_UPDATE_COMMAND_UI obslužné rutiny pro všechna tlačítka ve skupině.

Další informace o používání `CToolBar`, najdete v článku [implementace panelu nástrojů v prostředí MFC](../../mfc/mfc-toolbar-implementation.md) a [Technická poznámka 31: Ovládací pruhy](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Ccontrolbar –](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="commandtoindex"></a>  CToolBar::CommandToIndex

Tato členská funkce vrátí index prvního tlačítko panelu nástrojů, počínaje na pozici 0, jejíž ID příkazu odpovídá `nIDFind`.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDFind*<br/>
Identifikátor příkazu tlačítka panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Index tlačítka nebo -1, pokud se neobjeví tlačítko nemá ID daného příkazu.

##  <a name="create"></a>  CToolBar::Create

Tato členská funkce vytvoří panel nástrojů Windows (podřízené okno) a přidruží ji k `CToolBar` objektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na okno, která je nadřazeným prvkem panel nástrojů.

*dwStyle*<br/>
Styl toolbar. Další toolbar – styly podporovány jsou:

- CBRS_TOP ovládací panel je v horní části okna rámce.

- CBRS_BOTTOM ovládací panel je v dolní části okna rámce.

- Při změně velikosti nadřazené není přemístí CBRS_NOALIGN ovládací panel.

- CBRS_TOOLTIPS ovládací panel zobrazuje popisy tlačítek.

- CBRS_SIZE_DYNAMIC ovládací panel je dynamická.

- CBRS_SIZE_FIXED ovládací panel vyřešen.

- Panel ovládacího prvku CBRS_FLOATING je s plovoucí desetinnou čárkou.

- CBRS_FLYBY stavový řádek zobrazuje informace o tlačítku.

- Uživateli se nezobrazí CBRS_HIDE_INPLACE ovládací panel.

*nID*<br/>
ID podřízené okno panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Nastaví také výška panelu nástrojů na výchozí hodnotu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>  CToolBar::CreateEx

Voláním této funkce vytvořit panel nástrojů Windows (podřízené okno) a přidružte jej k `CToolBar` objektu.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na okno, která je nadřazeným prvkem panel nástrojů.

*dwCtrlStyle*<br/>
Další styly pro vytvoření vložený [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) objektu. Ve výchozím nastavení je tato hodnota nastavena na TBSTYLE_FLAT. Úplný seznam toolbar – styly, naleznete v tématu *dwStyle*.

*dwStyle*<br/>
Styl toolbar. Zobrazit [ovládací prvek panelu nástrojů a styly](/windows/desktop/Controls/toolbar-control-and-button-styles) v sadě Windows SDK pro seznam vhodné styly.

*rcBorders*<br/>
A [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který definuje šířky ohraničení okna nástrojů. Tyto hranice jsou nastaveny na 0,0,0,0 ve výchozím nastavení, což by vedlo k panelu nástrojů okno s bez ohraničení.

*nID*<br/>
ID podřízené okno panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Nastaví také výška panelu nástrojů na výchozí hodnotu.

Použití `CreateEx`, namísto [vytvořit](#create), když určité styly musí být k dispozici při vytváření ovládacích prvků panelu vložený nástroj. Například nastavte *dwCtrlStyle* k TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT vytvořit panel nástrojů, která se podobá Internet Exploreru 4 panely nástrojů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>  CToolBar::CToolBar

Tato členská funkce vytvoří `CToolBar` objekt a nastaví výchozí velikosti.

```
CToolBar();
```

### <a name="remarks"></a>Poznámky

Volání [vytvořit](#create) členská funkce se vytvořit okno nástrojů.

##  <a name="getbuttoninfo"></a>  CToolBar::GetButtonInfo

Tato členská funkce načte ID ovládacího prvku, styl a index obrázku tlačítka panelu nástrojů nebo oddělovač v umístění určeném *nIndex.*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítka panelu nástrojů nebo oddělovač, jehož informace má být načtena.

*nID*<br/>
Odkaz na UINT, která je nastavena na Identifikátor příkazu tlačítka.

*nStyle*<br/>
Odkaz na UINT, který je nastaven styl tlačítka.

*iImage*<br/>
Odkaz na celé číslo, které je nastavena na index obrázku tlačítka v rámci rastrového obrázku.

### <a name="remarks"></a>Poznámky

Tyto hodnoty jsou přiřazeny k proměnné odkazuje *nID*, *nStyle*, a *iImage*. Index bitové kopie je pozice image v rámci rastrový obrázek, který obsahuje Image pro tlačítka panelu nástrojů. První obrázek je na pozici 0.

Pokud *nIndex* Určuje oddělovač, *iImage* je nastavena na šířku oddělovače v pixelech.

##  <a name="getbuttonstyle"></a>  CToolBar::GetButtonStyle

Voláním této členské funkce k načtení styl tlačítka nebo oddělovač na panelu nástrojů.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index panelu nástrojů tlačítko nebo oddělovač styl se má načíst.

### <a name="return-value"></a>Návratová hodnota

Styl tlačítka nebo oddělovač určené *nIndex*.

### <a name="remarks"></a>Poznámky

Styl tohoto tlačítka Určuje, jak je zobrazeno tlačítko a jak reagovat na vstup uživatele. Zobrazit [SetButtonStyle](#setbuttonstyle) příklady styly.

##  <a name="getbuttontext"></a>  CToolBar::GetButtonText

Voláním této členské funkce k načtení textu, který se zobrazí na tlačítku.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index textu, který se má načíst.

*rString*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který bude obsahovat text, který se má načíst.

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který obsahuje text tlačítka.

### <a name="remarks"></a>Poznámky

Tedy o druhou podobu této členské funkce výplně `CString` objekt s text řetězce.

##  <a name="getitemid"></a>  CToolBar::GetItemID

Tato členská funkce vrátí Identifikátor příkazu tlačítka nebo oddělovač určené *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky, jejichž ID se má být načtena.

### <a name="return-value"></a>Návratová hodnota

Identifikátor příkazu tlačítka nebo oddělovač určené *nIndex*.

### <a name="remarks"></a>Poznámky

Oddělovače vrátit ID_SEPARATOR.

##  <a name="getitemrect"></a>  CToolBar::GetItemRect

Tato členská funkce vyplní `RECT` strukturu, jejíž adresa je součástí *lprect –* se souřadnicemi tlačítko nebo oddělovač určené *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky (tlačítko nebo oddělovač), jehož souřadnice obdélník se mají načíst.

*lprect –*<br/>
Adresa [RECT](/windows/desktop/api/windef/ns-windef-tagrect) struktura, která bude obsahovat souřadnice položky.

### <a name="remarks"></a>Poznámky

Souřadnice jsou uváděny v pixelech vzhledem k levého horního rohu panelu nástrojů.

Použití `GetItemRect` získat souřadnice chcete nahradit pole se seznamem nebo jiný ovládací prvek oddělovače.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CToolBar::SetSizes](#setsizes).

##  <a name="gettoolbarctrl"></a>  CToolBar::GetToolBarCtrl

Tato členská funkce umožňuje přímý přístup k podkladové běžný ovládací prvek.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CToolBarCtrl` objektu.

### <a name="remarks"></a>Poznámky

Použití `GetToolBarCtrl` využít výhody funkcí Windows běžné ovládací prvek panelu nástrojů a využít výhod podpory [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) poskytuje pro přizpůsobení panelu nástrojů.

Další informace o použití běžných ovládacích prvků, najdete v článku [ovládací prvky](../../mfc/controls-mfc.md) a [běžné ovládací prvky](/windows/desktop/Controls/common-controls-intro) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>  CToolBar::LoadBitmap

Voláním této členské funkce se načíst bitmapu určené `lpszResourceName` nebo `nIDResource`.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Ukazatel na název prostředku rastrového obrázku, který se má načíst.

*nIDResource*<br/>
ID prostředku rastrového obrázku má být načten.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Rastrový obrázek musí obsahovat jednu image pro každé tlačítko panelu nástrojů. Pokud obrázky nemají velikosti standard (16 pixelů a 15 pixelů), volání [SetSizes](#setsizes) k nastavení velikosti tlačítko a jejich bitové kopie.

> [!WARNING]
> `CToolBar` podporuje rastrové obrázky s délkou maximálně 16 barev. Při načítání bitovou kopii do panelu nástrojů editoru sady Visual Studio automaticky převede obrázek na 16 barev rastrový obrázek, v případě potřeby a zobrazí zprávu upozornění, pokud byl převeden na obrázku. Pokud použijete image s více než 16 barev (pomocí externí editor upravit obrázek), může být neočekávané chování aplikace.

##  <a name="loadtoolbar"></a>  CToolBar::LoadToolBar

Voláním této členské funkce k načtení nástrojů určené *lpszResourceName* nebo *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Ukazatel na název prostředku panelu nástrojů, který se má načíst.

*nIDResource*<br/>
ID prostředku panelu nástrojů, který se má načíst.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Zobrazit [panelu nástrojů editoru](../../windows/toolbar-editor.md) v další informace o vytvoření prostředku panelu nástrojů.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CToolBar::CreateEx](#createex).

##  <a name="setbitmap"></a>  CToolBar::SetBitmap

Voláním této členské funkce pro nastavení rastrový obrázek pro panel nástrojů.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parametry

*hbmImageWell*<br/>
Popisovač rastrový obrázek, který je spojen s panelem nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Například volání `SetBitmap` změnit rastrových obrázků, až uživatel provede akci na dokumentu, který změní akce tlačítka.

##  <a name="setbuttoninfo"></a>  CToolBar::SetButtonInfo

Voláním této členské funkce pro nastavení ID příkazu, styl a číslo obrázku tlačítka.

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule tlačítko nebo oddělovač, pro který má být nastavena informace.

*nID*<br/>
Hodnota, na které je Identifikátor příkazu tlačítka nastavit.

*nStyle*<br/>
Nový styl tlačítka. Podporují se tyto styly tlačítka:

- Pushbutton TBBS_BUTTON standardní (výchozí)

- Oddělovač TBBS_SEPARATOR

- Tlačítko automaticky TBBS_CHECKBOX zaškrtávací políčko

- TBBS_GROUP označuje začátek skupina tlačítek

- TBBS_CHECKGROUP označuje začátek skupina tlačítek, zaškrtávací políčko

- TBBS_DROPDOWN vytvoří tlačítko rozevíracího seznamu.

- TBBS_AUTOSIZE, které se vypočte šířka tlačítka podle textu tlačítka, ne na velikost bitové kopie.

- Text tlačítka TBBS_NOPREFIX nebude mít předponu akcelerátoru, s ním spojená.

*iImage*<br/>
Nový index obrázku tlačítka v rámci rastrového obrázku.

### <a name="remarks"></a>Poznámky

Pro oddělovače, které mají styl TBBS_SEPARATOR, tato funkce nastaví oddělovač šířku v pixelech na hodnotu uloženou v *iImage*.

> [!NOTE]
>  Můžete také nastavit pomocí stavy tlačítka *nStyle* parametr, nicméně protože stavy tlačítka se řídí [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) obslužnou rutinu, státy, které jste nastavili pomocí `SetButtonInfo` ztratí během na další zpracování při nečinnosti. Zobrazit [aktualizace objektů uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md) a [TN031: Ovládací pruhy](../../mfc/tn031-control-bars.md) Další informace.

Informace o rastrové obrázky a tlačítka, najdete v článku [ctoolbar –](../../mfc/reference/ctoolbar-class.md) přehled a [CToolBar::LoadBitmap](#loadbitmap).

##  <a name="setbuttons"></a>  CToolBar::SetButtons

Tato členská funkce nastaví ID příkazu pro každé tlačítko panelu nástrojů na hodnotu zadanou pomocí odpovídající prvek pole *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray*<br/>
Ukazatel na pole ID příkazů. To může mít hodnotu NULL pro přidělení prázdný tlačítka.

*nIDCount*<br/>
Počet prvků v poli odkazované *lpIDArray*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pokud element pole má hodnotu ID_SEPARATOR, vytvoří se oddělovač na odpovídající pozici panelu nástrojů. Tato funkce také nastaví styl každé tlačítko TBBS_BUTTON a každý oddělovač styl TBBS_SEPARATOR a přiřadí každé tlačítko index bitové kopie. Index bitové kopie Určuje umístění obrázku tlačítka v rámci rastrového obrázku.

Není nutné, aby se zohlednily oddělovače rastrového obrázku nastaven, protože tato funkce nepřiřazuje image indexů pro oddělovače. Pokud panel nástrojů má tlačítka při pozice 0, 1 a 3 a oddělovač na pozici 2, imagí v umístění 0, 1 a 2 ve vaší rastrového obrázku jsou přiřazeny k tlačítka při pozice 0, 1 a 3, v uvedeném pořadí.

Pokud *lpIDArray* má hodnotu NULL, tato funkce přiděluje místo pro počet položky zadané pomocí *nIDCount*. Použití [SetButtonInfo](#setbuttoninfo) nastavit atributy každé položky.

##  <a name="setbuttonstyle"></a>  CToolBar::SetButtonStyle

Voláním této členské funkce pro nastavení stylu tlačítka nebo oddělovač, nebo skupina tlačítek.

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítko nebo oddělovač, jehož informace je možné nastavit.

*nStyle*<br/>
Styl tlačítka. Podporují se tyto styly tlačítka:

- Pushbutton TBBS_BUTTON standardní (výchozí)

- Oddělovač TBBS_SEPARATOR

- Tlačítko automaticky TBBS_CHECKBOX zaškrtávací políčko

- TBBS_GROUP označuje začátek skupina tlačítek

- TBBS_CHECKGROUP označuje začátek skupina tlačítek, zaškrtávací políčko

- TBBS_DROPDOWN vytvoří tlačítko rozevíracího seznamu

- TBBS_AUTOSIZE, které se vypočte šířka tlačítka podle textu tlačítka, ne na velikost bitové kopie

- TBBS_NOPREFIX text tlačítka nebude mít předponu akcelerátoru, s ním spojená

### <a name="remarks"></a>Poznámky

Styl tohoto tlačítka Určuje, jak je zobrazeno tlačítko a jak reagovat na vstup uživatele.

Před voláním `SetButtonStyle`, zavolejte [GetButtonStyle](#getbuttonstyle) členské funkce lze získat styl tlačítka nebo oddělovač.

> [!NOTE]
>  Můžete také nastavit pomocí stavy tlačítka *nStyle* parametr, nicméně protože stavy tlačítka se řídí [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) obslužnou rutinu, státy, které jste nastavili pomocí `SetButtonStyle` ztratí během na další zpracování při nečinnosti. Zobrazit [aktualizace objektů uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md) a [TN031: Ovládací pruhy](../../mfc/tn031-control-bars.md) Další informace.

##  <a name="setbuttontext"></a>  CToolBar::SetButtonText

Voláním této funkce nastavit text na tlačítku.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítko, jejichž text je nastavit.

*lpszText*<br/>
Odkazuje na text, který má být nastavena na tlačítku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CToolBar::GetToolBarCtrl](#gettoolbarctrl).

##  <a name="setheight"></a>  CToolBar::SetHeight

Tato členská funkce nastaví výšku panelu nástrojů na hodnotu v pixelech, zadaný v *cyHeight*.

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parametry

*cyHeight*<br/>
Výška v pixelech panelu nástrojů.

### <a name="remarks"></a>Poznámky

Po volání [SetSizes](#setsizes), použijte tuto funkci člena přepsat výška standardním panelu nástrojů. Pokud výšku je příliš malá, bude oříznut tlačítek v dolní části.

Pokud tato funkce není volána, rozhraní používá velikost tlačítka k určení výška panelu nástrojů.

##  <a name="setsizes"></a>  CToolBar::SetSizes

Voláním této členské funkce nastavte tlačítka panelu nástrojů na velikost v pixelech, zadaný v *sizeButton*.

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parametry

*sizeButton*<br/>
Velikost v pixelech každé tlačítko.

*sizeImage*<br/>
Velikost v pixelech jednotlivých obrázků.

### <a name="remarks"></a>Poznámky

*SizeImage* parametr musí obsahovat velikost v pixelech, imagí v rastrového obrázku panelu nástrojů. Dimenze v *sizeButton* musí postačovat pro uložení image navíc 7 navíc šířku pixelů a 6 pixelů na výšku navíc. Tato funkce také nastaví výšku nástrojů tlačítek.

Voláním této členské funkce jenom pro panely nástrojů, které se neřídí *Windows rozhraní pokyny pro návrh softwaru* doporučení pro velikosti button a image.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC CTRLBARS](../../visual-cpp-samples.md)<br/>
[Ukázka DLGCBR32 knihovny MFC](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC DOCKTOOL](../../visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl – třída](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
