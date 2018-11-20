---
title: Crebarctrl – třída
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
ms.openlocfilehash: 072fcec4944088ab087a6a39c7d8b916c3bc80e2
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52177027"
---
# <a name="crebarctrl-class"></a>Crebarctrl – třída

Zapouzdřuje funkce ovládacího prvku matrice, což je kontejner pro podřízené okno.

## <a name="syntax"></a>Syntaxe

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|Vytvoří `CReBarCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|Umístí do režimu přetažení myší ovládacího prvku rebar.|
|[CReBarCtrl::Create](#create)|Vytvoří ovládací prvek matrice a připojí ho k `CReBarCtrl` objektu.|
|[CReBarCtrl::CreateEx](#createex)|Vytvoří ovládacím prvkem matrice se zadaným rozšířené styly Windows a připojí ho k `CReBarCtrl` objektu.|
|[CReBarCtrl::DeleteBand](#deleteband)|Odstraní pásmo z ovládacího prvku rebar.|
|[CReBarCtrl::DragMove](#dragmove)|Aktualizace umístění přetažení v ovládacím prvku matrice po volání `BeginDrag`.|
|[CReBarCtrl::EndDrag](#enddrag)|Ukončí operaci přetažení myší ovládacího prvku rebar.|
|[CReBarCtrl::GetBandBorders](#getbandborders)|Načte ohraničení pásu.|
|[CReBarCtrl::GetBandCount](#getbandcount)|Získá počet pruhy aktuálně v ovládacím prvku matrice.|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Načte informace o zadané vzdálené správy v ovládacím prvku matrice.|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Načte okraje pásmo.|
|[CReBarCtrl::GetBarHeight](#getbarheight)|Získá výšku ovládacího prvku rebar.|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Načte informace o ovládacím prvku matrice a seznam obrázků, které používá.|
|[CReBarCtrl::GetBkColor](#getbkcolor)|Načte výchozí barva pozadí ovládacího prvku rebar.|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Načte [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) struktura přidružený k ovládacímu prvku matrice.|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Načte ovládacím prvku matrice `IDropTarget` ukazatel rozhraní.|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Získá rozšířeného stylu aktuální ovládacího prvku rebar.|
|[CReBarCtrl::GetImageList](#getimagelist)|Načte seznam obrázků, které jsou spojené s ovládacím prvkem matrice.|
|[CReBarCtrl::GetPalette](#getpalette)|Načte aktuální palety ovládacího prvku rebar.|
|[CReBarCtrl::GetRect](#getrect)|Načte ohraničující obdélník pro dané pásmo v ovládacím prvku matrice.|
|[CReBarCtrl::GetRowCount](#getrowcount)|Získá počet řádků obsluhy vzdálené správy v ovládacím prvku matrice.|
|[CReBarCtrl::GetRowHeight](#getrowheight)|Získá výšku zadaný řádek v ovládacím prvku matrice.|
|[CReBarCtrl::GetTextColor](#gettextcolor)|Načte výchozí barva textu v ovládacím prvku matrice.|
|[CReBarCtrl::GetToolTips](#gettooltips)|Načte popisovač s žádným ovládacím prvkem popis tlačítka nástroj přidružený k ovládacímu prvku matrice.|
|[CReBarCtrl::HitTest](#hittest)|Určuje, jaká část pruhy matrice je v daném bodě na obrazovce, pokud v tomto okamžiku existuje pruhy matrice.|
|[CReBarCtrl::IDToIndex](#idtoindex)|Převede vzdálené identifikátor (ID) na vzdálené index v ovládacím prvku matrice.|
|[CReBarCtrl::InsertBand](#insertband)|Vloží nový obsluhy vzdálené správy v ovládacím prvku matrice.|
|[CReBarCtrl::MaximizeBand](#maximizeband)|Změní velikost svazku v ovládacím prvku matrice největší velikost.|
|[CReBarCtrl::MinimizeBand](#minimizeband)|Změní velikost svazku v ovládacím prvku matrice nejmenší velikost.|
|[CReBarCtrl::MoveBand](#moveband)|Přesune pásmo z jeden index do jiného.|
|[CReBarCtrl::PushChevron](#pushchevron)|Programově nabízených oznámení dvojitou šipku.|
|[CReBarCtrl::RestoreBand](#restoreband)|Změní velikost svazku v ovládacím prvku matrice na jeho ideální velikost.|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Nastaví vlastnosti existující vzdálenou v ovládacím prvku matrice.|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Nastavuje šířku zadané ukotvených obsluhy vzdálené správy v aktuální ovládacího prvku rebar.|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Nastaví vlastnosti ovládacího prvku matrice.|
|[CReBarCtrl::SetBkColor](#setbkcolor)|Nastaví výchozí barva pozadí ovládacího prvku rebar.|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Nastaví barevné schéma pro tlačítka na ovládacím prvku matrice.|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly pro aktuální ovládacího prvku rebar.|
|[CReBarCtrl::SetImageList](#setimagelist)|Nastaví seznam obrázků v ovládacím prvku matrice.|
|[CReBarCtrl::SetOwner](#setowner)|Nastaví ovládacím prvku matrice nadřazenému oknu.|
|[CReBarCtrl::SetPalette](#setpalette)|Nastaví aktuální palety ovládacího prvku rebar.|
|[CReBarCtrl::SetTextColor](#settextcolor)|Nastaví výchozí barva textu v ovládacím prvku matrice.|
|[CReBarCtrl::SetToolTips](#settooltips)|Přidruží ovládacím prvkem popis tlačítka nástroj ovládacího prvku rebar.|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Nastaví vizuálního stylu ovládacího prvku rebar.|
|[CReBarCtrl::ShowBand](#showband)|Zobrazí nebo skryje dané pásmo v ovládacím prvku matrice.|
|[CReBarCtrl::SizeToRect](#sizetorect)|Vejde do zadaného obdélníku ovládacího prvku matrice.|

## <a name="remarks"></a>Poznámky

Aplikace, ve kterém se nachází ovládacího prvku rebar přiřadí podřízené okno obsaženého v ovládacím prvku matrice na vzdálené matrice. Podřízené okno je obvykle jiný běžný ovládací prvek.

Ovládací prvky matrice obsahovat jeden nebo více pruhy. Každé vzdálené může obsahovat kombinaci úchytu panelu, bitmapy, textový popisek a podřízené okno. Pásmo může obsahovat pouze jednu roli od každého z těchto položek.

Ovládacího prvku rebar. můžete zobrazit podřízené okno přes zadané tapetu. Všechny ovládací pruhy matrice velikost lze změnit, s výjimkou těch, které používají RBBS_FIXEDSIZE style. Podle umístění nebo velikost svazku ovládacího prvku matrice, spravuje ovládacího prvku rebar. velikost a umístění podřízené okno přiřazené k této obsluhy vzdálené správy. Změnit velikost nebo změnit pořadí pruhy v ovládacím prvku, klikněte na tlačítko a přetáhněte úchyt obsluhy vzdálené správy.

Následující obrázek znázorňuje ovládacím prvkem matrice, který má tři pruhy:

- Vzdálené 0 obsahuje ovládacího prvku toolbar bez stromové struktury, transparentní.

- Vzdálené 1 obsahuje oba transparentní standardní a transparentní rozevírací tlačítka.

- Vzdálené 2 obsahuje čtyři standardní tlačítka a pole se seznamem.

   ![Příklad nabídky matrice](../../mfc/reference/media/vc4scc1.gif "příklad nabídky matrice")

## <a name="rebar-control"></a>Matrice – ovládací prvek

Matrice – ovládací prvky podpory:

- Seznamy obrázků.

- Zpracování zpráv.

- Vlastní vykreslení funkce.

- Širokou škálu – styly ovládacích prvků kromě standardní okno styly. Seznam těchto stylů, najdete v části [– styly ovládacího prvku Rebar](/windows/desktop/Controls/rebar-control-styles) v sadě Windows SDK.

Další informace najdete v tématu [používání atributu CReBarCtrl](../../mfc/using-crebarctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag

Implementuje chování zprávy Win32 [RB_BEGINDRAG](/windows/desktop/Controls/rb-begindrag), jak je popsáno v sadě Windows SDK.

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule obsluhy vzdálené správy, který bude mít vliv na operace přetažení myší.

*dwPos*<br/>
Hodnotu DWORD, která obsahuje počáteční myš souřadnice. Vodorovné bod se souřadnicemi je součástí LOWORD a bod se souřadnicemi svislé je součástí HIWORD. Pokud předáte (DWORD) -1, ovládacího prvku rebar. použije pozice myši posledního vlákno ovládacího prvku volá `GetMessage` nebo `PeekMessage`.

##  <a name="create"></a>  CReBarCtrl::Create

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
Určuje kombinaci – styly ovládacího prvku matrice použité pro ovládací prvek. Zobrazit [– styly ovládacího prvku Rebar](/windows/desktop/Controls/rebar-control-styles) v sadě Windows SDK pro seznam podporovaných styly.

*Rect*<br/>
Odkaz na [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, což je umístění a velikost ovládacího prvku rebar.

*pParentWnd*<br/>
Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku rebar. Nesmí být NULL.

*nID*<br/>
Určuje ID ovládacího prvku matrice

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl objekt vytvořen úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Vytvoření ovládacího prvku matrice ve dvou krocích:

1. Volání [atributu CReBarCtrl](#crebarctrl) k vytvoření `CReBarCtrl` objektu.

1. Voláním této členské funkce, která vytvoří ovládací prvek matrice Windows a připojí ho k `CReBarCtrl` objektu.

Při volání `Create`, běžné ovládací prvky jsou inicializovány.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

##  <a name="createex"></a>  CReBarCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ji k `CReBarCtrl` objektu.

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
Určuje rozšířený styl ovládacího prvku vytváří. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) v sadě Windows SDK.

*dwStyle*<br/>
Určuje kombinaci – styly ovládacího prvku matrice použité pro ovládací prvek. Seznam podporovaných stylů, najdete v části [– styly ovládacího prvku Rebar](/windows/desktop/Controls/rebar-control-styles) v sadě Windows SDK.

*Rect*<br/>
Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, který je nadřazeného ovládacího prvku.

*nID*<br/>
ID ovládacího prvku podřízené okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.

##  <a name="crebarctrl"></a>  CReBarCtrl::CReBarCtrl

Vytvoří `CReBarCtrl` objektu.

```
CReBarCtrl();
```

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CReBarCtrl::Create](#create).

##  <a name="deleteband"></a>  CReBarCtrl::DeleteBand

Implementuje chování zprávy Win32 [RB_DELETEBAND](/windows/desktop/Controls/rb-deleteband), jak je popsáno v sadě Windows SDK.

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule obsluhy vzdálené správy, která se má odstranit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je pásmo; úspěšně odstranil. jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

##  <a name="dragmove"></a>  CReBarCtrl::DragMove

Implementuje chování zprávy Win32 [RB_DRAGMOVE](/windows/desktop/Controls/rb-dragmove), jak je popsáno v sadě Windows SDK.

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Hodnota DWORD, který obsahuje novou souřadnic myši. Vodorovné bod se souřadnicemi je součástí LOWORD a bod se souřadnicemi svislé je součástí HIWORD. Pokud předáte (DWORD) -1, ovládacího prvku rebar. použije pozice myši posledního vlákno ovládacího prvku volá `GetMessage` nebo `PeekMessage`.

##  <a name="enddrag"></a>  CReBarCtrl::EndDrag

Implementuje chování zprávy Win32 [RB_ENDDRAG](/windows/desktop/Controls/rb-enddrag), jak je popsáno v sadě Windows SDK.

```
void EndDrag();
```

##  <a name="getbandborders"></a>  CReBarCtrl::GetBandBorders

Implementuje chování zprávy Win32 [RB_GETBANDBORDERS](/windows/desktop/Controls/rb-getbandborders), jak je popsáno v sadě Windows SDK.

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásmo, pro kterou budou načteny ohraničení.

*Čínská lidová republika*<br/>
Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která se zobrazí ohraničení obsluhy vzdálené správy. Pokud ovládacího prvku rebar. má RBS_BANDBORDERS styl, dostane každý člen této struktury počet pixelů na straně odpovídajícího pásmu, které tvoří ohraničení. Pokud ovládacího prvku rebar. nemá žádné RBS_BANDBORDERS styl, obdrží jenom levé člen této struktury platné informace. Popis – styly ovládacího prvku matrice, naleznete v tématu [– styly ovládacího prvku matrice](/windows/desktop/Controls/rebar-control-styles) v sadě Windows SDK.

##  <a name="getbandcount"></a>  CReBarCtrl::GetBandCount

Implementuje chování zprávy Win32 [RB_GETBANDCOUNT](/windows/desktop/Controls/rb-getbandcount), jak je popsáno v sadě Windows SDK.

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet pásma přiřazenou ovládacímu prvku.

##  <a name="getbandinfo"></a>  CReBarCtrl::GetBandInfo

Implementuje chování zprávy Win32 [RB_GETBANDINFO](/windows/desktop/Controls/rb-getbandinfo) jak je popsáno v sadě Windows SDK.

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásmo, pro kterou budou načteny informace.

*prbbi*<br/>
Ukazatel [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) struktuře získávat informace obsluhy vzdálené správy. Je nutné nastavit `cbSize` členem této struktury `sizeof(REBARBANDINFO)` a nastavit `fMask` člena do položky, které chcete načíst před odesláním této zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

##  <a name="getbandmargins"></a>  CReBarCtrl::GetBandMargins

Načte okraje pásmo.

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>Parametry

*pMargins*<br/>
Ukazatel [OKRAJE](/windows/desktop/api/uxtheme/ns-uxtheme-_margins)struktura, která bude dostávat informace.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost [RB_GETBANDMARGINS](/windows/desktop/Controls/rb-getbandmargins) zprávu, jak je popsáno v sadě Windows SDK.

##  <a name="getbarheight"></a>  CReBarCtrl::GetBarHeight

Načte výška panelu matrice.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která představuje výšku v pixelech, ovládacího prvku.

##  <a name="getbarinfo"></a>  CReBarCtrl::GetBarInfo

Implementuje chování zprávy Win32 [RB_GETBARINFO](/windows/desktop/Controls/rb-getbarinfo), jak je popsáno v sadě Windows SDK.

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>Parametry

*prbi*<br/>
Ukazatel [REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo) struktura, která bude dostávat informace ovládacího prvku rebar. Je nutné nastavit *cbSize* členem této struktury `sizeof(REBARINFO)` před odesláním této zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

##  <a name="getbkcolor"></a>  CReBarCtrl::GetBkColor

Implementuje chování zprávy Win32 [RB_GETBKCOLOR](/windows/desktop/Controls/rb-getbkcolor), jak je popsáno v sadě Windows SDK.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

COLORREF hodnotu představující aktuální výchozí barvu pozadí.

##  <a name="getcolorscheme"></a>  CReBarCtrl::GetColorScheme

Načte [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) struktura ovládacího prvku rebar.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Ukazatel [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) struktury, jak je popsáno v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

`COLORSCHEME` Struktura zahrnuje barvu zvýraznění tlačítka a tlačítka Barva stínu.

##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget

Implementuje chování zprávy Win32 [RB_GETDROPTARGET](/windows/desktop/Controls/rb-getdroptarget), jak je popsáno v sadě Windows SDK.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) rozhraní.

##  <a name="getextendedstyle"></a>  CReBarCtrl::GetExtendedStyle

Získá rozšířené styly aktuálního ovládacího prvku rebar.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová kombinace (nebo) příznaků, které označují rozšířené styly. Je to možné příznaky jsou RBS_EX_SPLITTER a RBS_EX_TRANSPARENT. Další informace najdete v tématu *dwMask* parametr [CReBarCtrl::SetExtendedStyle](#setextendedstyle) metody.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [RB_GETEXTENDEDSTYLE](/windows/desktop/Controls/rb-dragmove) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getimagelist"></a>  CReBarCtrl::GetImageList

Získá `CImageList` objektu souvisejícího s ovládacím prvkem matrice.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [atributu CImageList](../../mfc/reference/cimagelist-class.md) objektu. Vrátí hodnotu NULL, pokud je pro ovládací prvek nastavené žádné seznamu obrázků.

### <a name="remarks"></a>Poznámky

Tato členská funkce používá velikost a maska informací uložených v [REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo) struktury, jak je popsáno v sadě Windows SDK.

##  <a name="getpalette"></a>  CReBarCtrl::GetPalette

Načte aktuální palety ovládacího prvku rebar.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cpalette –](../../mfc/reference/cpalette-class.md) určující aktuální palety ovládacího prvku rebar.

### <a name="remarks"></a>Poznámky

Všimněte si, že tato členská funkce používá `CPalette` jako jeho návratovou hodnotu, nikoli HPALETTE objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

##  <a name="getrect"></a>  CReBarCtrl::GetRect

Implementuje chování zprávy Win32 [RB_GETRECT](/windows/desktop/Controls/rb-getrect), jak je popsáno v sadě Windows SDK.

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule vzdálené správy v rámci ovládacího prvku rebar.

*Čínská lidová republika*<br/>
Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která bude dostávat hranice vzdálené matrice.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

##  <a name="getrowcount"></a>  CReBarCtrl::GetRowCount

Implementuje chování zprávy Win32 [RB_GETROWCOUNT](/windows/desktop/Controls/rb-getrowcount), jak je popsáno v sadě Windows SDK.

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>Návratová hodnota

UINT hodnotu, která představuje počet vzdálené řádky v ovládacím prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

##  <a name="getrowheight"></a>  CReBarCtrl::GetRowHeight

Implementuje chování zprávy Win32 [RB_GETROWHEIGHT](/windows/desktop/Controls/rb-getrowheight), jak je popsáno v sadě Windows SDK.

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>Parametry

*uRow*<br/>
Index založený na nule, který bude mít výšku načíst pásma.

### <a name="return-value"></a>Návratová hodnota

UINT hodnotu, která představuje výška v pixelech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

##  <a name="gettextcolor"></a>  CReBarCtrl::GetTextColor

Implementuje chování zprávy Win32 [RB_GETTEXTCOLOR](/windows/desktop/Controls/rb-gettextcolor), jak je popsáno v sadě Windows SDK.

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>Návratová hodnota

COLORREF hodnotu představující aktuální výchozí barva textu.

##  <a name="gettooltips"></a>  CReBarCtrl::GetToolTips

Implementuje chování zprávy Win32 [RB_GETTOOLTIPS](/windows/desktop/Controls/rb-gettooltips), jak je popsáno v sadě Windows SDK.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objektu.

### <a name="remarks"></a>Poznámky

Všimněte si, že implementace MFC `GetToolTips` vrací ukazatel na `CToolTipCtrl`, místo popisovačem HWND.

##  <a name="hittest"></a>  CReBarCtrl::HitTest

Implementuje chování zprávy Win32 [RB_HITTEST](/windows/desktop/Controls/rb-hittest), jak je popsáno v sadě Windows SDK.

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>Parametry

*prbht*<br/>
Ukazatel [RBHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_rb_hittestinfo) struktury. Před odesláním zprávy, `pt` člena této struktury musí být inicializován na bod, který se má testovat, v souřadnicích klienta.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule obsluhy vzdálené správy na časovém okamžiku nebo -1, pokud žádné vzdálené matrice byl na místě.

##  <a name="idtoindex"></a>  CReBarCtrl::IDToIndex

Implementuje chování zprávy Win32 [RB_IDTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb774496), jak je popsáno v sadě Windows SDK.

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>Parametry

*uBandID*<br/>
Předaný identifikátor definovaného aplikací zadané obsluhy vzdálené správy `wID` člena [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) struktury při vložení pásmo.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule obsluhy vzdálené správy v případě úspěchu, nebo jinak -1. Pokud existují duplicitní obsluhy vzdálené správy indexů, vrátí se první z nich.

##  <a name="insertband"></a>  CReBarCtrl::InsertBand

Implementuje chování zprávy Win32 [RB_INSERTBAND](/windows/desktop/Controls/rb-insertband), jak je popsáno v sadě Windows SDK.

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parametry

*uIndex*<br/>
Z nuly vycházející index umístění, kde se vloží vzdálené. Pokud tento parametr nastavíte na hodnotu -1, ovládací prvek přidá nový obsluhy vzdálené správy na posledním místě.

*prbbi*<br/>
Ukazatel [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) strukturu, která definuje obsluhy vzdálené správy, která se má vložit. Je nutné nastavit *cbSize* členem této struktury `sizeof(REBARBANDINFO)` před voláním této funkce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

##  <a name="maximizeband"></a>  CReBarCtrl::MaximizeBand

Změní velikost svazku v ovládacím prvku matrice největší velikost.

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásmo maximalizovat.

### <a name="remarks"></a>Poznámky

Implementuje chování zprávy Win32 [RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband) s `fIdeal` nastavena na hodnotu 0, jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

##  <a name="minimizeband"></a>  CReBarCtrl::MinimizeBand

Změní velikost svazku v ovládacím prvku matrice nejmenší velikost.

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule vzdálené minimalizaci.

### <a name="remarks"></a>Poznámky

Implementuje chování zprávy Win32 [RB_MINIMIZEBAND](/windows/desktop/Controls/rb-minimizeband), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

##  <a name="moveband"></a>  CReBarCtrl::MoveBand

Implementuje chování zprávy Win32 [RB_MOVEBAND](/windows/desktop/Controls/rb-moveband), jak je popsáno v sadě Windows SDK.

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>Parametry

*uFrom*<br/>
Index založený na nule vzdálené přesunout.

*utomatická*<br/>
Index založený na nule na nové pozici obsluhy vzdálené správy. Hodnota tohoto parametru musí být nikdy větší než počet pásem mínus jedna. Chcete-li získat číslo pruhy, zavolejte [GetBandCount](#getbandcount).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

##  <a name="pushchevron"></a>  CReBarCtrl::PushChevron

Implementuje chování zprávy Win32 [RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron), jak je popsáno v sadě Windows SDK.

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule obsluhy vzdálené správy, jejichž šipky je doručit bez vyžádání.

*lAppValue*<br/>
Aplikace je definována hodnota 32-bit. Zobrazit *lAppValue* v [RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron) v sadě Windows SDK.

##  <a name="restoreband"></a>  CReBarCtrl::RestoreBand

Změní velikost svazku v ovládacím prvku matrice na jeho ideální velikost.

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule pásmo maximalizovat.

### <a name="remarks"></a>Poznámky

Implementuje chování zprávy Win32 [RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband) s `fIdeal` nastavena na hodnotu 1, jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

##  <a name="setbandinfo"></a>  CReBarCtrl::SetBandInfo

Implementuje chování zprávy Win32 [RB_SETBANDINFO](/windows/desktop/Controls/rb-setbandinfo), jak je popsáno v sadě Windows SDK.

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule obsluhy vzdálené správy, aby přijaly nové nastavení.

*prbbi*<br/>
Ukazatel [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) strukturu, která definuje obsluhy vzdálené správy, která se má vložit. Je nutné nastavit `cbSize` členem této struktury `sizeof(REBARBANDINFO)` před odesláním této zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

##  <a name="setbandwidth"></a>  CReBarCtrl::SetBandWidth

Nastavuje šířku zadané ukotvených obsluhy vzdálené správy v aktuální ovládacího prvku rebar.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*uBand*|[in] Index založený na nule pruhy matrice.|
|*cxWidth*|[in] Novou šířku pásma matrice, v pixelech.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je metoda úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [RB_SETBANDWIDTH](/windows/desktop/Controls/rb-setbandwidth) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_rebar`, která je pro přístup k aktuálnímu ovládacímu prvku matrice. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví každé matrice pásmo být stejnou šířku.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

