---
title: CSliderCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
ms.openlocfilehash: 24e1cb18f979d1144f15cf6ffedc6cace5f5361e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318218"
---
# <a name="csliderctrl-class"></a>CSliderCtrl – třída

Poskytuje funkce ovládacího prvku posuvníku systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Vytvoří `CSliderCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSliderCtrl::Vymazat se](#clearsel)|Vymaže aktuální výběr v ovládacím prvku jezdce.|
|[CSliderCtrl::ClearTics](#cleartics)|Odstraní aktuální značky z ovládacího prvku posuvníku.|
|[CSliderCtrl::Vytvořit](#create)|Vytvoří ovládací prvek posuvníku `CSliderCtrl` a připojí jej k objektu.|
|[CSliderCtrl::CreateEx](#createex)|Vytvoří jezdecké ovládací prvek se zadanými rozšířenými styly systému Windows a připojí jej k objektu. `CSliderCtrl`|
|[CSliderCtrl::GetBuddy](#getbuddy)|Načte popisovač do okna kamaráda ovládacího prvku posuvníku v daném umístění.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Načte velikost kanálu ovládacího prvku posuvníku.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Načte velikost čáry ovládacího prvku posuvníku.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Načte počet značek v ovládacím prvku posuvníku.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Načte velikost stránky ovládacího prvku posuvníku.|
|[CSliderCtrl::GetPos](#getpos)|Načte aktuální pozici jezdce.|
|[CSliderCtrl::GetRange](#getrange)|Načte minimální a maximální pozice pro posuvník.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Načte maximální pozici jezdce.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Načte minimální pozici pro posuvník.|
|[CSliderCtrl::GetSelection](#getselection)|Načte rozsah aktuálního výběru.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Načte délku jezdce v aktuálním ovládacím prvku trackbar.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Načte velikost palce ovládacího prvku posuvníku.|
|[CSliderCtrl::GetTic](#gettic)|Načte pozici zadaného značkového pole.|
|[CSliderCtrl::GetTicArray](#getticarray)|Načte pole značek pozice pro ovládací prvek jezdce.|
|[CSliderCtrl::GetTicPos](#getticpos)|Načte pozici zadaného značky v souřadnicích klienta.|
|[CSliderCtrl::GetToolTips](#gettooltips)|Načte popisovač do ovládacího prvku popisku přiřazeného k ovládacímu prvku posuvníku, pokud existuje.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Přiřadí okno jako okno kamaráda pro ovládací prvek posuvníku.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Nastaví velikost čáry ovládacího prvku posuvníku.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Nastaví velikost stránky ovládacího prvku posuvníku.|
|[CSliderCtrl::SetPos](#setpos)|Nastaví aktuální pozici jezdce.|
|[CSliderCtrl::SetRange](#setrange)|Nastaví minimální a maximální polohu jezdce.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Nastaví maximální polohu jezdce.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Nastaví minimální polohu jezdce.|
|[CSliderCtrl::SetSelection](#setselection)|Nastaví rozsah aktuálního výběru.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Nastaví délku jezdce v aktuálním ovládacím prvku trackbaru.|
|[CSliderCtrl::SetTic](#settic)|Nastaví pozici zadaného značky.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Nastaví frekvenci značek na přírůstek ovládacího prvku posuvníku.|
|[CSliderCtrl::SetTipSide](#settipside)|Umístí ovládací prvek popisku používaný ovládacím prvkem trackbaru.|
|[CSliderCtrl::SetToolTips](#settooltips)|Přiřadí ovládací prvek popisu ovládacímu prvku jezdce.|

## <a name="remarks"></a>Poznámky

"Posuvník" (také známý jako trackbar) je okno obsahující posuvník a volitelné značky. Když uživatel přesune jezdec, pomocí myši nebo směrové klávesy, ovládací prvek odešle oznámení označí změnu.

Posuvníkové ovládací prvky jsou užitečné, pokud chcete, aby uživatel vybral diskrétní hodnotu nebo sadu po sobě jdoucích hodnot v rozsahu. Můžete například použít posuvník, který uživateli umožní nastavit rychlost opakování klávesnice přesunutím jezdce na danou značku.

Tento ovládací prvek `CSliderCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novějších.

Jezdec se pohybuje v krocích, které zadáte při jeho vytváření. Pokud například určíte, že jezdec má rozsah pěti, může jezdec zabírat pouze šest pozic: pozici na levé straně ovládacího prvku jezdce a jednu pozici pro každý přírůstek v rozsahu. Obvykle je každá z těchto pozic označena značkou.

