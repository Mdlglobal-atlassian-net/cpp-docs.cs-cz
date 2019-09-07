---
title: Atributu CReBarCtrl – třída
ms.date: 11/19/2018
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
ms.openlocfilehash: 14befb819a30238abb5780b1bdcc6d74402e8976
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741193"
---
# <a name="crebarctrl-class"></a>Atributu CReBarCtrl – třída

Zapouzdřuje funkce ovládacího prvku matrice, který je kontejnerem pro podřízené okno.

## <a name="syntax"></a>Syntaxe

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|`CReBarCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|Umístí ovládací prvek matrice do režimu přetažení.|
|[CReBarCtrl::Create](#create)|Vytvoří ovládací prvek matrice a připojí ho k `CReBarCtrl` objektu.|
|[CReBarCtrl::CreateEx](#createex)|Vytvoří ovládací prvek matrice se zadanými rozšířenými styly Windows a připojí ho k `CReBarCtrl` objektu.|
|[CReBarCtrl::DeleteBand](#deleteband)|Odstraní z ovládacího prvku matrice pásmo.|
|[CReBarCtrl::DragMove](#dragmove)|Aktualizuje pozici přetažení v ovládacím prvku matrice po volání `BeginDrag`.|
|[CReBarCtrl::EndDrag](#enddrag)|Ukončí operaci přetažení ovládacího prvku matrice.|
|[CReBarCtrl::GetBandBorders](#getbandborders)|Načte ohraničení pásma.|
|[CReBarCtrl::GetBandCount](#getbandcount)|Načte počet pásem aktuálně v ovládacím prvku matrice.|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Načte informace o určeném pásmu v ovládacím prvku matrice.|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Načte okraje pásma.|
|[CReBarCtrl::GetBarHeight](#getbarheight)|Načte výšku ovládacího prvku matrice.|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Načte informace o ovládacím prvku matrice a seznamu obrázků, který používá.|
|[CReBarCtrl::GetBkColor](#getbkcolor)|Načte výchozí barvu pozadí ovládacího prvku matrice.|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Načte strukturu [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) přidruženou k ovládacímu prvku matrice.|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Načte ukazatel `IDropTarget` rozhraní ovládacího prvku matrice.|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Získá rozšířený styl aktuálního ovládacího prvku matrice.|
|[CReBarCtrl::GetImageList](#getimagelist)|Načte seznam obrázků přidružený k ovládacímu prvku matrice.|
|[CReBarCtrl::GetPalette](#getpalette)|Načte aktuální paletu ovládacího prvku matrice.|
|[CReBarCtrl::GetRect](#getrect)|Načte ohraničující obdélník pro daný proužek v ovládacím prvku matrice.|
|[CReBarCtrl::GetRowCount](#getrowcount)|Načte počet řádků pásma v ovládacím prvku matrice.|
|[CReBarCtrl::GetRowHeight](#getrowheight)|Načte výšku zadaného řádku v ovládacím prvku matrice.|
|[CReBarCtrl::GetTextColor](#gettextcolor)|Načte výchozí barvu textu ovládacího prvku matrice.|
|[CReBarCtrl::GetToolTips](#gettooltips)|Načte popisovač pro jakýkoli ovládací prvek popisu tlačítka přidružený k ovládacímu prvku matrice.|
|[CReBarCtrl::HitTest](#hittest)|Určuje, která část matrice pásma je na daném místě na obrazovce, pokud matrice pásmo v tomto okamžiku existuje.|
|[CReBarCtrl::IDToIndex](#idtoindex)|Převede identifikátor pásma (ID) na index pásma v ovládacím prvku matrice.|
|[CReBarCtrl::InsertBand](#insertband)|Vloží nový proužek do ovládacího prvku matrice.|
|[CReBarCtrl::MaximizeBand](#maximizeband)|Změní velikost pásma v ovládacím prvku matrice na jeho největší velikost.|
|[CReBarCtrl::MinimizeBand](#minimizeband)|Změní velikost pásma v ovládacím prvku matrice na jeho nejmenší velikost.|
|[CReBarCtrl::MoveBand](#moveband)|Přesune proužek z jednoho indexu do druhého.|
|[CReBarCtrl::PushChevron](#pushchevron)|Prostřednictvím kódu programu je vložena Dvojitá šipka.|
|[Atributu CReBarCtrl:: RestoreBand](#restoreband)|Změní velikost pásma v ovládacím prvku matrice na jeho ideální velikost.|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Nastaví charakteristiky existující řady v ovládacím prvku matrice.|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Nastaví šířku určené ukotvené řady v aktuálním ovládacím prvku matrice.|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Nastaví charakteristiky ovládacího prvku matrice.|
|[CReBarCtrl::SetBkColor](#setbkcolor)|Nastaví výchozí barvu pozadí ovládacího prvku matrice.|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Nastaví barevné schéma pro tlačítka na ovládacím prvku matrice.|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly pro aktuální ovládací prvek matrice.|
|[CReBarCtrl::SetImageList](#setimagelist)|Nastaví seznam obrázků ovládacího prvku matrice.|
|[CReBarCtrl::SetOwner](#setowner)|Nastaví vlastní okno ovládacího prvku matrice.|
|[CReBarCtrl::SetPalette](#setpalette)|Nastaví aktuální paletu ovládacího prvku matrice.|
|[CReBarCtrl::SetTextColor](#settextcolor)|Nastaví výchozí barvu textu ovládacího prvku matrice.|
|[CReBarCtrl::SetToolTips](#settooltips)|Přidruží ovládací prvek popis tlačítka k ovládacímu prvku matrice.|
|[Atributu CReBarCtrl:: SetWindowTheme](#setwindowtheme)|Nastaví vizuální styl ovládacího prvku matrice.|
|[CReBarCtrl::ShowBand](#showband)|Zobrazí nebo skryje daný proužek v ovládacím prvku matrice.|
|[CReBarCtrl::SizeToRect](#sizetorect)|Přizpůsobí ovládacímu prvku matrice určený obdélník.|

## <a name="remarks"></a>Poznámky

Aplikace, ve které se nachází ovládací prvek matrice, přiřadí podřízené okno obsažené v ovládacím prvku matrice do matrice pásma. Podřízené okno je obvykle další běžný ovládací prvek.

Ovládací prvky matrice obsahují jeden nebo více pásem. Každý pruh může obsahovat kombinaci úchytového panelu, rastrového obrázku, textového popisku a podřízeného okna. Pásmo může obsahovat pouze jednu z těchto položek.

Ovládací prvek matrice může zobrazit podřízené okno přes zadaný rastrový obrázek pozadí. Velikost všech řídicích pásem matrice lze změnit s výjimkou těch, které používají styl RBBS_FIXEDSIZE. Když přemístěte nebo změníte velikost řídicího panelu matrice, ovládací prvek matrice spravuje velikost a polohu podřízeného okna přiřazeného k tomuto pásma. Chcete-li změnit velikost nebo změnu pořadí pásem v rámci ovládacího prvku, klikněte na panel úchytu a přetáhněte ho na pruh.

Následující ilustrace znázorňuje ovládací prvek matrice, který má tři pruhy:

- Panel 0 obsahuje plochý transparentní ovládací prvek panelu nástrojů.

- Panel 1 obsahuje průhledná standardní i transparentní rozevírací tlačítko.

- Panel 2 obsahuje pole se seznamem a čtyři standardní tlačítka.

   ![Příklad nabídky matrice](../../mfc/reference/media/vc4scc1.gif "Příklad nabídky matrice")

## <a name="rebar-control"></a>Ovládací prvek matrice

Podpora ovládacích prvků matrice:

- Seznamy obrázků.

- Zpracování zpráv.

- Funkce vlastního vykreslování.

- Různé styly ovládacích prvků kromě standardních stylů oken. Seznam těchto stylů naleznete v tématu [styly ovládacího prvku matrice](/windows/win32/Controls/rebar-control-styles) v Windows SDK.

Další informace najdete v tématu [použití atributu CReBarCtrl](../../mfc/using-crebarctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag

Implementuje chování zprávy Win32 [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag), jak je popsáno v Windows SDK.

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásma, které bude mít vliv na operaci přetažení.

*dwPos*<br/>
Hodnota DWORD, která obsahuje počáteční souřadnice myši. Vodorovná souřadnice je obsažena v LOWORD a Svislá souřadnice je obsažena v HIWORD. Pokud předáte (DWORD)-1, ovládací prvek matrice použije pozici myši při posledním vyvolání `GetMessage` vlákna ovládacího prvku nebo. `PeekMessage`

##  <a name="create"></a>Atributu CReBarCtrl:: Create

Vytvoří ovládací prvek matrice a připojí ho k `CReBarCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje kombinaci stylů ovládacího prvku matrice použitých pro ovládací prvek. Seznam podporovaných stylů naleznete v tématu [styly ovládacího prvku matrice](/windows/win32/Controls/rebar-control-styles) v Windows SDK.