##  <a name="setbarinfo"></a>  CReBarCtrl::SetBarInfo

Implementuje chování zprávy Win32 [RB_SETBARINFO](/windows/desktop/Controls/rb-setbarinfo), jak je popsáno v sadě Windows SDK.

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>Parametry

*prbi*<br/>
Ukazatel [REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo) strukturu, která obsahuje informace o nastavení. Je nutné nastavit `cbSize` členem této struktury `sizeof(REBARINFO)` před odesláním této zprávy

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

##  <a name="setbkcolor"></a>  CReBarCtrl::SetBkColor

Implementuje chování zprávy Win32 [RB_SETBKCOLOR](/windows/desktop/Controls/rb-setbkcolor), jak je popsáno v sadě Windows SDK.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
COLORREF hodnotu, která představuje výchozí barvu pozadí.

### <a name="return-value"></a>Návratová hodnota

A [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která představuje předchozí výchozí barvu pozadí.

### <a name="remarks"></a>Poznámky

V tomto tématu pro další informace o kdy se má nastavit barvu pozadí a jak nastavit výchozí.

##  <a name="setcolorscheme"></a>  CReBarCtrl::SetColorScheme

Nastaví barevné schéma pro tlačítka na ovládacím prvku matrice.

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Ukazatel [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) struktury, jak je popsáno v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

`COLORSCHEME` Struktura zahrnuje barvu zvýraznění tlačítka a tlačítka Barva stínu.

##  <a name="setextendedstyle"></a>  CReBarCtrl::SetExtendedStyle

Nastaví rozšířené styly pro aktuální ovládacího prvku rebar.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwMask*|[in] Bitová kombinace (OR) mezi příznaky, které určují, které příznaky v *dwStyleEx* použít parametr. Použijte jednu nebo více z následujících hodnot:<br /><br /> RBS_EX_SPLITTER: Ve výchozím nastavení, Zobrazit příčky v dolní části ve vodorovném režimu a na pravé straně ve svislém režimu.<br /><br /> RBS_EX_TRANSPARENT: Předávání [WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd) zprávu nadřazenému oknu.|
|*dwStyleEx*|[in] Bitová kombinace (nebo) příznaků, které určují, styly, které chcete použít. Pokud chcete nastavit styl, zadejte stejný příznak, který se používá v *dwMask* parametru. Pokud chcete resetovat styl, zadejte binární nulu.|

### <a name="return-value"></a>Návratová hodnota

Předchozí rozšířený styl.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [RB_SETEXTENDEDSTYLE](/windows/desktop/Controls/rb-setextendedstyle) zprávu, která je popsána v sadě Windows SDK.

##  <a name="setimagelist"></a>  CReBarCtrl::SetImageList

Seznam obrázků přiřadí ovládacím prvkem matrice.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Ukazatel [atributu CImageList](../../mfc/reference/cimagelist-class.md) objekt, který obsahuje seznam obrázků má být přiřazena k ovládacího prvku rebar.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

##  <a name="setowner"></a>  CReBarCtrl::SetOwner

Implementuje chování zprávy Win32 [RB_SETPARENT](/windows/desktop/Controls/rb-setparent), jak je popsáno v sadě Windows SDK.

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel `CWnd` objektu, který chcete nastavit jako vlastníka ovládacího prvku rebar.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je aktuálním vlastníkem ovládacího prvku rebar.

### <a name="remarks"></a>Poznámky

Všimněte si, že tato členská funkce používá ukazatele na `CWnd` objekty pro aktuální a vybrané vlastník ovládacího prvku rebar, nikoli zpracovává do systému windows.

> [!NOTE]
>  Tato členská funkce nezmění skutečné nadřazeného objektu, který byl nastaven při vytvoření ovládacího prvku; Místo toho odešle zprávy s oznámením v okně, které zadáte.

##  <a name="setpalette"></a>  CReBarCtrl::SetPalette

Implementuje chování zprávy Win32 [RB_SETPALETTE](/windows/desktop/Controls/rb-setpalette), jak je popsáno v sadě Windows SDK.

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>Parametry

*hPal*<br/>
HPALETTE, určující nové paletu, která bude používat ovládacího prvku rebar.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cpalette –](../../mfc/reference/cpalette-class.md) určující předchozí palety ovládacího prvku rebar.