Posuvník vytvoříte pomocí konstruktoru `Create` a `CSliderCtrl`členské funkce aplikace . Po vytvoření ovládacího prvku posuvníku můžete `CSliderCtrl` pomocí členských funkcí změnit mnoho jeho vlastností. Mezi změny, které můžete provést, patří nastavení minimálních a maximálních pozic pro jezdec, kreslení značek, nastavení rozsahu výběru a přemístění jezdce.

Další informace o `CSliderCtrl`použití naleznete v [tématech Ovládací prvky](../../mfc/controls-mfc.md) a [Použití kláves CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="csliderctrlclearsel"></a><a name="clearsel"></a>CSliderCtrl::Vymazat se

Vymaže aktuální výběr v ovládacím prvku jezdce.

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bPřekreslit*<br/>
Překreslit vlajku. Pokud je tento parametr TRUE, jezdec se překreslí po výběru; jinak se posuvník nepřekreslí.

## <a name="csliderctrlcleartics"></a><a name="cleartics"></a>CSliderCtrl::ClearTics

Odstraní aktuální značky z ovládacího prvku posuvníku.

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bPřekreslit*<br/>
Překreslit vlajku. Pokud je tento parametr TRUE, jezdec se překreslí po vymazání značek; jinak se posuvník nepřekreslí.

## <a name="csliderctrlcreate"></a><a name="create"></a>CSliderCtrl::Vytvořit

Vytvoří ovládací prvek posuvníku `CSliderCtrl` a připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl ovládacího prvku posuvníku. Použijte libovolnou kombinaci [stylů ovládacího prvku posuvníku](/windows/win32/Controls/trackbar-control-styles), popsané v sadě Windows SDK, na ovládací prvek.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku posuvníku. Může to být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/previous-versions/dd162897\(v=vs.85\)) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího `CDialog`prvku posuvníku, obvykle . Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku posuvníku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CSliderCtrl` ve dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který vytvoří ovládací `CSliderCtrl` prvek jezdce a připojí jej k objektu.

V závislosti na hodnotách nastavených pro *dwStyle*může mít ovládací prvek posuvníku svislou nebo vodorovnou orientaci. To může mít značky na obou stranách, na obou stranách, nebo ani jeden. Lze jej také použít k určení rozsahu po sobě jdoucích hodnot.

Chcete-li použít rozšířené styly oken pro ovládací `Create`prvek posuvníku, zavolejte [createex](#createex) místo .

## <a name="csliderctrlcreateex"></a><a name="createex"></a>CSliderCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a `CSliderCtrl` přidruží jej k objektu.

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
Určuje styl ovládacího prvku posuvníku. Použijte libovolnou kombinaci [stylů ovládacího prvku posuvníku](/windows/win32/Controls/trackbar-control-styles), popsané v sadě Windows SDK, na ovládací prvek.

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

## <a name="csliderctrlcsliderctrl"></a><a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl

Vytvoří `CSliderCtrl` objekt.

```
CSliderCtrl();
```

## <a name="csliderctrlgetbuddy"></a><a name="getbuddy"></a>CSliderCtrl::GetBuddy

Načte popisovač do okna kamaráda ovládacího prvku posuvníku v daném umístění.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parametry

*fUmístění*<br/>
Logická hodnota, která označuje, které ze dvou popisovačů okna kamaráda načíst. Může se na nich vyvěšovat jedna z následujících hodnot:

- TRUE Načte úchyt do kamaráda nalevo od jezdce. Pokud ovládací prvek posuvníku používá styl TBS_VERT, zpráva načte kamaráda nad jezdcem.

- FALSE Načte úchyt na kamaráda napravo od jezdce. Pokud ovládací prvek posuvníku používá styl TBS_VERT, zpráva načte kamaráda pod jezdcem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je okno kamaráda v umístění určeném *fLocation*nebo NULL, pokud neexistuje žádné okno kamaráda v tomto umístění.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)zprávy Win32 , jak je popsáno v sadě Windows SDK. Popis stylů ovládacího prvku posuvníku naleznete v tématu [Styly ovládacího prvku trackpanelu](/windows/win32/Controls/trackbar-control-styles) v sadě Windows SDK.

## <a name="csliderctrlgetchannelrect"></a><a name="getchannelrect"></a>CSliderCtrl::GetChannelRect

Načte velikost a umístění ohraničovacího obdélníku pro kanál ovládacího prvku posuvníku.

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Ukazatel na [cRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje velikost a umístění ohraničující obdélník kanálu, když se vrátí funkce.

### <a name="remarks"></a>Poznámky

Kanál je oblast, přes kterou se jezdec pohybuje a která obsahuje zvýraznění, když je vybraný rozsah.

## <a name="csliderctrlgetlinesize"></a><a name="getlinesize"></a>CSliderCtrl::GetLineSize

Načte velikost řádku pro ovládací prvek posuvníku.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost čáry pro ovládací prvek posuvníku.

### <a name="remarks"></a>Poznámky

Velikost řádku ovlivňuje, o kolik se jezdec přesune pro oznámení TB_LINEUP a TB_LINEDOWN. Výchozí nastavení pro velikost řádku je 1.

## <a name="csliderctrlgetnumtics"></a><a name="getnumtics"></a>CSliderCtrl::GetNumTics

Načte počet značek v ovládacím prvku posuvníku.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet značek v ovládacím prvku posuvníku.

## <a name="csliderctrlgetpagesize"></a><a name="getpagesize"></a>CSliderCtrl::GetPageSize

Načte velikost stránky pro ovládací prvek posuvníku.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost stránky pro ovládací prvek posuvníku.

### <a name="remarks"></a>Poznámky

Velikost stránky ovlivňuje, o kolik se jezdec přesune pro TB_PAGEUP a TB_PAGEDOWN oznámení.

## <a name="csliderctrlgetpos"></a><a name="getpos"></a>CSliderCtrl::GetPos

Načte aktuální pozici jezdce v ovládacím prvku jezdce.

```
int GetPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice.

