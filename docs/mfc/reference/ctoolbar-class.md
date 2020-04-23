---
title: CToolBar – třída
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
ms.openlocfilehash: cbb2d1bb797737a14e9728d339305bf9c371b543
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752204"
---
# <a name="ctoolbar-class"></a>CToolBar – třída

Ovládací panely, které mají řadu bitmapovaných tlačítek a volitelné oddělovače.

## <a name="syntax"></a>Syntaxe

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Ctoolbar::CToolBar](#ctoolbar)|Vytvoří `CToolBar` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|Vrátí index tlačítka s daným ID příkazu.|
|[CToolBar::Vytvořit](#create)|Vytvoří panel nástrojů systému Windows `CToolBar` a připojí jej k objektu.|
|[CToolBar::CreateEx](#createex)|Vytvoří `CToolBar` objekt s dalšími styly pro vložený `CToolBarCtrl` objekt.|
|[Ctoolbar::GetButtonInfo](#getbuttoninfo)|Načte ID, styl a číslo obrázku tlačítka.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Načte styl tlačítka.|
|[Ctoolbar::GetButtonText](#getbuttontext)|Načte text, který se zobrazí na tlačítku.|
|[CToolBar::GetItemID](#getitemid)|Vrátí ID příkazu tlačítka nebo oddělovače v daném indexu.|
|[CToolBar::GetItemRect](#getitemrect)|Načte obdélník zobrazení pro položku v daném indexu.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Umožňuje přímý přístup k základní společný ovládací prvek.|
|[CToolBar::LoadBitmap](#loadbitmap)|Načte bitmapu obsahující obrazy bitmapových tlačítek.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Načte prostředek panelu nástrojů vytvořený pomocí editoru prostředků.|
|[CToolBar::SetBitmap](#setbitmap)|Nastaví bitmapovaný obraz.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Nastaví číslo ID, stylu a obrázku tlačítka.|
|[CToolBar::Tlačítka nastavení](#setbuttons)|Nastaví styly tlačítek a index obrazů tlačítek v bitmapě.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Nastaví styl tlačítka.|
|[CToolBar::SetButtonText](#setbuttontext)|Nastaví text, který se zobrazí na tlačítku.|
|[CToolBar::SetHeight](#setheight)|Nastaví výšku panelu nástrojů.|
|[CToolBar::SetSizes](#setsizes)|Nastaví velikosti tlačítek a jejich bitmap.|

## <a name="remarks"></a>Poznámky

Tlačítka mohou fungovat jako tlačítka, zaškrtávací tlačítka nebo přepínací tlačítka. `CToolBar`objekty jsou obvykle vložené členy objektů frame-window odvozených z třídy [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar::GetToolBarCtrl](#gettoolbarctrl), členská funkce nová pro knihovnu MFC 4.0, umožňuje využít podporu společného ovládacího prvku systému Windows pro přizpůsobení panelu nástrojů a další funkce. `CToolBar`členské funkce poskytují většinu funkcí běžných ovládacích prvků systému Windows; Při volání `GetToolBarCtrl`však můžete panelům nástrojů poskytnout ještě více vlastností panelů nástrojů systému Windows 95/98. Při volání `GetToolBarCtrl`vrátí odkaz na `CToolBarCtrl` objekt. Další informace o návrhu panelů nástrojů pomocí běžných ovládacích prvků systému Windows naleznete v tématu [CToolBarCtrl.](../../mfc/reference/ctoolbarctrl-class.md) Obecnější informace o běžných ovládacích prvcích naleznete v [tématu Common Controls](/windows/win32/Controls/common-controls-intro) in the Windows SDK.

Visual C++ poskytuje dvě metody pro vytvoření panelu nástrojů. Chcete-li vytvořit prostředek panelu nástrojů pomocí Editoru prostředků, postupujte takto:

1. Vytvořte prostředek panelu nástrojů.

1. Vytvořte `CToolBar` objekt.

1. Volání [vytvořit](#create) (nebo [CreateEx](#createex)) funkce vytvořit panel nástrojů `CToolBar` systému Windows a připojit k objektu.

1. Volání [LoadToolBar](#loadtoolbar) načíst prostředek panelu nástrojů.

Jinak postupujte podle těchto kroků:

1. Vytvořte `CToolBar` objekt.

1. Volání [vytvořit](#create) (nebo [CreateEx](#createex)) funkce vytvořit panel nástrojů `CToolBar` systému Windows a připojit k objektu.

1. [VoláníloadBitmap](#loadbitmap) načíst bitmapu, která obsahuje panel nástrojů tlačítko obrázky.

1. Volání [MAStrům](#setbuttons) nastavte styl tlačítka a přidružte každé tlačítko k obrazu v bitmapě.

Všechny obrázky tlačítek v panelu nástrojů jsou převzaty z jedné bitmapy, která musí obsahovat jeden obrázek pro každé tlačítko. Všechny obrázky musí mít stejnou velikost; výchozí hodnota je 16 pixelů široká a 15 pixelů vysoká. Obrazy musí být v bitmapě vedle sebe.

Funkce `SetButtons` přebírá ukazatel na pole ID ovládacího prvku a celé číslo, které určuje počet prvků v poli. Funkce nastaví ID každého tlačítka na hodnotu odpovídajícího prvku pole a přiřadí každému tlačítku index obrazu, který určuje polohu obrazu tlačítka v bitmapě. Pokud prvek pole má hodnotu ID_SEPARATOR, není přiřazen žádný index obrázku.

Pořadí obrazů v bitmapě je obvykle pořadí, ve kterém jsou kresleny na obrazovce, ale můžete použít [Funkci SetButtonInfo](#setbuttoninfo) změnit vztah mezi pořadí množiny obrázků a pořadí kreslení.

Všechna tlačítka na panelu nástrojů mají stejnou velikost. Výchozí hodnota je 24 x 22 pixelů v souladu s *pokyny rozhraní systému Windows pro návrh softwaru*. Další mezera mezi rozměry obrázku a tlačítka se použije k vytvoření ohraničení kolem obrázku.

Každé tlačítko má jeden obrázek. Z tohoto jednoho obrázku jsou generovány různé stavy a styly tlačítek (stisknuté, nahoru, dolů, zakázané, zakázané dolů a neurčité). Přestože bitmapy mohou mít libovolnou barvu, můžete dosáhnout nejlepších výsledků s obrazy v černé a odstínech šedé.

> [!WARNING]
> `CToolBar`podporuje bitmapy s maximálně 16 barvami. Když načtete obraz do editoru panelu nástrojů, Visual Studio automaticky převede obraz na bitmapu 16 barev, pokud je to nutné, a zobrazí se varovná zpráva, pokud byl obraz převeden. Pokud používáte obraz s více než 16 barvami (k úpravám obrazu pomocí externího editoru), může se aplikace chovat neočekávaně.

Tlačítka panelu nástrojů ve výchozím nastavení napodobují tlačítka. Tlačítka panelu nástrojů však mohou také napodobovat zaškrtávací políčka nebo přepínací tlačítka. Zaškrtávací políčka mají tři stavy: zaškrtnuté, nezaškrtnuté a neurčité. Přepínací tlačítka mají pouze dva stavy: zaškrtnuté a nezaškrtnuté.

Chcete-li nastavit styl jednotlivých tlačítek nebo oddělovačů bez směrování na pole, zavolejte `SetButtons` [GetButtonStyle,](#getbuttonstyle) abyste načetli styl, a pak místo něj zavolejte [SetButtonStyle](#setbuttonstyle) . `SetButtonStyle`je nejužitečnější, pokud chcete změnit styl tlačítka za běhu.

Chcete-li přiřadit text, který se zobrazí na tlačítku, zavolejte [GetButtonText,](#getbuttontext) abyste načetli text, který se zobrazí na tlačítku, a pak volání [MButtonText](#setbuttontext) nastavte text.

Chcete-li vytvořit zaškrtávací tlačítko, `CCmdUI` přiřaďte mu styl TBBS_CHECKBOX nebo použijte členskou `SetCheck` funkci objektu v obslužné rutině ON_UPDATE_COMMAND_UI. Volání `SetCheck` změní tlačítko na zaškrtávací políčko. Předat `SetCheck` argument 0 pro nezaškrtnuté, 1 pro kontrolovány nebo 2 pro neurčité.

Chcete-li vytvořit přepínací tlačítko, volejte členskou funkci [Objektu CCmdUI](../../mfc/reference/ccmdui-class.md) [setradio](../../mfc/reference/ccmdui-class.md#setradio) z obslužné rutiny ON_UPDATE_COMMAND_UI. Předat `SetRadio` argument 0 pro nezaškrtnuté nebo nenulové pro kontrolovány. Chcete-li zajistit vzájemně se vylučující chování skupiny rádiových vozidl, musíte mít ON_UPDATE_COMMAND_UI obslužné rutiny pro všechna tlačítka ve skupině.

Další informace o `CToolBar`použití naleznete v článku [Implementace panelu nástrojů knihovny MFC](../../mfc/mfc-toolbar-implementation.md) a [technická poznámka 31: Ovládací panely](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ovládací panel CControl](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="ctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CToolBar::CommandToIndex

Tato členská funkce vrátí index prvního tlačítka panelu nástrojů počínaje `nIDFind`pozicí 0, jejíž ID příkazu odpovídá .

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDNajít*<br/>
ID příkazu tlačítka panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

Index tlačítka nebo -1, pokud žádné tlačítko nemá dané ID příkazu.

## <a name="ctoolbarcreate"></a><a name="create"></a>CToolBar::Vytvořit

Tato členská funkce vytvoří panel nástrojů systému Windows (podřízené okno) a přidruží jej k objektu. `CToolBar`

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazenou položkou panelu nástrojů.

*dwStyl*<br/>
Styl panelu nástrojů. Další podporované styly panelu nástrojů jsou:

- CBRS_TOP Ovládací panel je v horní části okna rámce.

- CBRS_BOTTOM Ovládací panel je v dolní části okna rámce.

- CBRS_NOALIGN Ovládací panel není přemístěn, když je velikost nadřazené velikosti.

- CBRS_TOOLTIPS Ovládací panel zobrazuje tipy nástrojů.

- CBRS_SIZE_DYNAMIC Ovládací panel je dynamický.

- CBRS_SIZE_FIXED Ovládací lišta je pevná.

- CBRS_FLOATING Ovládací panel je plovoucí.

- CBRS_FLYBY stavový řádek zobrazuje informace o tlačítku.

- CBRS_HIDE_INPLACE Ovládací panel se uživateli nezobrazí.

*Nid*<br/>
ID podřízeného okna panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Také nastaví výšku panelu nástrojů na výchozí hodnotu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

## <a name="ctoolbarcreateex"></a><a name="createex"></a>CToolBar::CreateEx

Volání této funkce k vytvoření panelu nástrojů systému Windows `CToolBar` (podřízené okno) a přidružit k objektu.

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

*dwCtrlStyl*<br/>
Další styly pro vytvoření vloženého objektu [CToolBarCtrl.](../../mfc/reference/ctoolbarctrl-class.md) Ve výchozím nastavení je tato hodnota nastavena na TBSTYLE_FLAT. Úplný seznam stylů panelů nástrojů naleznete *v tématu dwStyle*.

*dwStyl*<br/>
Styl panelu nástrojů. Seznam vhodných stylů naleznete v části [Styly ovládacích prvků panelu nástrojů a styly tlačítek](/windows/win32/Controls/toolbar-control-and-button-styles) v sadě Windows SDK.

*rcBorders*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který definuje šířky ohraničení okna panelu nástrojů. Tato ohraničení jsou ve výchozím nastavení nastavena na 0,0,0,0, což vede k oknu panelu nástrojů bez ohraničení.

*Nid*<br/>
ID podřízeného okna panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Také nastaví výšku panelu nástrojů na výchozí hodnotu.

Místo `CreateEx`funkce [Vytvořit](#create)použijte , když při vytváření vloženého ovládacího prvku panelu nástrojů musí být přítomny určité styly. Například nastavte *dwCtrlStyle* na TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT a vytvořte panel nástrojů, který se podobá panelu nástrojů aplikace Internet Explorer 4.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

## <a name="ctoolbarctoolbar"></a><a name="ctoolbar"></a>Ctoolbar::CToolBar

Tato členská funkce `CToolBar` vytvoří objekt a nastaví výchozí velikosti.

```
CToolBar();
```

### <a name="remarks"></a>Poznámky

Voláním členské funkce [Vytvořit](#create) vytvořte okno panelu nástrojů.

## <a name="ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>Ctoolbar::GetButtonInfo

Tato členská funkce načte ID ovládacího prvku, styl a index obrázku tlačítka panelu nástrojů nebo oddělovače v umístění určeném *nIndex.*

```cpp
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítka panelu nástrojů nebo oddělovače, jehož informace mají být načteny.

*Nid*<br/>
Odkaz na UINT, který je nastaven na ID příkazu tlačítka.

*nStyl*<br/>
Odkaz na UINT, který je nastaven na styl tlačítka.

*iImage*<br/>
Odkaz na celé číslo, které je nastaveno na index obrazu tlačítka v bitmapě.

### <a name="remarks"></a>Poznámky

Tyto hodnoty jsou přiřazeny proměnným, na které odkazují *nID*, *nStyle*a *iImage*. Index obrazu je umístění obrazu v bitmapě, která obsahuje obrazy pro všechna tlačítka panelu nástrojů. První obrázek je na pozici 0.

Pokud *nIndex* určuje oddělovač, *iImage* je nastavena na šířku oddělovače v obrazových bodech.

## <a name="ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CToolBar::GetButtonStyle

Volánítéto členské funkce načíst styl tlačítka nebo oddělovačna na panelu nástrojů.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítka panelu nástrojů nebo stylu oddělovače, který má být načten.

### <a name="return-value"></a>Návratová hodnota

Styl tlačítka nebo oddělovače určený *nIndex*.

### <a name="remarks"></a>Poznámky

Styl tlačítka určuje, jak se tlačítko zobrazí a jak reaguje na vstup uživatele. Příklady stylů tlačítek naleznete v tématu [SetButtonStyle.](#setbuttonstyle)

## <a name="ctoolbargetbuttontext"></a><a name="getbuttontext"></a>Ctoolbar::GetButtonText

Volání této členské funkce načíst text, který se zobrazí na tlačítko.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index textu, který má být načten.

*rString*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který bude obsahovat text, který má být načten.

### <a name="return-value"></a>Návratová hodnota

Objekt `CString` obsahující text tlačítka.

### <a name="remarks"></a>Poznámky

Druhý formulář této členské funkce `CString` vyplní objekt textem řetězce.

## <a name="ctoolbargetitemid"></a><a name="getitemid"></a>CToolBar::GetItemID

Tato členská funkce vrátí ID příkazu tlačítka nebo oddělovače určeného *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky, jejíž ID má být načten.

### <a name="return-value"></a>Návratová hodnota

ID příkazu tlačítka nebo oddělovače *určeného nIndex*.

### <a name="remarks"></a>Poznámky

Oddělovače vrátí ID_SEPARATOR.

## <a name="ctoolbargetitemrect"></a><a name="getitemrect"></a>CToolBar::GetItemRect

Tato členská funkce `RECT` vyplní strukturu, jejíž adresa je obsažena v *lpRect* souřadnicemi tlačítka nebo oddělovače určené *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky (tlačítko nebo oddělovač), jehož obdélník ové souřadnice mají být načteny.

*lpRect*<br/>
Adresa [rect](/windows/win32/api/windef/ns-windef-rect) struktury, která bude obsahovat souřadnice položky.

### <a name="remarks"></a>Poznámky

Souřadnice jsou v obrazových bodech vzhledem k levému hornímu rohu panelu nástrojů.

Slouží `GetItemRect` k získání souřadnic oddělovače, který chcete nahradit polem se seznamem nebo jiným ovládacím prvkem.

### <a name="example"></a>Příklad

  Viz příklad [ctoolbar::SetSizes](#setsizes).

## <a name="ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a>CToolBar::GetToolBarCtrl

Tato členská funkce umožňuje přímý přístup k základní společný ovládací prvek.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CToolBarCtrl` objekt.

### <a name="remarks"></a>Poznámky

Slouží `GetToolBarCtrl` k využití funkcí společného ovládacího prvku panelu nástrojů systému Windows a k využití podpory, kterou [ctoolbarctrl](../../mfc/reference/ctoolbarctrl-class.md) poskytuje pro přizpůsobení panelu nástrojů.

Další informace o použití běžných ovládacích prvků naleznete v článku [Ovládací prvky](../../mfc/controls-mfc.md) a [běžné ovládací prvky](/windows/win32/Controls/common-controls-intro) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

## <a name="ctoolbarloadbitmap"></a><a name="loadbitmap"></a>CToolBar::LoadBitmap

Volánítéto členské funkce k načtení `lpszResourceName` `nIDResource`bitmapy určené nebo .

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Ukazatel na název prostředku bitmapy, která má být načtena.

*nIDZdroj*<br/>
ID prostředku bitmapy, která má být načtena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Bitmapa by měla obsahovat jeden obraz pro každé tlačítko panelu nástrojů. Pokud obrázky nemají standardní velikost (16 pixelů široké a 15 pixelů vysoké), volání [SetSizes](#setsizes) nastavte velikosti tlačítek a jejich obrazy.

> [!WARNING]
> `CToolBar`podporuje bitmapy s maximálně 16 barvami. Když načtete obraz do editoru panelu nástrojů, Visual Studio automaticky převede obraz na bitmapu 16 barev, pokud je to nutné, a zobrazí se varovná zpráva, pokud byl obraz převeden. Pokud používáte obraz s více než 16 barvami (k úpravám obrazu pomocí externího editoru), může se aplikace chovat neočekávaně.

## <a name="ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CToolBar::LoadToolBar

Voláním této členské funkce načtěte panel nástrojů určený *lpszResourceName* nebo *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Ukazatel na název prostředku panelu nástrojů, který má být načten.

*nIDZdroj*<br/>
ID prostředku panelu nástrojů, který má být načten.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Další informace o vytvoření prostředku panelu nástrojů naleznete v [editoru panelu nástrojů](../../windows/toolbar-editor.md) v článku.

### <a name="example"></a>Příklad

  Viz příklad [ctoolbar::CreateEx](#createex).

## <a name="ctoolbarsetbitmap"></a><a name="setbitmap"></a>CToolBar::SetBitmap

Voláním této členské funkce nastavte bitmapový obraz pro panel nástrojů.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parametry

*hbmImageWell*<br/>
Zpracovat bitmapový obraz, který je přidružen k panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Volání `SetBitmap` například změnit bitmapovaný obrázek poté, co uživatel provede akci v dokumentu, který změní akci tlačítka.

## <a name="ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBar::SetButtonInfo

Voláním této členské funkce nastavte ID příkazu, styl a číslo obrázku tlačítka.

```cpp
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nulový index tlačítka nebo oddělovače, pro který mají být informace nastaveny.

*Nid*<br/>
Hodnota, na kterou je nastaveno ID příkazu tlačítka.

*nStyl*<br/>
Nový styl tlačítka. Podporovány jsou následující styly tlačítek:

- TBBS_BUTTON Standardní tlačítko (výchozí)

- oddělovač TBBS_SEPARATOR

- TBBS_CHECKBOX zaškrtávací políčko Auto

- TBBS_GROUP Označuje začátek skupiny tlačítek.

- TBBS_CHECKGROUP Označuje začátek skupiny zaškrtávacích tlačítek.

- TBBS_DROPDOWN Vytvoří rozevírací seznam.

- TBBS_AUTOSIZE Šířka tlačítka se vypočítá na základě textu tlačítka, nikoli podle velikosti obrázku.

- TBBS_NOPREFIX K textu tlačítka nebude přidružena předpona akcelerátoru.

*iImage*<br/>
Nový index pro obraz tlačítka v bitmapě.

### <a name="remarks"></a>Poznámky

U oddělovačů, které mají styl TBBS_SEPARATOR, tato funkce nastaví šířku oddělovače v obrazových bodech na hodnotu uloženou v *iImage*.

> [!NOTE]
> Můžete také nastavit stavy tlačítek pomocí parametru *nStyle;* protože jsou však stavy tlačítek řízeny obslužnou rutinou [ON_UPDATE_COMMAND_UI,](message-map-macros-mfc.md#on_update_command_ui) bude během dalšího nečinného zpracování ztracen jakýkoli stav, který nastavíte pomocí. `SetButtonInfo` Další informace naleznete [v tématu Jak aktualizovat objekty uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md) a [TN031: Ovládací panely.](../../mfc/tn031-control-bars.md)

Informace o bitmapových obrázcích a tlačítkách naleznete v [tématech Přehled panelu CToolBar](../../mfc/reference/ctoolbar-class.md) a [CToolBar::LoadBitmap](#loadbitmap).

## <a name="ctoolbarsetbuttons"></a><a name="setbuttons"></a>CToolBar::Tlačítka nastavení

Tato členská funkce nastaví ID příkazu každého tlačítka panelu nástrojů na hodnotu určenou odpovídajícím prvkem pole *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*pole lpIDArray*<br/>
Ukazatel na pole ID příkazů. Může být NULL přidělit prázdná tlačítka.

*nIDCount*<br/>
Počet prvků v poli, na které se vztahuje *lpIDArray*.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud má prvek pole hodnotu ID_SEPARATOR, vytvoří se oddělovač v odpovídající pozici panelu nástrojů. Tato funkce také nastaví styl každého tlačítka tak, aby TBBS_BUTTON a styl každého oddělovače TBBS_SEPARATOR a každému tlačítku přiřadí index obrazu. Index obrazu určuje umístění obrazu tlačítka v bitmapě.

Není nutné účet pro oddělovače v bitmapě, protože tato funkce nepřiřazuje indexy obrázků pro oddělovače. Pokud je na panelu nástrojů tlačítka v pozicích 0, 1 a 3 a oddělovač na pozici 2, jsou obrázky v pozicích 0, 1 a 2 v rastrové mapě přiřazeny tlačítkům v pozicích 0, 1 a 3.

Pokud je *lpIDArray* NULL, přidělí tato funkce místo pro počet položek určených *parametrem nIDCount*. Pomocí [funkce SetButtonInfo](#setbuttoninfo) nastavte atributy jednotlivých položek.

## <a name="ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CToolBar::SetButtonStyle

Voláním této členské funkce nastavte styl tlačítka nebo oddělovače nebo seskupte tlačítka.

```cpp
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tlačítka nebo oddělovače, jehož informace mají být nastaveny.

*nStyl*<br/>
Styl tlačítka. Podporovány jsou následující styly tlačítek:

- TBBS_BUTTON Standardní tlačítko (výchozí)

- oddělovač TBBS_SEPARATOR

- TBBS_CHECKBOX zaškrtávací políčko Auto

- TBBS_GROUP Označuje začátek skupiny tlačítek.

- TBBS_CHECKGROUP Označuje začátek skupiny zaškrtávacích tlačítek.

- TBBS_DROPDOWN Vytvoří tlačítko rozevíracího seznamu.

- TBBS_AUTOSIZE Šířka tlačítka se vypočítá na základě textu tlačítka, nikoli na základě velikosti obrázku

- TBBS_NOPREFIX Text tlačítka nebude mít přidruženou předponu akcelerátoru

### <a name="remarks"></a>Poznámky

Styl tlačítka určuje, jak se tlačítko zobrazí a jak reaguje na vstup uživatele.

Před `SetButtonStyle`voláním volejte člennou funkci [GetButtonStyle,](#getbuttonstyle) abyste načetli styl tlačítka nebo oddělovače.

> [!NOTE]
> Můžete také nastavit stavy tlačítek pomocí parametru *nStyle;* protože jsou však stavy tlačítek řízeny obslužnou rutinou [ON_UPDATE_COMMAND_UI,](message-map-macros-mfc.md#on_update_command_ui) bude během dalšího nečinného zpracování ztracen jakýkoli stav, který nastavíte pomocí. `SetButtonStyle` Další informace naleznete [v tématu Jak aktualizovat objekty uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md) a [TN031: Ovládací panely.](../../mfc/tn031-control-bars.md)

## <a name="ctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CToolBar::SetButtonText

Voláním této funkce nastavte text na tlačítko.

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

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

  Viz příklad [ctoolbar::GetToolBarCtrl](#gettoolbarctrl).

## <a name="ctoolbarsetheight"></a><a name="setheight"></a>CToolBar::SetHeight

Tato členská funkce nastaví výšku panelu nástrojů na hodnotu v obrazových bodech zadanou v *poli cyHeight*.

```cpp
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parametry

*cyVýška*<br/>
Výška v obrazových bodech panelu nástrojů.

### <a name="remarks"></a>Poznámky

Po volání [SetSizes](#setsizes)použijte tuto členovou funkci k přepsání standardní výšky panelu nástrojů. Pokud je výška příliš malá, tlačítka budou dole oříznuta.

Pokud tato funkce není volána, rozhraní používá velikost tlačítka k určení výšky panelu nástrojů.

## <a name="ctoolbarsetsizes"></a><a name="setsizes"></a>CToolBar::SetSizes

Voláním této členské funkce nastavte tlačítka panelu nástrojů na velikost v pixelech zadaná v *poli sizeButton*.

```cpp
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parametry

*sizeButton*<br/>
Velikost v pixelech každého tlačítka.

*sizeImage*<br/>
Velikost v obrazových bodech každého obrázku.

### <a name="remarks"></a>Poznámky

Parametr *sizeImage* musí obsahovat velikost obrazů v bitmapě panelu nástrojů v obrazových bodech. Rozměry v *sizeButton* musí být dostatečné pro uložení obrazu plus 7 pixelů navíc na šířku a 6 pixelů navíc na výšku. Tato funkce také nastaví výšku panelu nástrojů tak, aby odpovídala tlačítkům.

Tuto členská funkci zavolejte pouze pro panely nástrojů, které nedodržují *pokyny rozhraní systému Windows pro* doporučení návrhu softwaru pro velikosti tlačítek a obrázků.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC Ukázka DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CToolBarctrl](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