*OBD*<br/>
Odkaz na objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) nebo strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , což je pozice a velikost ovládacího prvku matrice.

*pParentWnd*<br/>
Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je nadřazeným oknem ovládacího prvku matrice. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku ovládacího prvku matrice.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl objekt úspěšně vytvořen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Vytvořte ovládací prvek matrice ve dvou krocích:

1. Volání [atributu CReBarCtrl](#crebarctrl) k vytvoření `CReBarCtrl` objektu.

1. Zavolejte tuto členskou funkci, která vytvoří ovládací prvek Windows matrice a připojí ho k `CReBarCtrl` objektu.

Při volání `Create`jsou inicializovány běžné ovládací prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

##  <a name="createex"></a>Atributu CReBarCtrl:: CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ho k `CReBarCtrl` objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Určuje rozšířený styl ovládacího prvku, který se vytváří. Seznam rozšířených stylů Windows naleznete v parametru *dwExStyle* pro [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

*dwStyle*<br/>
Určuje kombinaci stylů ovládacího prvku matrice použitých pro ovládací prvek. Seznam podporovaných stylů naleznete v tématu [styly ovládacího prvku matrice](/windows/win32/Controls/rebar-control-styles) v Windows SDK.

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) popisující velikost a umístění okna, které má být vytvořeno, v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*nID*<br/>
ID podřízeného okna ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` místo příkaz [vytvořit](#create) pro použití rozšířených stylů Windows, které jsou určené **WS_EX_** rozšířeným stylem Windows.

##  <a name="crebarctrl"></a>  CReBarCtrl::CReBarCtrl

`CReBarCtrl` Vytvoří objekt.

```
CReBarCtrl();
```

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CReBarCtrl:: Create](#create).

##  <a name="deleteband"></a>  CReBarCtrl::DeleteBand

Implementuje chování zprávy Win32 [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband), jak je popsáno v Windows SDK.

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásma, který se má odstranit

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se pásmo úspěšně odstranilo; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

##  <a name="dragmove"></a>  CReBarCtrl::DragMove

Implementuje chování zprávy Win32 [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove), jak je popsáno v Windows SDK.

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Hodnota DWORD, která obsahuje nové souřadnice myši. Vodorovná souřadnice je obsažena v LOWORD a Svislá souřadnice je obsažena v HIWORD. Pokud předáte (DWORD)-1, ovládací prvek matrice použije pozici myši při posledním vyvolání `GetMessage` vlákna ovládacího prvku nebo. `PeekMessage`

##  <a name="enddrag"></a>Atributu CReBarCtrl:: EndDrag

Implementuje chování zprávy Win32 [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag), jak je popsáno v Windows SDK.

```
void EndDrag();
```

##  <a name="getbandborders"></a>Atributu CReBarCtrl:: GetBandBorders

Implementuje chování zprávy Win32 [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders), jak je popsáno v Windows SDK.

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásma, pro které budou ohraničení načtena.

*prc*<br/>
Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která získá ohraničení pásma. Pokud má ovládací prvek matrice styl RBS_BANDBORDERS, každý člen této struktury obdrží počet pixelů v odpovídající straně pásma, které tvoří ohraničení. Pokud ovládací prvek matrice nemá styl RBS_BANDBORDERS, obdrží platné informace pouze levý člen této struktury. Popis stylů ovládacího prvku matrice naleznete v tématu [styly ovládacího prvku matrice](/windows/win32/Controls/rebar-control-styles) v Windows SDK.

##  <a name="getbandcount"></a>  CReBarCtrl::GetBandCount

Implementuje chování zprávy Win32 [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount), jak je popsáno v Windows SDK.

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet pásem přiřazených k ovládacímu prvku.

##  <a name="getbandinfo"></a>  CReBarCtrl::GetBandInfo

Implementuje chování zprávy Win32 [RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo) , jak je popsáno v Windows SDK.

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásma, pro které budou informace načteny.

*prbbi*<br/>
Ukazatel na strukturu [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) , která získá informace o pásce. Musíte nastavit `cbSize` člena této struktury na `sizeof(REBARBANDINFO)` a nastavit `fMask` člena na položky, které chcete načíst před odesláním této zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

##  <a name="getbandmargins"></a>Atributu CReBarCtrl:: GetBandMargins

Načte okraje pásma.

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>Parametry

*pMargins*<br/>
Ukazatel na strukturu [okrajů](/windows/win32/api/uxtheme/ns-uxtheme-margins), která obdrží informace.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [RB_GETBANDMARGINS](/windows/win32/Controls/rb-getbandmargins) zprávy, jak je popsáno v Windows SDK.

##  <a name="getbarheight"></a>Atributu CReBarCtrl:: GetBarHeight

Načte výšku matrice pruhu.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která představuje výšku ovládacího prvku v pixelech.

##  <a name="getbarinfo"></a>  CReBarCtrl::GetBarInfo

Implementuje chování zprávy Win32 [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo), jak je popsáno v Windows SDK.

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>Parametry

*prbi*<br/>
Ukazatel na strukturu [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) , která bude přijímat informace o ovládacím prvku matrice. Před odesláním této zprávy musíte nastavit člena *cbSize* této `sizeof(REBARINFO)` struktury na.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

##  <a name="getbkcolor"></a>  CReBarCtrl::GetBkColor

Implementuje chování zprávy Win32 [RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor), jak je popsáno v Windows SDK.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF, která představuje aktuální výchozí barvu pozadí.

##  <a name="getcolorscheme"></a>Atributu CReBarCtrl:: GetColorScheme

Načte strukturu [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) pro ovládací prvek matrice.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Ukazatel na strukturu [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) , jak je popsáno v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

`COLORSCHEME` Struktura obsahuje barvu zvýraznění tlačítka a barvu tlačítka stín.

##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget

Implementuje chování zprávy Win32 [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget), jak je popsáno v Windows SDK.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) .

##  <a name="getextendedstyle"></a>Atributu CReBarCtrl:: GetExtendedStyle

Získá Rozšířené styly aktuálního ovládacího prvku matrice.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitových kombinací (nebo) příznaků, které označují rozšířené styly. Možné příznaky jsou RBS_EX_SPLITTER a RBS_EX_TRANSPARENT. Další informace naleznete v parametru *dwMask* metody [atributu CReBarCtrl:: SetExtendedStyle](#setextendedstyle) .

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [RB_GETEXTENDEDSTYLE](/windows/win32/Controls/rb-dragmove) , která je popsána v Windows SDK.

##  <a name="getimagelist"></a>  CReBarCtrl::GetImageList

`CImageList` Získá objekt přidružený k ovládacímu prvku matrice.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [atributu CImageList](../../mfc/reference/cimagelist-class.md) . Vrátí hodnotu NULL, pokud není nastaven žádný seznam obrázků pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Tato členská funkce používá informace o velikosti a masce uložené ve struktuře [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) , jak je popsáno v Windows SDK.

##  <a name="getpalette"></a>  CReBarCtrl::GetPalette

Načte aktuální paletu ovládacího prvku matrice.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CPalette –](../../mfc/reference/cpalette-class.md) určující aktuální paletu ovládacího prvku matrice.

### <a name="remarks"></a>Poznámky

Všimněte si, že tato členská `CPalette` funkce používá objekt jako vrácenou hodnotu, nikoli HPALETTE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

##  <a name="getrect"></a>Atributu CReBarCtrl:: GetRect

Implementuje chování zprávy Win32 [RB_GETRECT](/windows/win32/Controls/rb-getrect), jak je popsáno v Windows SDK.

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásma v ovládacím prvku matrice.

*prc*<br/>
Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která bude přijímat hranice matrice pásma.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

##  <a name="getrowcount"></a>  CReBarCtrl::GetRowCount

Implementuje chování zprávy Win32 [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount), jak je popsáno v Windows SDK.

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota UINT, která představuje počet řádků pásma v ovládacím prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

##  <a name="getrowheight"></a>Atributu CReBarCtrl:: GetRowHeight

Implementuje chování zprávy Win32 [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight), jak je popsáno v Windows SDK.

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>Parametry

*uRow*<br/>
Index založený na nule pásma, jehož výška se načetla.

### <a name="return-value"></a>Návratová hodnota

Hodnota UINT, která představuje výšku řádku (v pixelech).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

##  <a name="gettextcolor"></a>  CReBarCtrl::GetTextColor

Implementuje chování zprávy Win32 [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor), jak je popsáno v Windows SDK.

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF, která představuje aktuální výchozí barvu textu.

##  <a name="gettooltips"></a>  CReBarCtrl::GetToolTips

Implementuje chování zprávy Win32 [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips), jak je popsáno v Windows SDK.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) .

### <a name="remarks"></a>Poznámky

Všimněte si, že implementace `GetToolTips` knihovny MFC vrací ukazatel na a `CToolTipCtrl`, nikoli HWND.

##  <a name="hittest"></a>  CReBarCtrl::HitTest

Implementuje chování zprávy Win32 [RB_HITTEST](/windows/win32/Controls/rb-hittest), jak je popsáno v Windows SDK.

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>Parametry

*prbht*<br/>
Ukazatel na strukturu [RBHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo) . Před odesláním zprávy `pt` musí být člen této struktury inicializován do bodu, který bude testován, v souřadnicích klienta.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule pásma v daném bodě, nebo hodnota-1, pokud v daném bodě není matrice žádný proužek.

##  <a name="idtoindex"></a>  CReBarCtrl::IDToIndex

Implementuje chování zprávy Win32 [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex), jak je popsáno v Windows SDK.

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>Parametry

*uBandID*<br/>
Identifikátor definovaný aplikací zadaného pásma, předaný do `wID` členu struktury [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) při vložení pásma.

### <a name="return-value"></a>Návratová hodnota

Index pásma založený na nule, pokud je to úspěšné, nebo-1 v opačném případě. Pokud existují duplicitní indexy pruhů, vrátí se první z nich.

##  <a name="insertband"></a>Atributu CReBarCtrl:: InsertBand

Implementuje chování zprávy Win32 [RB_INSERTBAND](/windows/win32/Controls/rb-insertband), jak je popsáno v Windows SDK.

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parametry

*uIndex*<br/>
Index založený na nule umístění, kam bude pruh vložen. Pokud nastavíte tento parametr na hodnotu-1, ovládací prvek přidá novou oblast do posledního umístění.

*prbbi*<br/>
Ukazatel na strukturu [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) , která definuje pásmo, které má být vloženo. Před voláním této funkce je nutné nastavit člena cbSize `sizeof(REBARBANDINFO)` této struktury na.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

##  <a name="maximizeband"></a>Atributu CReBarCtrl:: MaximizeBand

Změní velikost pásma v ovládacím prvku matrice na jeho největší velikost.

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule z pásma, který se má maximalizovat

### <a name="remarks"></a>Poznámky

Implementuje chování zprávy Win32 [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) s `fIdeal` nastavením na 0, jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

##  <a name="minimizeband"></a>Atributu CReBarCtrl:: MinimizeBand

Změní velikost pásma v ovládacím prvku matrice na jeho nejmenší velikost.

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index s nulovým základem pro minimalizaci pásma.

### <a name="remarks"></a>Poznámky

Implementuje chování zprávy Win32 [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

##  <a name="moveband"></a>  CReBarCtrl::MoveBand

Implementuje chování zprávy Win32 [RB_MOVEBAND](/windows/win32/Controls/rb-moveband), jak je popsáno v Windows SDK.

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>Parametry

*uFrom*<br/>
Index založený na nule pásma, který se má přesunout

*uTo*<br/>
Index nové pozice pásma vycházející z nuly. Hodnota tohoto parametru nesmí být větší než počet pásem minus jedna. Chcete-li získat počet pásem, zavolejte [GetBandCount](#getbandcount).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

##  <a name="pushchevron"></a>  CReBarCtrl::PushChevron

Implementuje chování zprávy Win32 [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron), jak je popsáno v Windows SDK.

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásma, jehož Dvojitá šipka má být vložena.

*lAppValue*<br/>
Aplikace definovaná 32 hodnota bitů. Viz *lAppValue* v [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron) ve Windows SDK.

##  <a name="restoreband"></a>Atributu CReBarCtrl:: RestoreBand

Změní velikost pásma v ovládacím prvku matrice na jeho ideální velikost.

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule z pásma, který se má maximalizovat

### <a name="remarks"></a>Poznámky

Implementuje chování zprávy Win32 [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) s `fIdeal` nastavením na 1, jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

##  <a name="setbandinfo"></a>Atributu CReBarCtrl:: SetBandInfo

Implementuje chování zprávy Win32 [RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo), jak je popsáno v Windows SDK.

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásma pro příjem nových nastavení.

*prbbi*<br/>
Ukazatel na strukturu [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) definující pásmo, které má být vloženo. Před odesláním této `cbSize` zprávy musíte nastavit člena této struktury. `sizeof(REBARBANDINFO)`

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

##  <a name="setbandwidth"></a>Atributu CReBarCtrl:: SetBandWidth

Nastaví šířku určené ukotvené řady v aktuálním ovládacím prvku matrice.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*uBand*|pro Index matrice pásma založený na nule.|
|*cxWidth*|pro Nová šířka matrice pásma (v pixelech)|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [RB_SETBANDWIDTH](/windows/win32/Controls/rb-setbandwidth) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_rebar`která se používá pro přístup k aktuálnímu ovládacímu prvku matrice. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví jednotlivé matrice pásma na stejnou šířku.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