## <a name="csliderctrlgetrange"></a><a name="getrange"></a>CSliderCtrl::GetRange

Načte maximální a minimální pozice jezdce v ovládacím prvku posuvníku.

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Odkaz na celé číslo, které obdrží minimální pozici.

*nMax*<br/>
Odkaz na celé číslo, které obdrží maximální pozici.

### <a name="remarks"></a>Poznámky

Tato funkce zkopíruje hodnoty do celých čísel, na která odkazují *nMin* a *nMax*.

## <a name="csliderctrlgetrangemax"></a><a name="getrangemax"></a>CSliderCtrl::GetRangeMax

Načte maximální pozici jezdce v ovládacím prvku jezdce.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální pozice ovládacího prvku.

## <a name="csliderctrlgetrangemin"></a><a name="getrangemin"></a>CSliderCtrl::GetRangeMin

Načte minimální pozici jezdce v ovládacím prvku posuvníku.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální poloha ovládacího prvku.

## <a name="csliderctrlgetselection"></a><a name="getselection"></a>CSliderCtrl::GetSelection

Načte počáteční a koncovou pozici aktuálního výběru v ovládacím prvku posuvníku.

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Odkaz na celé číslo, které přijímá počáteční pozici aktuálního výběru.

*nMax*<br/>
Odkaz na celé číslo, které obdrží koncovou pozici aktuálního výběru.

## <a name="csliderctrlgetthumblength"></a><a name="getthumblength"></a>CSliderCtrl::GetThumbLength

Načte délku jezdce v aktuálním ovládacím prvku trackbar.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka jezdce v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu TBM_GETTHUMBLENGTH,](/windows/win32/Controls/tbm-getthumblength) která je popsána v sadě Windows SDK.

## <a name="csliderctrlgetthumbrect"></a><a name="getthumbrect"></a>CSliderCtrl::GetThumbRect

Načte velikost a umístění ohraničovacího obdélníku pro jezdec (palec) v ovládacím prvku jezdce.

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Ukazatel na `CRect` objekt, který obsahuje ohraničovací obdélník pro jezdec, když se vrátí funkce.

## <a name="csliderctrlgettic"></a><a name="gettic"></a>CSliderCtrl::GetTic

Načte pozici značky v ovládacím prvku posuvníku.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Index založený na nule identifikující značku.

### <a name="return-value"></a>Návratová hodnota

Pozice zadané značky nebo - 1, pokud *nTic* neurčuje platný index.

## <a name="csliderctrlgetticarray"></a><a name="getticarray"></a>CSliderCtrl::GetTicArray

Načte adresu pole obsahující pozice značek pro ovládací prvek posuvníku.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa pole obsahující pozice značek pro ovládací prvek posuvníku.

## <a name="csliderctrlgetticpos"></a><a name="getticpos"></a>CSliderCtrl::GetTicPos

Načte aktuální fyzickou pozici značky v ovládacím prvku posuvníku.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Index založený na nule identifikující značku.

### <a name="return-value"></a>Návratová hodnota

Fyzická pozice v souřadnicích klienta zadaného značky nebo - 1, pokud *nTic* neurčuje platný index.

## <a name="csliderctrlgettooltips"></a><a name="gettooltips"></a>CSliderCtrl::GetToolTips

