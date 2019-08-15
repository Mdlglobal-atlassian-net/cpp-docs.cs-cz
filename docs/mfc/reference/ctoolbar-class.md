---
title: CToolBar – – třída
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
ms.openlocfilehash: 4977cbe0b749724f999d6d7089d46f12d1e2963e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502393"
---
# <a name="ctoolbar-class"></a>CToolBar – – třída

Ovládací panely, které mají řádek tlačítek s rastrovými obrázky a volitelné oddělovače.

## <a name="syntax"></a>Syntaxe

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CToolBar –:: CToolBar –](#ctoolbar)|`CToolBar` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CToolBar –:: CommandToIndex](#commandtoindex)|Vrátí index tlačítka s daným ID příkazu.|
|[CToolBar –:: Create](#create)|Vytvoří panel nástrojů Windows a připojí ho k `CToolBar` objektu.|
|[CToolBar –:: CreateEx](#createex)|Vytvoří objekt s dalšími styly pro vložený `CToolBarCtrl` objekt. `CToolBar`|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Načte ID, styl a číslo obrázku tlačítka.|
|[CToolBar –:: GetButtonStyle](#getbuttonstyle)|Načte styl tlačítka.|
|[CToolBar::GetButtonText](#getbuttontext)|Načte text, který se zobrazí na tlačítku.|
|[CToolBar –:: getitemid](#getitemid)|Vrátí ID příkazu tlačítka nebo oddělovače na daném indexu.|
|[CToolBar –:: GetItemRect](#getitemrect)|Načte zobrazovací obdélník pro položku na daném indexu.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Umožňuje přímý přístup k základnímu běžnému ovládacímu prvku.|
|[CToolBar::LoadBitmap](#loadbitmap)|Načte rastr obsahující obrázky rastrového tlačítka.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Načte prostředek panelu nástrojů vytvořený pomocí editoru prostředků.|
|[CToolBar –:: SetBitmap](#setbitmap)|Nastaví obrázek rastrového obrázku.|
|[CToolBar –:: SetButtonInfo](#setbuttoninfo)|Nastaví ID, styl a číslo obrázku tlačítka.|
|[CToolBar –:: SetButtons](#setbuttons)|Nastaví styly tlačítek a index obrázků tlačítek v rámci rastrového obrázku.|
|[CToolBar –:: SetButtonStyle](#setbuttonstyle)|Nastaví styl tlačítka.|
|[CToolBar –:: SetButtonText](#setbuttontext)|Nastaví text, který se zobrazí na tlačítku.|
|[CToolBar –:: SetHeight](#setheight)|Nastaví výšku panelu nástrojů.|
|[CToolBar –:: SetSizes](#setsizes)|Nastaví velikost tlačítek a jejich rastrových obrázků.|

## <a name="remarks"></a>Poznámky

Tlačítka mohou fungovat jako pushbuttons, tlačítka pro zaškrtávací políčka nebo přepínače. `CToolBar`objekty jsou obvykle vložené členy objektů oken s rámečkem odvozenými z třídy [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIFrameWnd –](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar –:: GetToolBarCtrl](#gettoolbarctrl), členská funkce, která je novinkou pro MFC 4,0, vám umožní využít podporu obecného ovládacího prvku Windows pro přizpůsobení panelu nástrojů a další funkce. `CToolBar`Členské funkce poskytují většinu funkcí běžných ovládacích prvků Windows. Když však zavoláte `GetToolBarCtrl`, můžete své panely nástrojů poskytnout ještě více z vlastností panelů nástrojů Windows 95/98. Při volání `GetToolBarCtrl`vrátí odkaz `CToolBarCtrl` na objekt. Další informace o navrhování panelů nástrojů pomocí běžných ovládacích prvků Windows najdete v tématu [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) . Obecnější informace o běžných ovládacích prvcích najdete v tématu [běžné ovládací prvky](/windows/win32/Controls/common-controls-intro) v Windows SDK.

Vizuál C++ nabízí dvě metody vytvoření panelu nástrojů. K vytvoření prostředku panelu nástrojů pomocí editoru prostředků použijte následující postup:

1. Vytvořte prostředek panelu nástrojů.

1. Sestavte `CToolBar` objekt.

1. Voláním funkce [Create](#create) (nebo [CreateEx](#createex)) vytvořte panel nástrojů systému Windows a připojte `CToolBar` jej k objektu.

1. Voláním [LoadToolBar](#loadtoolbar) načtěte prostředek panelu nástrojů.

Jinak postupujte podle následujících kroků:

1. Sestavte `CToolBar` objekt.

1. Voláním funkce [Create](#create) (nebo [CreateEx](#createex)) vytvořte panel nástrojů systému Windows a připojte `CToolBar` jej k objektu.

1. Voláním [LoadBitmap](#loadbitmap) načtěte rastr, který obsahuje obrázky tlačítek panelu nástrojů.

1. Zavolejte [SetButtons](#setbuttons) a nastavte styl tlačítka a přidružte jednotlivá tlačítka k obrázku v rastrovém obrázku.

Všechny obrázky tlačítek na panelu nástrojů jsou odebírány z jedné bitmapy, která musí obsahovat jeden obrázek pro každé tlačítko. Všechny obrázky musí mít stejnou velikost; Výchozí hodnota je 16 pixelů na šířku a je vyšší než 15 pixelů. Obrázky musí být vedle sebe v rastrovém obrázku.

`SetButtons` Funkce přebírá ukazatel na pole ID ovládacího prvku a celé číslo, které určuje počet prvků v poli. Funkce nastaví ID každého tlačítka na hodnotu odpovídajícího prvku pole a přiřadí každému tlačítku index obrázku, který určuje polohu obrázku tlačítka v rastrovém obrázku. Pokud má element Array hodnotu ID_SEPARATOR, není přiřazen žádný index obrázku.

Pořadí obrázků v rastrovém obrázku je obvykle pořadím, ve kterém jsou vykreslovány na obrazovce, ale můžete použít funkci [SetButtonInfo](#setbuttoninfo) ke změně vztahu mezi pořadím obrázku a pořadím vykreslování.

Všechna tlačítka na panelu nástrojů mají stejnou velikost. Výchozí hodnota je 24 x 22 pixelů v souladu s *pokyny pro rozhraní Windows pro návrh softwaru*. Jakékoli další místo mezi rozměry obrázku a tlačítka se používá k vytvoření ohraničení kolem obrázku.

Každé tlačítko má jeden obrázek. Z tohoto obrázku jsou vygenerovány různé stavy a styly tlačítek (stisknuté, nahoru, vypnuto, zakázáno, zakázáno a neurčité). I když rastrové obrázky mohou být libovolné barvy, můžete dosáhnout nejlepších výsledků s obrázky černou a odstíny šedé.

> [!WARNING]
> `CToolBar`podporuje rastry s maximálně 16 barvami. Když načtete obrázek do editoru panelu nástrojů, Visual Studio automaticky převede obrázek na obrázek s 16 barvami, pokud je to nutné, a zobrazí upozornění, pokud byla bitová kopie převedena. Použijete-li obrázek s více než 16 barvami (pomocí externího editoru pro úpravu obrázku), aplikace se může chovat neočekávaně.

Tlačítka panelu nástrojů napodobují pushbuttons ve výchozím nastavení. Nicméně tlačítka panelu nástrojů mohou také napodobovat tlačítka zaškrtávacího políčka nebo přepínací tlačítka. Tlačítka pro zaškrtávací políčko mají tři stavy: zaškrtnuto, vymazáno a neurčito. Přepínače mají pouze dva stavy: zaškrtnuto a vymazáno.

Chcete-li nastavit styl jednotlivých tlačítek nebo oddělovačů bez nasměrování na pole, zavolejte [GetButtonStyle](#getbuttonstyle) pro načtení stylu a pak zavolejte [SetButtonStyle](#setbuttonstyle) namísto `SetButtons`. `SetButtonStyle`je nejužitečnější, pokud chcete změnit styl tlačítka v době běhu.

Chcete-li přiřadit text, který se zobrazí na tlačítku, zavolejte [GetButtonText](#getbuttontext) k načtení textu, který se zobrazí na tlačítku, a pak zavolejte [SetButtonText](#setbuttontext) pro nastavení textu.

Chcete-li vytvořit tlačítko pro zaškrtávací políčko, přiřaďte mu styl TBBS_CHECKBOX nebo použijte `CCmdUI` `SetCheck` členskou funkci objektu v obslužné rutině ON_UPDATE_COMMAND_UI. Voláním `SetCheck` se (pushbutton) převede na tlačítko se zaškrtávacím políčkem. Předejte `SetCheck` argument 0 pro nezaškrtnuto, 1 pro Checked nebo 2 pro neurčitou hodnotu.

Chcete-li vytvořit přepínač, zavolejte členskou funkci [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) objektu [CCmdUI –](../../mfc/reference/ccmdui-class.md) z obslužné rutiny ON_UPDATE_COMMAND_UI. Předejte `SetRadio` argument 0 pro nezaškrtnutí nebo nenulovou hodnotu pro zaškrtnutí. Aby bylo možné poskytnout vzájemně exkluzivní chování skupiny rádi, je nutné mít obslužné rutiny ON_UPDATE_COMMAND_UI pro všechna tlačítka ve skupině.

Další informace o použití `CToolBar`naleznete v článku [implementace panelu nástrojů MFC](../../mfc/mfc-toolbar-implementation.md) a [technická Poznámka 31: Ovládací panely](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext. h

##  <a name="commandtoindex"></a>CToolBar –:: CommandToIndex

Tato členská funkce vrátí index prvního tlačítka panelu nástrojů počínaje pozicí 0, jejíž ID příkazu odpovídá `nIDFind`.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDFind*<br/>
ID příkazu tlačítka panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

Index tlačítka nebo-1, pokud žádné tlačítko neobsahuje dané ID příkazu.

##  <a name="create"></a>CToolBar –:: Create

Tato členská funkce vytvoří panel nástrojů Windows (podřízené okno) a přidruží ho k `CToolBar` objektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazenou položkou panelu nástrojů.

*dwStyle*<br/>
Styl panelu nástrojů Podporovány jsou další styly panelů nástrojů:

- Ovládací panel CBRS_TOP je v horní části okna rámce.

- Ovládací panel CBRS_BOTTOM je v dolní části okna rámce.

- Ovládací panel CBRS_NOALIGN není přemístění při změně velikosti nadřazeného objektu.

- Ovládací panel CBRS_TOOLTIPS zobrazí popisy nástrojů.

- Ovládací panel CBRS_SIZE_DYNAMIC je dynamický.

- Je opraven ovládací panel CBRS_SIZE_FIXED.

- Ovládací panel CBRS_FLOATING je plovoucí.

- Stavový řádek CBRS_FLYBY zobrazí informace o tlačítku.

- Uživateli se nezobrazí ovládací panel CBRS_HIDE_INPLACE.

*nID*<br/>
ID podřízeného okna panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Také nastaví výšku panelu nástrojů na výchozí hodnotu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>CToolBar –:: CreateEx

Voláním této funkce vytvoříte panel nástrojů Windows (podřízené okno) a přidružíte ho `CToolBar` k objektu.

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
Ukazatel na okno, které je nadřazenou položkou panelu nástrojů.

*dwCtrlStyle*<br/>
Další styly pro vytvoření vloženého objektu [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) Ve výchozím nastavení je tato hodnota nastavená na TBSTYLE_FLAT. Úplný seznam stylů panelů nástrojů naleznete v tématu *dwStyle*.

*dwStyle*<br/>
Styl panelu nástrojů Seznam vhodných stylů najdete v tématu [ovládací prvky panelu nástrojů a styly tlačítek](/windows/win32/Controls/toolbar-control-and-button-styles) v Windows SDK.

*rcBorders*<br/>
Objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který definuje šířku ohraničení okna panelu nástrojů. Tato ohraničení jsou ve výchozím nastavení nastavena na 0, 0, 0, 0, což vede k oknu panelu nástrojů bez ohraničení.

*nID*<br/>
ID podřízeného okna panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Také nastaví výšku panelu nástrojů na výchozí hodnotu.

Použijte `CreateEx`namísto [Create](#create), pokud jsou určité styly přítomny při vytváření vloženého ovládacího prvku panelu nástrojů. Například nastavte *dwCtrlStyle* na TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT pro vytvoření panelu nástrojů, který se podobá panelům nástrojů Internet Explorer 4.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>CToolBar –:: CToolBar –

Tato členská funkce vytvoří `CToolBar` objekt a nastaví výchozí velikosti.

```
CToolBar();
```

### <a name="remarks"></a>Poznámky

Voláním funkce [vytvořit](#create) členskou funkci vytvořte okno panelu nástrojů.

##  <a name="getbuttoninfo"></a>CToolBar –:: GetButtonInfo

Tato členská funkce načte ID ovládacího prvku, styl a index obrázku tlačítka panelu nástrojů nebo oddělovače v umístění určeném parametrem *nIndex.*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítka panelu nástrojů nebo oddělovače, jejichž informace mají být načteny

*nID*<br/>
Odkaz na objekt UINT, který je nastaven na ID příkazu tlačítka.

*nStyle*<br/>
Odkaz na objekt UINT, který je nastaven na styl tlačítka.

*iImage*<br/>
Odkaz na celé číslo, které je nastaveno na index obrázku tlačítka v rámci rastrového obrázku.

### <a name="remarks"></a>Poznámky

Tyto hodnoty jsou přiřazeny k proměnným, na které odkazují *NID*, *nStyle*a *iImage*. Index obrázku je pozice obrázku v rastrovém obrázku, který obsahuje obrázky pro všechna tlačítka panelu nástrojů. První obrázek je na pozici 0.

Pokud *nIndex* určuje oddělovač, *iImage* se nastaví na šířku oddělovače v pixelech.

##  <a name="getbuttonstyle"></a>CToolBar –:: GetButtonStyle

Voláním této členské funkce načtěte styl tlačítka nebo oddělovače na panelu nástrojů.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítka panelu nástrojů nebo stylu oddělovače, který se má načíst

### <a name="return-value"></a>Návratová hodnota

Styl tlačítka nebo oddělovače určený parametrem *nIndex*

### <a name="remarks"></a>Poznámky

Styl tlačítka Určuje, jak se tlačítko zobrazí a jak reaguje na vstup uživatele. Příklady stylů tlačítek naleznete v tématu [SetButtonStyle](#setbuttonstyle) .

##  <a name="getbuttontext"></a>CToolBar –:: GetButtonText

Chcete-li načíst text, který se zobrazí na tlačítku, zavolejte tuto členskou funkci.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index textu, který se má načíst

*rString*<br/>
Odkaz na objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který bude obsahovat text, který má být načten.

### <a name="return-value"></a>Návratová hodnota

`CString` Objekt obsahující text tlačítka.

### <a name="remarks"></a>Poznámky

Druhá forma této členské funkce vyplní `CString` objekt textem řetězce.

##  <a name="getitemid"></a>CToolBar –:: getitemid

Tato členská funkce vrátí ID příkazu tlačítka nebo oddělovače určeného parametrem *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky, jejíž ID má být načteno.

### <a name="return-value"></a>Návratová hodnota

ID příkazu pro tlačítko nebo oddělovač určené parametrem *nIndex*.

### <a name="remarks"></a>Poznámky

Oddělovače vracejí ID_SEPARATOR.

##  <a name="getitemrect"></a>CToolBar –:: GetItemRect

Tato členská funkce vyplní strukturu, `RECT` jejíž adresa je obsažena v *lpRect* , souřadnicemi tlačítka nebo oddělovače určeného parametrem *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky (tlačítko nebo oddělovač), jejichž souřadnice obdélníku mají být načteny.

*lpRect*<br/>
Adresa struktury [Rect](/windows/win32/api/windef/ns-windef-rect) , která bude obsahovat souřadnice položky

### <a name="remarks"></a>Poznámky

Souřadnice jsou v pixelech vzhledem k levému hornímu rohu panelu nástrojů.

Použijte `GetItemRect` k získání souřadnic oddělovače, který chcete nahradit polem se seznamem nebo jiným ovládacím prvkem.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CToolBar –:: SetSizes](#setsizes).

##  <a name="gettoolbarctrl"></a>CToolBar –:: GetToolBarCtrl

Tato členská funkce umožňuje přímý přístup k základnímu běžnému ovládacímu prvku.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CToolBarCtrl` objekt.

### <a name="remarks"></a>Poznámky

Slouží `GetToolBarCtrl` k využití funkcí společného ovládacího prvku panelu nástrojů Windows a k využití [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) podpory pro přizpůsobení panelu nástrojů.

Další informace o použití běžných ovládacích prvků naleznete v článku [ovládací prvky](../../mfc/controls-mfc.md) a [běžné ovládací prvky](/windows/win32/Controls/common-controls-intro) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>CToolBar –:: LoadBitmap

Zavolejte tuto členskou funkci pro načtení rastrového obrázku určeného `lpszResourceName` nebo `nIDResource`.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Ukazatel na název prostředku rastrového obrázku, který má být načten.

*nIDResource*<br/>
ID prostředku rastrového obrázku, který má být načten.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Rastrový obrázek by měl obsahovat jeden obrázek pro každé tlačítko panelu nástrojů. Pokud obrázky nemají standardní velikost (16 pixelů na šířku a 15 pixelů vysoké), zavolejte [SetSizes](#setsizes) a nastavte velikosti tlačítek a jejich obrázky.

> [!WARNING]
> `CToolBar`podporuje rastry s maximálně 16 barvami. Když načtete obrázek do editoru panelu nástrojů, Visual Studio automaticky převede obrázek na obrázek s 16 barvami, pokud je to nutné, a zobrazí upozornění, pokud byla bitová kopie převedena. Použijete-li obrázek s více než 16 barvami (pomocí externího editoru pro úpravu obrázku), aplikace se může chovat neočekávaně.

##  <a name="loadtoolbar"></a>CToolBar –:: LoadToolBar

Zavolejte tuto členskou funkci pro načtení panelu nástrojů určeného parametrem *lpszResourceName* nebo *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Ukazatel na název prostředku panelu nástrojů, který má být načten.

*nIDResource*<br/>
ID prostředku panelu nástrojů, který se má načíst

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Další informace o vytvoření prostředku panelu nástrojů najdete v tématu [Editor panelu nástrojů](../../windows/toolbar-editor.md) .

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CToolBar –:: CreateEx](#createex).

##  <a name="setbitmap"></a>CToolBar –:: SetBitmap

Chcete-li nastavit rastrový obrázek pro panel nástrojů, zavolejte tuto členskou funkci.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parametry

*hbmImageWell*<br/>
Popisovač rastrového obrázku, který je přidružen k panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Například zavolejte `SetBitmap` na změnu obrázku bitmapy poté, co uživatel provede akci s dokumentem, který změní akci tlačítka.

##  <a name="setbuttoninfo"></a>CToolBar –:: SetButtonInfo

Voláním této členské funkce nastavte ID příkazu, styl a číslo obrázku tlačítka.

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index vycházející z tlačítka nebo oddělovače založený na nule, pro které mají být nastaveny informace

*nID*<br/>
Hodnota, na kterou je nastaveno ID příkazu tlačítka

*nStyle*<br/>
Nový styl tlačítka. Podporují se tyto styly tlačítek:

- TBBS_BUTTON Standard (pushbutton) (výchozí)

- Oddělovač TBBS_SEPARATOR

- Tlačítko pro automatické zaškrtávací políčko TBBS_CHECKBOX

- TBBS_GROUP označuje začátek skupiny tlačítek.

- TBBS_CHECKGROUP označuje začátek skupiny tlačítek se zaškrtávacím políčkem.

- TBBS_DROPDOWN vytvoří tlačítko rozevíracího seznamu.

- TBBS_AUTOSIZE Šířka tlačítka se vypočítá na základě textu tlačítka, nikoli podle velikosti obrázku.

- TBBS_NOPREFIX na text tlačítka nebude přiřazena předpona akcelerátoru.

*iImage*<br/>
Nový index obrázku tlačítka v rámci rastrového obrázku

### <a name="remarks"></a>Poznámky

Pro oddělovače, které mají styl TBBS_SEPARATOR, tato funkce nastaví šířku oddělovače v pixelech na hodnotu uloženou v *iImage*.

> [!NOTE]
>  Stavy tlačítek můžete nastavit také pomocí parametru *nStyle* ; Nicméně, protože stavy tlačítek jsou ovládány obslužnou rutinou [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) , jakýkoli stav, který `SetButtonInfo` jste nastavili pomocí, bude ztracen během příštího nečinného zpracování. Podívejte [se, jak aktualizovat objekty uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md) a [TN031: Ovládací panely](../../mfc/tn031-control-bars.md) pro další informace.

Informace o rastrových obrázcích a tlačítkách naleznete v přehledu [CToolBar –](../../mfc/reference/ctoolbar-class.md) a [CToolBar –:: LoadBitmap](#loadbitmap).

##  <a name="setbuttons"></a>CToolBar –:: SetButtons

Tato členská funkce nastaví každé tlačítko panelu nástrojů na hodnotu určenou odpovídajícím prvkem pole *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray*<br/>
Ukazatel na pole ID příkazů. Pro přidělení prázdných tlačítek může mít hodnotu NULL.

*nIDCount*<br/>
Počet prvků v poli, na které ukazuje *lpIDArray*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud má element pole hodnotu ID_SEPARATOR, vytvoří se oddělovač v odpovídající pozici panelu nástrojů. Tato funkce také nastaví styl každého tlačítka na TBBS_BUTTON a každý styl oddělovače na TBBS_SEPARATOR a přiřadí k jednotlivým tlačítkům index obrázku. Index obrázku určuje pozici obrázku tlačítka v rámci rastrového obrázku.

Nemusíte vytvářet účty oddělovačů v rastrovém obrázku, protože tato funkce nepřiřazuje indexy obrázků pro oddělovače. Pokud má panel nástrojů tlačítka na pozicích 0, 1 a 3 a oddělovač na pozici 2, obrázky na pozicích 0, 1 a 2 ve vaší bitmapě jsou přiřazeny tlačítkům na pozicích 0, 1 a 3 v uvedeném pořadí.

Pokud má *lpIDArray* hodnotu null, tato funkce přidělí místo pro počet položek určených parametrem *nIDCount*. Použijte [SetButtonInfo](#setbuttoninfo) k nastavení atributů každé položky.

##  <a name="setbuttonstyle"></a>CToolBar –:: SetButtonStyle

Zavolejte tuto členskou funkci pro nastavení stylu tlačítka nebo oddělovače nebo pro seskupení tlačítek.

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítka nebo oddělovače, jejichž informace mají být nastaveny.

*nStyle*<br/>
Styl tlačítka Podporují se tyto styly tlačítek:

- TBBS_BUTTON Standard (pushbutton) (výchozí)

- Oddělovač TBBS_SEPARATOR

- Tlačítko pro automatické zaškrtávací políčko TBBS_CHECKBOX

- TBBS_GROUP označuje začátek skupiny tlačítek.

- TBBS_CHECKGROUP označuje začátek skupiny tlačítek se zaškrtávacím políčkem.

- TBBS_DROPDOWN vytvoří tlačítko rozevíracího seznamu.

- TBBS_AUTOSIZE Šířka tlačítka se vypočítá na základě textu tlačítka, nikoli podle velikosti obrázku.

- TBBS_NOPREFIX textu tlačítka nebude mít přidruženou předponu akcelerátoru.

### <a name="remarks"></a>Poznámky

Styl tlačítka Určuje, jak se tlačítko zobrazí a jak reaguje na vstup uživatele.

Před voláním `SetButtonStyle`volejte členskou funkci [GetButtonStyle](#getbuttonstyle) , která načte styl tlačítka nebo oddělovače.

> [!NOTE]
>  Stavy tlačítek můžete nastavit také pomocí parametru *nStyle* ; Nicméně, protože stavy tlačítek jsou ovládány obslužnou rutinou [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) , jakýkoli stav, který `SetButtonStyle` jste nastavili pomocí, bude ztracen během příštího nečinného zpracování. Podívejte [se, jak aktualizovat objekty uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md) a [TN031: Ovládací panely](../../mfc/tn031-control-bars.md) pro další informace.

##  <a name="setbuttontext"></a>CToolBar –:: SetButtonText

Voláním této funkce nastavíte text na tlačítko.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítka, jehož text má být nastaven.

*lpszText*<br/>
Odkazuje na text, který má být nastaven na tlačítko.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CToolBar –:: GetToolBarCtrl](#gettoolbarctrl).

##  <a name="setheight"></a>CToolBar –:: SetHeight

Tato členská funkce nastavuje výšku panelu nástrojů na hodnotu v pixelech určených v *cyHeight*.

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parametry

*cyHeight*<br/>
Výška v pixelech panelu nástrojů

### <a name="remarks"></a>Poznámky

Po volání [SetSizes](#setsizes)použijte tuto členskou funkci k přepsání standardní výšky panelu nástrojů. Pokud je výška příliš malá, tlačítka se v dolní části oříznou.

Pokud tato funkce není volána, rozhraní používá velikost tlačítka k určení výšky panelu nástrojů.

##  <a name="setsizes"></a>CToolBar –:: SetSizes

Zavolejte tuto členskou funkci pro nastavení tlačítek panelu nástrojů na velikost (v pixelech), která je určena v *sizeButton*.

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parametry

*sizeButton*<br/>
Velikost každého tlačítka v pixelech

*sizeImage*<br/>
Velikost každého obrázku v pixelech.

### <a name="remarks"></a>Poznámky

Parametr *sizeImage* musí obsahovat velikost obrázků v rastrovém obrázku panelu nástrojů (v pixelech). Rozměry v *sizeButton* musí být dostačující pro uchování obrázku Plus 7 pixelů extra na šířku a dalších 6 pixelů na výšku. Tato funkce také nastaví výšku panelu nástrojů tak, aby odpovídala tlačítkům.

Tuto členskou funkci volejte jenom pro panely nástrojů, které nedodržují *pokyny pro rozhraní Windows* pro doporučení pro navrhování softwaru pro velikost tlačítek a obrázků.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Viz také:

[CTRLBARS Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[DLGCBR32 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[DOCKTOOL Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl – třída](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