##  <a name="setbarinfo"></a>  CReBarCtrl::SetBarInfo

Implementuje chování zprávy Win32 [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo), jak je popsáno v Windows SDK.

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>Parametry

*prbi*<br/>
Ukazatel na strukturu [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) , která obsahuje informace, které mají být nastaveny. Před odesláním této `cbSize` zprávy musíte nastavit člena této struktury. `sizeof(REBARINFO)`

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

##  <a name="setbkcolor"></a>  CReBarCtrl::SetBkColor

Implementuje chování zprávy Win32 [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor), jak je popsáno v Windows SDK.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
Hodnota COLORREF, která představuje novou výchozí barvu pozadí.

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) , která představuje předchozí výchozí barvu pozadí.

### <a name="remarks"></a>Poznámky

V tomto tématu najdete další informace o tom, kdy se má nastavit barva pozadí, a jak nastavit výchozí nastavení.

##  <a name="setcolorscheme"></a>Atributu CReBarCtrl:: SetColorScheme

Nastaví barevné schéma pro tlačítka na ovládacím prvku matrice.

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Ukazatel na strukturu [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) , jak je popsáno v Windows SDK.

### <a name="remarks"></a>Poznámky

`COLORSCHEME` Struktura zahrnuje barvu zvýraznění tlačítka i barvu stínu tlačítka.