Načte popisovač do ovládacího prvku popisku přiřazeného k ovládacímu prvku posuvníku, pokud existuje.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [ctooltipctrl](../../mfc/reference/ctooltipctrl-class.md) objekt nebo NULL, pokud popisky nejsou používány. Pokud ovládací prvek posuvníku nepoužívá styl TBS_TOOLTIPS, vrácená hodnota je NULL.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/tbm-gettooltips)Win32 TBM_GETTOOLTIPS , jak je popsáno v sadě Windows SDK. Všimněte si, že `CToolTipCtrl` tato členská funkce vrátí objekt namísto popisovače do ovládacího prvku.

Popis stylů ovládacího prvku posuvníku naleznete v tématu [Styly ovládacího prvku trackpanelu](/windows/win32/Controls/trackbar-control-styles) v sadě Windows SDK.

## <a name="csliderctrlsetbuddy"></a><a name="setbuddy"></a>CSliderCtrl::SetBuddy

Přiřadí okno jako okno kamaráda pro ovládací prvek posuvníku.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parametry

*pWndBuddy*<br/>
Ukazatel na `CWnd` objekt, který bude nastaven jako kamarád ovládacího prvku posuvníku.

*fUmístění*<br/>
Hodnota určující umístění, ve kterém se má zobrazit okno kamaráda. Tato hodnota může být jedna z následujících:

- PRAVDA Kamarád se zobrazí vlevo od trackbaru, pokud ovládací prvek trackbaru používá TBS_HORZ styl. Pokud trackbar používá styl TBS_VERT, zobrazí se nad ovládacím prvkem trackbaru.

- FALSE Kamarád se zobrazí vpravo od trackbaru, pokud ovládací prvek trackbaru používá TBS_HORZ stylu. Pokud trackbar používá styl TBS_VERT, zobrazí se pod ovládacím prvkem trackbaru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který byl dříve přiřazen k ovládacímu prvku jezdce v tomto umístění.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)zprávy Win32 , jak je popsáno v sadě Windows SDK. Všimněte si, že tato `CWnd` členská funkce používá ukazatele na objekty, nikoli popisovače okna pro jeho vrácenou hodnotu a parametr.

Popis stylů ovládacího prvku posuvníku naleznete v tématu [Styly ovládacího prvku trackpanelu](/windows/win32/Controls/trackbar-control-styles) v sadě Windows SDK.

## <a name="csliderctrlsetlinesize"></a><a name="setlinesize"></a>CSliderCtrl::SetLineSize

Nastaví velikost čáry pro ovládací prvek posuvníku.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nVelikost*<br/>
Nová velikost řádku ovládacího prvku posuvníku.

### <a name="return-value"></a>Návratová hodnota

Předchozí velikost řádku.

### <a name="remarks"></a>Poznámky

Velikost řádku ovlivňuje, o kolik se jezdec přesune pro oznámení TB_LINEUP a TB_LINEDOWN.

## <a name="csliderctrlsetpagesize"></a><a name="setpagesize"></a>CSliderCtrl::SetPageSize

Nastaví velikost stránky pro ovládací prvek posuvníku.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nVelikost*<br/>
Nová velikost stránky ovládacího prvku posuvníku.

### <a name="return-value"></a>Návratová hodnota

Předchozí velikost stránky.

### <a name="remarks"></a>Poznámky

Velikost stránky ovlivňuje, o kolik se jezdec přesune pro TB_PAGEUP a TB_PAGEDOWN oznámení.

## <a name="csliderctrlsetpos"></a><a name="setpos"></a>CSliderCtrl::SetPos

Nastaví aktuální polohu jezdce v ovládacím prvku jezdce.