### <a name="remarks"></a>Poznámky

Všimněte si, že tato členská funkce používá `CPalette` jako jeho návratovou hodnotu, nikoli HPALETTE objekt.

##  <a name="settextcolor"></a>  CReBarCtrl::SetTextColor

Implementuje chování zprávy Win32 [RB_SETTEXTCOLOR](/windows/desktop/Controls/rb-settextcolor), jak je popsáno v sadě Windows SDK.

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
COLORREF hodnotu, která představuje nový text barvy v `CReBarCtrl` objektu.

### <a name="return-value"></a>Návratová hodnota

[COLORREF](/windows/desktop/gdi/colorref) přidružené hodnotu představující na předchozí barvu textu `CReBarCtrl` objektu.

### <a name="remarks"></a>Poznámky

Poskytuje pro podporu flexibilitu barvu textu v ovládacím prvku matrice.

##  <a name="settooltips"></a>  CReBarCtrl::SetToolTips

Přidruží ovládacím prvkem popis tlačítka nástroj s ovládacím prvkem matrice.

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>Parametry

*pToolTip*<br/>
Ukazatel [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objektu

### <a name="remarks"></a>Poznámky

Budete muset zničit `CToolTipCtrl` objektu, jakmile budete hotovi s ním.

##  <a name="setwindowtheme"></a>  CReBarCtrl::SetWindowTheme

Nastaví vizuálního stylu ovládacího prvku rebar.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Ukazatel na řetězec znaků Unicode, který obsahuje vizuální styl matrice nastavení.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota se nepoužívá.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost [RB_SETWINDOWTHEME](/windows/desktop/Controls/rb-setwindowtheme) zprávu, jak je popsáno v sadě Windows SDK.

##  <a name="showband"></a>  CReBarCtrl::ShowBand

Implementuje chování zprávy Win32 [RB_SHOWBAND](/windows/desktop/Controls/rb-showband), jak je popsáno v sadě Windows SDK.

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>Parametry

*uBand*<br/>
Index založený na nule vzdálené správy v rámci ovládacího prvku rebar.

*fShow*<br/>
Označuje, pokud vzdálené zobrazen nebo skryt. Pokud je tato hodnota TRUE, zobrazí se pásmo. V opačném případě se skryjí pásmo.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

##  <a name="sizetorect"></a>  CReBarCtrl::SizeToRect

Implementuje chování zprávy Win32 [RB_SIZETORECT](/windows/desktop/Controls/rb-sizetorect), jak je popsáno v sadě Windows SDK.

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odkaz na [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který určuje obdélník, který by měl velikost ovládacího prvku rebar.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Všimněte si, že tato členská funkce používá `CRect` objektu jako parametr, spíše než `RECT` struktury.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