##  <a name="setextendedstyle"></a>Atributu CReBarCtrl:: SetExtendedStyle

Nastaví rozšířené styly pro aktuální ovládací prvek matrice.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwMask*|pro Bitových kombinací (nebo) příznaků, které určují, které příznaky v parametru *dwStyleEx* použít. Použijte jednu nebo více následujících hodnot:<br /><br /> RBS_EX_SPLITTER: Ve výchozím nastavení zobrazí rozdělovač dole ve vodorovném režimu a napravo ve vertikálním režimu.<br /><br /> RBS_EX_TRANSPARENT: Předejte zprávu [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) nadřazenému oknu.|
|*dwStyleEx*|pro Bitová kombinace příznaků (nebo) příznaků, které určují styly, které mají být použity. Chcete-li nastavit styl, zadejte stejný příznak, který se používá v parametru *dwMask* . Chcete-li obnovit styl, zadejte binární hodnotu nula.|

### <a name="return-value"></a>Návratová hodnota

Předchozí rozšířený styl.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle) , která je popsána v Windows SDK.

##  <a name="setimagelist"></a>  CReBarCtrl::SetImageList

Přiřadí seznam obrázků k ovládacímu prvku matrice.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Ukazatel na objekt [atributu CImageList](../../mfc/reference/cimagelist-class.md) obsahující seznam obrázků, který má být přiřazen ovládacímu prvku matrice.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