```
void SetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje novou polohu jezdce.

## <a name="csliderctrlsetrange"></a><a name="setrange"></a>CSliderCtrl::SetRange

Nastaví rozsah (minimální a maximální polohy) jezdce v ovládacím prvku posuvníku.

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Minimální poloha pro posuvník.

*nMax*<br/>
Maximální poloha jezdce.

*bPřekreslit*<br/>
Překreslit vlajku. Pokud je tento parametr TRUE, posuvník se po nastavení rozsahu překreslí; jinak se posuvník nepřekreslí.

## <a name="csliderctrlsetrangemax"></a><a name="setrangemax"></a>CSliderCtrl::SetRangeMax

Nastaví maximální rozsah jezdce v ovládacím prvku posuvníku.

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nMax*<br/>
Maximální poloha jezdce.

*bPřekreslit*<br/>
Překreslit vlajku. Pokud je tento parametr TRUE, posuvník se po nastavení rozsahu překreslí; jinak se posuvník nepřekreslí.

## <a name="csliderctrlsetrangemin"></a><a name="setrangemin"></a>CSliderCtrl::SetRangeMin

Nastaví minimální rozsah jezdce v ovládacím prvku posuvníku.

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Minimální poloha pro posuvník.

*bPřekreslit*<br/>
Překreslit vlajku. Pokud je tento parametr TRUE, posuvník se po nastavení rozsahu překreslí; jinak se posuvník nepřekreslí.

## <a name="csliderctrlsetselection"></a><a name="setselection"></a>CSliderCtrl::SetSelection

Nastaví počáteční a koncovou pozici pro aktuální výběr v ovládacím prvku posuvníku.

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Počáteční poloha pro posuvník.

*nMax*<br/>
Koncová pozice pro posuvník.

## <a name="csliderctrlsetthumblength"></a><a name="setthumblength"></a>CSliderCtrl::SetThumbLength

Nastaví délku jezdce v aktuálním ovládacím prvku trackbaru.

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nDélka*|[v] Délka jezdce v obrazových bodech.|

### <a name="remarks"></a>Poznámky

Tato metoda vyžaduje, aby ovládací prvek trackbar nastavit [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) stylu.

Tato metoda odešle [zprávu TBM_SETTHUMBLENGTH,](/windows/win32/Controls/tbm-setthumblength) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_sliderCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku trackbar. Příklad také definuje proměnnou `thumbLength`, která se používá k uložení výchozí délky komponenty palce ovládacího prvku trackbar. Tyto proměnné se používají v následujícím příkladu.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví komponentu palce ovládacího prvku trackbaru na dvojnásobek výchozí délky.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

## <a name="csliderctrlsettic"></a><a name="settic"></a>CSliderCtrl::SetTic

Nastaví pozici značky v ovládacím prvku posuvníku.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Pozice značky. Tento parametr musí určit kladnou hodnotu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je značka nastavena; jinak 0.

## <a name="csliderctrlsetticfreq"></a><a name="setticfreq"></a>CSliderCtrl::SetTicFreq

Nastaví frekvenci, s jakou jsou značky zobrazeny v posuvníku.

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parametry

*nFreq*<br/>
Frekvence značek.

### <a name="remarks"></a>Poznámky

Pokud je například frekvence nastavena na 2, zobrazí se značka pro každý druhý přírůstek v rozsahu jezdce. Výchozí nastavení frekvence je 1 (to znamená, že každý přírůstek v rozsahu je spojen se značkou zaškrtnutí).

Chcete-li tuto funkci použít, je nutné vytvořit ovládací prvek se stylem TBS_AUTOTICKS. Další informace naleznete v tématu [CSliderCtrl::Create](#create).

## <a name="csliderctrlsettipside"></a><a name="settipside"></a>CSliderCtrl::SetTipSide

Umístí ovládací prvek popisku používaný ovládacím prvkem trackbaru.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parametry

*nUmístění*<br/>
Hodnota představující umístění, ve kterém chcete zobrazit ovládací prvek popisku. Seznam možných hodnot naleznete ve zprávě win32 [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside), jak je popsáno v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která představuje předchozí umístění ovládacího prvku popisku. Vrácená hodnota se rovná jedné z možných hodnot pro *nLocation*.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 TBM_SETTIPSIDE, jak je popsáno v sadě Windows SDK. Posuvník ovládací prvky, které používají TBS_TOOLTIPS styl zobrazení popisky. Popis stylů ovládacího prvku posuvníku naleznete v tématu [Styly ovládacího prvku trackpanelu](/windows/win32/Controls/trackbar-control-styles) v sadě Windows SDK.

## <a name="csliderctrlsettooltips"></a><a name="settooltips"></a>CSliderCtrl::SetToolTips

Přiřadí ovládací prvek popisu ovládacímu prvku jezdce.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWndTip*<br/>
Ukazatel na objekt [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obsahující popisky, které se mají použít s ovládacím prvkem posuvníku.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/tbm-settooltips)Win32 TBM_SETTOOLTIPS , jak je popsáno v sadě Windows SDK. Když je ovládací prvek posuvníku vytvořen s TBS_TOOLTIPS stylem, vytvoří výchozí ovládací prvek popisku, který se zobrazí vedle jezdce a zobrazí aktuální polohu jezdce. Popis stylů ovládacího prvku posuvníku naleznete v tématu [Styly ovládacího prvku trackpanelu](/windows/win32/Controls/trackbar-control-styles) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl – třída](../../mfc/reference/cprogressctrl-class.md)
