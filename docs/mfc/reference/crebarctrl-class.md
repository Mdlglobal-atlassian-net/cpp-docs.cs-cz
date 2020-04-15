---
title: Třída CRebarctrl
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
ms.openlocfilehash: 776892d71e2cb0f5d57512754cd7fa12730eb044
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367445"
---
# <a name="crebarctrl-class"></a>Třída CRebarctrl

Zapouzdřuje funkce ovládacího prvku výztuže, což je kontejner pro podřízené okno.

## <a name="syntax"></a>Syntaxe

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Crebarctrl::crebarctrl](#crebarctrl)|Vytvoří `CReBarCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRebarctrl::BeginDrag](#begindrag)|Přepne ovládací prvek výztuže do režimu přetahování.|
|[CRebarctrl::Vytvořit](#create)|Vytvoří ovládací prvek výztuže `CReBarCtrl` a připojí jej k objektu.|
|[CRebarctrl::CreateEx](#createex)|Vytvoří ovládací prvek výztuže se zadanými `CReBarCtrl` rozšířenými styly systému Windows a připojí jej k objektu.|
|[CReBarCtrl::DeleteBand](#deleteband)|Odstraní pásmo z ovládacího prvku výztuže.|
|[CReBarCtrl::DragMove](#dragmove)|Aktualizuje pozici přetažení v ovládacím prvku `BeginDrag`výztuže po volání .|
|[Crebarctrl::EndDrag](#enddrag)|Ukončí operaci přetažení ovládacího prvku výztuže.|
|[Crebarctrl::GetBandBorders](#getbandborders)|Načte hranice pásma.|
|[CRebarctrl::GetBandCount](#getbandcount)|Načte počet pásem aktuálně v ovládacím prvku výztuže.|
|[Crebarctrl::GetBandInfo](#getbandinfo)|Načte informace o zadaném pásmu v ovládacím prvku výztuže.|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Načte okraje pásma.|
|[Crebarctrl::GetBarHeight](#getbarheight)|Načte výšku ovládacího prvku výztuže.|
|[Crebarctrl::GetBarInfo](#getbarinfo)|Načte informace o ovládacím prvku výztuže a seznamu obrázků, který používá.|
|[CReBarCtrl::GetBkColor](#getbkcolor)|Načte výchozí barvu pozadí ovládacího prvku výztuže.|
|[Crebarctrl::Getcolorscheme](#getcolorscheme)|Načte strukturu [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) přidruženou k ovládacímu prvku výztuže.|
|[Crebarctrl::GetDropTarget](#getdroptarget)|Načte ukazatel rozhraní ovládacího prvku výztuže. `IDropTarget`|
|[Crebarctrl::GetextendedStyle](#getextendedstyle)|Získá rozšířený styl aktuální hojné pryska ovládacího prvku.|
|[Crebarctrl::GetImageList](#getimagelist)|Načte seznam obrázků přidružený k ovládacímu prvku výztuže.|
|[Crebarctrl::GetPalette](#getpalette)|Načte aktuální paletu ovládacího prvku výztuže.|
|[CReBarCtrl::GetRect](#getrect)|Načte ohraničovací obdélník pro daný pás v ovládacím prvku výztuže.|
|[CRebarctrl::GetRowCount](#getrowcount)|Načte počet řádků pásma v ovládacím prvku výztuže.|
|[Crebarctrl::GetRowHeight](#getrowheight)|Načte výšku zadaného řádku v ovládacím prvku výztuže.|
|[Crebarctrl::GetTextColor](#gettextcolor)|Načte výchozí barvu textu ovládacího prvku výztuže.|
|[Crebarctrl::GettoolTips](#gettooltips)|Načte úchyt do libovolného ovládacího prvku špičky nástroje přidruženého k ovládacímu prvku výztuže.|
|[Crebarctrl::HitTest](#hittest)|Určuje, která část pásma výztuže je v daném bodě na obrazovce, pokud v tomto okamžiku existuje pásmo výztuže.|
|[Crebarctrl::IDToIndex](#idtoindex)|Převede identifikátor pásma (ID) na index pásma v ovládacím prvku výztuže.|
|[CRebarctrl::InsertBand](#insertband)|Vloží nový pás do ovládacího prvku výztuže.|
|[CRebarctrl::Maximalizovat pásmo](#maximizeband)|Změní velikost pásu v ovládacím prvku výztuže na jeho největší velikost.|
|[Crebarctrl::minimalizovat pásmo](#minimizeband)|Změní velikost pásu v ovládacím prvku výztuže na jeho nejmenší velikost.|
|[Crebarctrl::MoveBand](#moveband)|Přesune pásmo z jednoho indexu do druhého.|
|[CReBarCtrl::PushChevron](#pushchevron)|Programově posune prýmek.|
|[CRebarctrl::RestoreBand](#restoreband)|Změní velikost pásu v ovládacím prvku výztuže na jeho ideální velikost.|
|[Crebarctrl::SetBandInfo](#setbandinfo)|Nastaví charakteristiky existujícího pásma v ovládacím prvku výztuže.|
|[Crebarctrl::SetBandWidth](#setbandwidth)|Nastaví šířku zadaného ukotveného pásma v aktuálním ovládacím prvku výztuže.|
|[Crebarctrl::SetBarInfo](#setbarinfo)|Nastaví charakteristiky ovládacího prvku výztuže.|
|[CReBarCtrl::SetBkColor](#setbkcolor)|Nastaví výchozí barvu pozadí ovládacího prvku výztuže.|
|[CRebarctrl::SetColorScheme](#setcolorscheme)|Nastaví barevné schéma tlačítek v ovládacím prvku výztuže.|
|[Crebarctrl::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly pro aktuální ovládací prvek výztuže.|
|[Crebarctrl::SetImageList](#setimagelist)|Nastaví seznam obrázků ovládacího prvku výztuže.|
|[CRebarctrl::SetOwner](#setowner)|Nastaví okno vlastníka ovládacího prvku výztuže.|
|[Crebarctrl::SetPalette](#setpalette)|Nastaví aktuální paletu ovládacího prvku výztuže.|
|[CRebarctrl::SettextColor](#settextcolor)|Nastaví výchozí barvu textu ovládacího prvku výztuže.|
|[Crebarctrl::settooltips](#settooltips)|Přidruží ovládací prvek špičky nástroje k ovládacímu prvku výztuže.|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Nastaví vizuální styl ovládacího prvku výztuže.|
|[CRebarctrl::ShowBand](#showband)|Zobrazí nebo skryje dané pásmo v ovládacím prvku výztuže.|
|[CReBarCtrl::SizeToRect](#sizetorect)|Přizpůsobí ovládací prvek výztuže do zadaného obdélníku.|

## <a name="remarks"></a>Poznámky

Aplikace, ve které je umístěn ovládací prvek výztuže, přiřadí podřízené okno obsažené ovládacím prvkem výztuže k pásmu výztuže. Podřízené okno je obvykle jiný společný ovládací prvek.

Ovládací prvky výztuže obsahují jedno nebo více pásem. Každé pásmo může obsahovat kombinaci úchytu, rastrového grafu, textového popisku a podřízeného okna. Pásmo může obsahovat pouze jednu z těchto položek.

Ovládací prvek výztuže může zobrazit podřízené okno nad zadanou bitmapu pozadí. Změnit velikost všech ovládacích pásem výztuže lze změnit s výjimkou těch, které používají styl RBBS_FIXEDSIZE. Při změně umístění nebo změny velikosti ovládacího pásma výztuže řídí ovládací prvek výztuže řídí velikost a umístění podřízeného okna přiřazeného k tomuto pásmu. Chcete-li změnit velikost nebo změnit pořadí pásem v ovládacím prvku, klepněte a přetáhněte úchopovou lištu pásma.

Následující obrázek znázorňuje ovládací prvek výztuže, který má tři pásma:

- Pásmo 0 obsahuje plochý průhledný ovládací prvek panelu nástrojů.

- Pásmo 1 obsahuje transparentní standardní i průhledná rozevírací tlačítka.

- Pásmo 2 obsahuje pole se seznamem a čtyři standardní tlačítka.

   ![Příklad nabídky výztuže](../../mfc/reference/media/vc4scc1.gif "Příklad nabídky výztuže")

## <a name="rebar-control"></a>Ovládací prvek výztuže

Podpora ovládacích prvků výztuže:

- Seznamy obrázků.

- Zpracování zpráv.

- Vlastní funkce kreslení.

- Kromě standardních stylů oken je k dispozici také řada stylů ovládacích prvků. Seznam těchto stylů naleznete v tématu [Styly ovládacích prvků výztuže](/windows/win32/Controls/rebar-control-styles) v sadě Windows SDK.

Další informace naleznete [v tématu Použití crebarctrl](../../mfc/using-crebarctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a>CRebarctrl::BeginDrag

Implementuje chování [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)zprávy Win32 , jak je popsáno v sadě Windows SDK.

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma, které ovlivní operace přetažení myší.

*dwPos*<br/>
Hodnota DWORD, která obsahuje počáteční souřadnice myši. Horizontální souřadnice je obsažena v LOWORD a svislá souřadnice je obsažena v HIWORD. Pokud předáte (DWORD)-1, ovládací prvek výztuže použije pozici myši při `GetMessage` posledním `PeekMessage`volání vlákna ovládacího prvku nebo .

## <a name="crebarctrlcreate"></a><a name="create"></a>CRebarctrl::Vytvořit

Vytvoří ovládací prvek výztuže `CReBarCtrl` a připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje kombinaci stylů ovládacích prvků použitých na ovládací prvek. Seznam podporovaných stylů najdete v tématu [Styly ovládacích prvků výztuže](/windows/win32/Controls/rebar-control-styles) v sadě Windows SDK.

*Rect*<br/>
Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/previous-versions/dd162897\(v=vs.85\)) struktury, což je umístění a velikost ovládacího prvku výztuže.

*pParentWnd*<br/>
Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku výztuže. Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku výztuže.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl objekt úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Vytvořte ovládací prvek výztuže ve dvou krocích:

1. Volání [CReBarCtrl](#crebarctrl) k `CReBarCtrl` vytvoření objektu.

1. Volání této členské funkce, která vytvoří ovládací prvek výztuže systému Windows a připojí jej k objektu. `CReBarCtrl`

Při volání `Create`jsou inicializovány běžné ovládací prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a>CRebarctrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a `CReBarCtrl` přidruží jej k objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyl*<br/>
Určuje rozšířený styl vytvářeného ovládacího prvku. Seznam rozšířených stylů systému Windows naleznete v parametru *dwExStyle* pro [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*dwStyl*<br/>
Určuje kombinaci stylů ovládacích prvků použitých na ovládací prvek. Seznam podporovaných stylů najdete v tématu [Styly ovládacích prvků výztuže](/windows/win32/Controls/rebar-control-styles) v sadě Windows SDK.

*Rect*<br/>
Odkaz na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu popisující velikost a umístění okna, které mají být vytvořeny, v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*Nid*<br/>
ID podřízeného okna ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` funkce [Vytvořit](#create) použijte použití rozšířených stylů systému Windows určených **předmluvou**rozšířeného stylu systému Windows WS_EX_ .

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a>Crebarctrl::crebarctrl

Vytvoří `CReBarCtrl` objekt.

```
CReBarCtrl();
```

### <a name="example"></a>Příklad

  Viz příklad [crebarctrl::create](#create).

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a>CReBarCtrl::DeleteBand

Implementuje chování zprávy Win32 [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband), jak je popsáno v sadě Windows SDK.

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma, které má být odstraněno.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo pásmo úspěšně odstraněno; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a>CReBarCtrl::DragMove

Implementuje chování zprávy Win32 [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove), jak je popsáno v sadě Windows SDK.

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Hodnota DWORD, která obsahuje nové souřadnice myši. Horizontální souřadnice je obsažena v LOWORD a svislá souřadnice je obsažena v HIWORD. Pokud předáte (DWORD)-1, ovládací prvek výztuže použije pozici myši při `GetMessage` posledním `PeekMessage`volání vlákna ovládacího prvku nebo .

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a>Crebarctrl::EndDrag

Implementuje chování [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)zprávy Win32 , jak je popsáno v sadě Windows SDK.

```
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a>Crebarctrl::GetBandBorders

Implementuje chování zprávy Win32 [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders), jak je popsáno v sadě Windows SDK.

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma, pro které budou načtena ohraničení.

*Člr*<br/>
Ukazatel na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu, která obdrží ohraničení pásma. Pokud má ovládací prvek výztuže RBS_BANDBORDERS styl, každý člen této struktury obdrží počet pixelů na odpovídající straně pásma, které tvoří ohraničení. Pokud ovládací prvek výztuže nemá styl RBS_BANDBORDERS, pouze levý člen této struktury obdrží platné informace. Popis stylů ovládacích prvků naleznete v tématu [Styly ovládacích prvků výztuže](/windows/win32/Controls/rebar-control-styles) v sadě Windows SDK.

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a>CRebarctrl::GetBandCount

Implementuje chování zprávy Win32 [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount), jak je popsáno v sadě Windows SDK.

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet pásem přiřazených ovládacímu prvku.

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a>Crebarctrl::GetBandInfo

Implementuje chování zprávy Win32 [RB_GETBANDINFO,](/windows/win32/Controls/rb-getbandinfo) jak je popsáno v sadě Windows SDK.

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma, pro které budou načteny informace.

*prbbi*<br/>
Ukazatel na strukturu [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) pro příjem informací o pásmu. Je nutné `cbSize` nastavit člen této `sizeof(REBARBANDINFO)` struktury `fMask` a nastavit člen na položky, které chcete načíst před odesláním této zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a>CReBarCtrl::GetBandMargins

Načte okraje pásma.

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>Parametry

*pMary*<br/>
Ukazatel na strukturu [MARGINS,](/windows/win32/api/uxtheme/ns-uxtheme-margins)která obdrží informace.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [zprávy RB_GETBANDMARGINS,](/windows/win32/Controls/rb-getbandmargins) jak je popsáno v sadě Windows SDK.

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a>Crebarctrl::GetBarHeight

Načte výšku výztuže.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která představuje výšku ovládacího prvku v obrazových bodech.

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a>Crebarctrl::GetBarInfo

Implementuje chování zprávy Win32 [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo), jak je popsáno v sadě Windows SDK.

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>Parametry

*prbi*<br/>
Ukazatel na strukturu [REBARINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) která obdrží informace o ovládacím prvku výztuže. Před odesláním této zprávy je `sizeof(REBARINFO)` nutné nastavit člen *cbSize* této struktury.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a>CReBarCtrl::GetBkColor

Implementuje chování zprávy Win32 [RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor), jak je popsáno v sadě Windows SDK.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF, která představuje aktuální výchozí barvu pozadí.

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a>Crebarctrl::Getcolorscheme

Načte [colorscheme](/windows/win32/api/commctrl/ns-commctrl-colorscheme) strukturu pro ovládací prvek výztuže.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Ukazatel na strukturu [COLORSCHEME,](/windows/win32/api/commctrl/ns-commctrl-colorscheme) jak je popsáno v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Struktura `COLORSCHEME` zahrnuje barvu zvýraznění tlačítka a barvu stínu tlačítka.

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a>Crebarctrl::GetDropTarget

Implementuje chování [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)zprávy Win32 , jak je popsáno v sadě Windows SDK.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní [IDropTarget.](/windows/win32/api/oleidl/nn-oleidl-idroptarget)

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a>Crebarctrl::GetextendedStyle

Získá rozšířené styly aktuální ovládací prvek výztuže.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová kombinace (OR) příznaků, které označují rozšířené styly. Možné příznaky jsou RBS_EX_SPLITTER a RBS_EX_TRANSPARENT. Další informace naleznete v parametru *dwMask* metody [CReBarCtrl::SetExtendedStyle.](#setextendedstyle)

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu RB_GETEXTENDEDSTYLE,](/windows/win32/Controls/rb-dragmove) která je popsána v sadě Windows SDK.

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a>Crebarctrl::GetImageList

Získá `CImageList` objekt přidružený k ovládacímu prvku výztuže.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CImageList.](../../mfc/reference/cimagelist-class.md) Vrátí hodnotu NULL, pokud pro ovládací prvek není nastaven žádný seznam obrázků.

### <a name="remarks"></a>Poznámky

Tato členská funkce používá informace o velikosti a masce uložené ve struktuře [REBARINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) jak je popsáno v sadě Windows SDK.

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a>Crebarctrl::GetPalette

Načte aktuální paletu ovládacího prvku výztuže.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CPalette](../../mfc/reference/cpalette-class.md) určující aktuální paletu ovládacího prvku výztuže.

### <a name="remarks"></a>Poznámky

Všimněte si, že `CPalette` tato členská funkce používá objekt jako jeho vrácená hodnota, nikoli HPALETTE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a>CReBarCtrl::GetRect

Implementuje chování zprávy Win32 [RB_GETRECT](/windows/win32/Controls/rb-getrect), jak je popsáno v sadě Windows SDK.

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma v ovládacím prvku výztuže.

*Člr*<br/>
Ukazatel na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu, která obdrží hranice pásma výztuže.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a>CRebarctrl::GetRowCount

Implementuje chování zprávy Win32 [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount), jak je popsáno v sadě Windows SDK.

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota UINT, která představuje počet řádků pásma v ovládacím prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a>Crebarctrl::GetRowHeight

Implementuje chování [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)zprávy Win32 , jak je popsáno v sadě Windows SDK.

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>Parametry

*uRow*<br/>
Nulový index pásma, který bude mít jeho výšku načteny.

### <a name="return-value"></a>Návratová hodnota

Hodnota UINT, která představuje výšku řádku v obrazových bodech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a>Crebarctrl::GetTextColor

Implementuje chování zprávy Win32 [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor), jak je popsáno v sadě Windows SDK.

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF, která představuje aktuální výchozí barvu textu.

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a>Crebarctrl::GettoolTips

Implementuje chování zprávy Win32 [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips), jak je popsáno v sadě Windows SDK.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [ctooltipctrl](../../mfc/reference/ctooltipctrl-class.md) objekt.

### <a name="remarks"></a>Poznámky

Všimněte si, že `GetToolTips` mfc implementace `CToolTipCtrl`vrátí ukazatel na , spíše než HWND.

## <a name="crebarctrlhittest"></a><a name="hittest"></a>Crebarctrl::HitTest

Implementuje chování [RB_HITTEST](/windows/win32/Controls/rb-hittest)zprávy Win32 , jak je popsáno v sadě Windows SDK.

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>Parametry

*prbht řekl:*<br/>
Ukazatel na strukturu [RBHITTESTINFO.](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo) Před odesláním zprávy `pt` musí být člen této struktury inicializován do bodu, který bude testován v souřadnicích klienta.

### <a name="return-value"></a>Návratová hodnota

Nulový index pásma v daném bodě nebo -1, pokud v bodě nebylo žádné pásmo výztuže.

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a>Crebarctrl::IDToIndex

Implementuje chování zprávy Win32 [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex), jak je popsáno v sadě Windows SDK.

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>Parametry

*uBandID*<br/>
Identifikátor definované aplikací zadaného pásma, `wID` předaný v člen [u rebarbandinfo](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) struktury při vložení pásma.

### <a name="return-value"></a>Návratová hodnota

Index pásma na základě nuly, pokud je úspěšný, nebo -1 jinak. Pokud existují duplicitní indexy pásma, první je vrácena.

## <a name="crebarctrlinsertband"></a><a name="insertband"></a>CRebarctrl::InsertBand

Implementuje chování zprávy Win32 [RB_INSERTBAND](/windows/win32/Controls/rb-insertband), jak je popsáno v sadě Windows SDK.

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parametry

*uIndex*<br/>
Nulový index umístění, kam bude vloženo pásmo. Pokud nastavíte tento parametr na -1, ovládací prvek přidá nové pásmo na posledním místě.

*prbbi*<br/>
Ukazatel na strukturu [REBARBANDINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) která definuje pásmo, které má být vloženo. Před voláním této funkce je `sizeof(REBARBANDINFO)` nutné nastavit člen *cbSize* této struktury.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a>CRebarctrl::Maximalizovat pásmo

Změní velikost pásu v ovládacím prvku výztuže na jeho největší velikost.

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma, které má být maximalizováno.

### <a name="remarks"></a>Poznámky

Implementuje chování zprávy Win32 `fIdeal` [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) s nastavenou na 0, jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a>Crebarctrl::minimalizovat pásmo

Změní velikost pásu v ovládacím prvku výztuže na jeho nejmenší velikost.

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma, které má být minimalizováno.

### <a name="remarks"></a>Poznámky

Implementuje chování zprávy Win32 [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a>Crebarctrl::MoveBand

Implementuje chování [RB_MOVEBAND](/windows/win32/Controls/rb-moveband)zprávy Win32 , jak je popsáno v sadě Windows SDK.

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>Parametry

*uFrom*<br/>
Nulový index pásma, které má být přesunuto.

*Uto*<br/>
Nulový index nové pozice pásma. Tato hodnota parametru nesmí být nikdy větší než počet pásem mínus jedna. Chcete-li získat počet pásem, volejte [GetBandCount](#getbandcount).

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a>CReBarCtrl::PushChevron

Implementuje chování zprávy Win32 [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron), jak je popsáno v sadě Windows SDK.

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma, jehož dvojitá šipka má být posunuta.

*hodnota lAppValue*<br/>
Aplikace definovaná 32bitovou hodnotou. Viz *hodnota lAppValue* v [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron) v sadě Windows SDK.

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a>CRebarctrl::RestoreBand

Změní velikost pásu v ovládacím prvku výztuže na jeho ideální velikost.

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma, které má být maximalizováno.

### <a name="remarks"></a>Poznámky

Implementuje chování zprávy Win32 `fIdeal` [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) s nastavenou na 1, jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a>Crebarctrl::SetBandInfo

Implementuje chování zprávy Win32 [RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo), jak je popsáno v sadě Windows SDK.

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma pro příjem nového nastavení.

*prbbi*<br/>
Ukazatel na strukturu [REBARBANDINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) která definuje pásmo, které má být vloženo. Před odesláním `cbSize` této zprávy `sizeof(REBARBANDINFO)` je nutné nastavit člena této struktury.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a>Crebarctrl::SetBandWidth

Nastaví šířku zadaného ukotveného pásma v aktuálním ovládacím prvku výztuže.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*uPásmo*|[v] Nulový index pásma výztuže.|
|*cxWidth*|[v] Nová šířka pásma výztuže v pixelech.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu RB_SETBANDWIDTH,](/windows/win32/Controls/rb-setbandwidth) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_rebar`která se používá pro přístup k aktuálnímu ovládacímu prvku výztuže. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví každý pás výztuže na stejnou šířku.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a>Crebarctrl::SetBarInfo

Implementuje chování [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)zprávy Win32 , jak je popsáno v sadě Windows SDK.

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>Parametry

*prbi*<br/>
Ukazatel na strukturu [REBARINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) která obsahuje informace, které mají být nastaveny. Před odesláním `cbSize` této zprávy `sizeof(REBARINFO)` je nutné nastavit člena této struktury.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a>CReBarCtrl::SetBkColor

Implementuje chování zprávy Win32 [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor), jak je popsáno v sadě Windows SDK.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Colorref hodnota, která představuje novou výchozí barvu pozadí.

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF,](/windows/win32/gdi/colorref) která představuje předchozí výchozí barvu pozadí.

### <a name="remarks"></a>Poznámky

Další informace o tom, kdy nastavit barvu pozadí a jak nastavit výchozí nastavení, naleznete v tomto tématu.

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a>CRebarctrl::SetColorScheme

Nastaví barevné schéma tlačítek v ovládacím prvku výztuže.

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Ukazatel na strukturu [COLORSCHEME,](/windows/win32/api/commctrl/ns-commctrl-colorscheme) jak je popsáno v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Struktura `COLORSCHEME` zahrnuje jak barvu zvýraznění tlačítka, tak barvu stínu tlačítka.

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a>Crebarctrl::SetExtendedStyle

Nastaví rozšířené styly pro aktuální ovládací prvek výztuže.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwMask*|[v] Bitová kombinace (OR) příznaků, které určují, které příznaky v parametru *dwStyleEx* platí. Použijte jednu nebo více z následujících hodnot:<br /><br /> RBS_EX_SPLITTER: Ve výchozím nastavení zobrazte rozdělovač na spodní straně v horizontálním režimu a vpravo ve svislém režimu.<br /><br /> RBS_EX_TRANSPARENT: Přepošle [zprávu WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) do nadřazeného okna.|
|*dwStyleEx*|[v] Bitová kombinace (OR) příznaků, které určují styly, které mají být aplikovány. Chcete-li nastavit styl, zadejte stejný příznak, který se používá v parametru *dwMask.* Chcete-li obnovit styl, zadejte binární nulu.|

### <a name="return-value"></a>Návratová hodnota

Předchozí rozšířený styl.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu RB_SETEXTENDEDSTYLE,](/windows/win32/Controls/rb-setextendedstyle) která je popsána v sadě Windows SDK.

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a>Crebarctrl::SetImageList

Přiřadí seznam obrázků ovládacímu prvku výztuže.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*seznam obrázků pImage*<br/>
Ukazatel na objekt [CImageList](../../mfc/reference/cimagelist-class.md) obsahující seznam obrázků, který má být přiřazen ovládacímu prvku výztuže.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

## <a name="crebarctrlsetowner"></a><a name="setowner"></a>CRebarctrl::SetOwner

Implementuje chování zprávy Win32 [RB_SETPARENT](/windows/win32/Controls/rb-setparent), jak je popsáno v sadě Windows SDK.

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na `CWnd` objekt nastavit jako vlastník ovládacího prvku výztuže.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je aktuálním vlastníkem ovládacího prvku výztuže.

### <a name="remarks"></a>Poznámky

Všimněte si, že tato `CWnd` členská funkce používá ukazatele na objekty pro aktuální i vybraný vlastník ovládacího prvku výztuže, nikoli popisovače do oken.

> [!NOTE]
> Tato členská funkce nezmění skutečnou nadřazenou položku, která byla nastavena při vytvoření ovládacího prvku; spíše odesílá oznámení do zadaného okna.

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a>Crebarctrl::SetPalette

Implementuje chování zprávy Win32 [RB_SETPALETTE](/windows/win32/Controls/rb-setpalette), jak je popsáno v sadě Windows SDK.

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>Parametry

*hPal*<br/>
HPALETTE, který určuje novou paletu, kterou bude ovládací prvek výztuže používat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CPalette](../../mfc/reference/cpalette-class.md) určující předchozí paletu ovládacího prvku výztuže.

### <a name="remarks"></a>Poznámky

Všimněte si, že `CPalette` tato členská funkce používá objekt jako jeho vrácená hodnota, nikoli HPALETTE.

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a>CRebarctrl::SettextColor

Implementuje chování [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)zprávy Win32 , jak je popsáno v sadě Windows SDK.

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Hodnota COLORREF, která představuje novou `CReBarCtrl` barvu textu v objektu.

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) představující předchozí barvu textu `CReBarCtrl` přidruženou k objektu.

### <a name="remarks"></a>Poznámky

Je k dispozici pro podporu flexibility barev textu v ovládacím prvku výztuže.

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a>Crebarctrl::settooltips

Přidruží ovládací prvek špičky nástroje k ovládacímu prvku výztuže.

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>Parametry

*pPopis nástroje*<br/>
Ukazatel na objekt [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Poznámky

Musíte zničit `CToolTipCtrl` objekt, když jste hotovi s ním.

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CReBarCtrl::SetWindowTheme

Nastaví vizuální styl ovládacího prvku výztuže.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Ukazatel na řetězec Unicode, který obsahuje vizuální styl výztuže, který chcete nastavit.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota se nepoužívá.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme) zprávy, jak je popsáno v sadě Windows SDK.

## <a name="crebarctrlshowband"></a><a name="showband"></a>CRebarctrl::ShowBand

Implementuje chování [RB_SHOWBAND](/windows/win32/Controls/rb-showband)zprávy Win32 , jak je popsáno v sadě Windows SDK.

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>Parametry

*uPásmo*<br/>
Nulový index pásma v ovládacím prvku výztuže.

*fZobrazit*<br/>
Označuje, zda má být pásmo zobrazeno nebo skryto. Pokud je tato hodnota PRAVDA, zobrazí se pásmo. V opačném případě bude kapela skryta.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a>CReBarCtrl::SizeToRect

Implementuje chování zprávy Win32 [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect), jak je popsáno v sadě Windows SDK.

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odkaz na [cRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který určuje obdélník, který by měl být velikost ovládacího prvku výztuže velikosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Všimněte si, že `CRect` tato členská funkce `RECT` používá objekt jako parametr, nikoli strukturu.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