##  <a name="setowner"></a>Atributu CReBarCtrl:: SetOwner

Implementuje chování zprávy Win32 [RB_SETPARENT](/windows/win32/Controls/rb-setparent), jak je popsáno v Windows SDK.

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na `CWnd` objekt, který má být nastaven jako vlastník ovládacího prvku matrice.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je aktuálním vlastníkem ovládacího prvku matrice.

### <a name="remarks"></a>Poznámky

Všimněte si, že tato členská funkce používá `CWnd` ukazatele na objekty pro aktuální a vybraný vlastník ovládacího prvku matrice místo obslužných rutin systému Windows.

> [!NOTE]
>  Tato členská funkce nemění skutečný nadřazený objekt, který byl nastaven při vytvoření ovládacího prvku. místo toho posílá zprávy s oznámením do okna, které zadáte.

##  <a name="setpalette"></a>  CReBarCtrl::SetPalette

Implementuje chování zprávy Win32 [RB_SETPALETTE](/windows/win32/Controls/rb-setpalette), jak je popsáno v Windows SDK.

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>Parametry

*hPal*<br/>
HPALETTE, který určuje novou paletu, kterou bude ovládací prvek matrice používat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CPalette –](../../mfc/reference/cpalette-class.md) určující předchozí paletu ovládacího prvku matrice.

### <a name="remarks"></a>Poznámky

Všimněte si, že tato členská `CPalette` funkce používá objekt jako vrácenou hodnotu, nikoli HPALETTE.

##  <a name="settextcolor"></a>  CReBarCtrl::SetTextColor

Implementuje chování zprávy Win32 [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor), jak je popsáno v Windows SDK.

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
Hodnota COLORREF, která představuje novou barvu textu v `CReBarCtrl` objektu.

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) představující předchozí barvu textu přidruženou `CReBarCtrl` k objektu

### <a name="remarks"></a>Poznámky

Je k dispozici pro podporu flexibility barev textu v ovládacím prvku matrice.

##  <a name="settooltips"></a>  CReBarCtrl::SetToolTips

Přidruží ovládací prvek popisu tlačítka k ovládacímu prvku matrice.

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>Parametry

*pToolTip*<br/>
Ukazatel na objekt [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Poznámky

`CToolTipCtrl` Objekt musíte zničit, jakmile s ním budete hotovi.

##  <a name="setwindowtheme"></a>Atributu CReBarCtrl:: SetWindowTheme

Nastaví vizuální styl ovládacího prvku matrice.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Ukazatel na řetězec v kódování Unicode, který obsahuje vizuální styl matrice, který se má nastavit.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota se nepoužívá.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme) zprávy, jak je popsáno v Windows SDK.

##  <a name="showband"></a>Atributu CReBarCtrl:: ShowBand

Implementuje chování zprávy Win32 [RB_SHOWBAND](/windows/win32/Controls/rb-showband), jak je popsáno v Windows SDK.

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásma v ovládacím prvku matrice.

*fShow*<br/>
Určuje, zda má být panel zobrazen nebo skryt. Pokud je tato hodnota TRUE, zobrazí se pásmo. V opačném případě bude pruh skrytý.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

##  <a name="sizetorect"></a>Atributu CReBarCtrl:: SizeToRect

Implementuje chování zprávy Win32 [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect), jak je popsáno v Windows SDK.

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
Odkaz na objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který určuje obdélník, na který má být ovládací prvek matrice velikosti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Všimněte si, že tato členská `CRect` funkce používá objekt jako parametr, nikoli `RECT` strukturu.

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
