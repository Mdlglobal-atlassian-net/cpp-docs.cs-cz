---
title: Atributu CSliderCtrl – třída
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
ms.openlocfilehash: 8fffdfc002b25fdcd72dcbbf53e7e6c321f55296
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502522"
---
# <a name="csliderctrl-class"></a>Atributu CSliderCtrl – třída

Poskytuje funkce pro běžný ovládací prvek posuvníku systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|`CSliderCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|Zruší aktuální výběr v ovládacím prvku posuvník.|
|[CSliderCtrl::ClearTics](#cleartics)|Odebere aktuální osové značky z ovládacího prvku posuvník.|
|[CSliderCtrl::Create](#create)|Vytvoří ovládací prvek posuvníku a připojí ho k `CSliderCtrl` objektu.|
|[CSliderCtrl::CreateEx](#createex)|Vytvoří ovládací prvek posuvník se zadanými rozšířenými styly Windows a připojí ho k `CSliderCtrl` objektu.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Načte popisovač k oknu s ovládacím prvkem na posuvníku v daném umístění.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Načte velikost kanálu ovládacího prvku posuvníku.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Načítá velikost čáry ovládacího prvku posuvník.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Načte počet značek v ovládacím prvku posuvník.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Načte velikost stránky ovládacího prvku posuvníku.|
|[CSliderCtrl::GetPos](#getpos)|Načte aktuální pozici posuvníku.|
|[CSliderCtrl::GetRange](#getrange)|Načte minimální a maximální polohu posuvníku.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Načte maximální pozici posuvníku.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Načte minimální pozici posuvníku.|
|[CSliderCtrl::GetSelection](#getselection)|Načte rozsah aktuálního výběru.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Načte délku posuvníku v aktuálním ovládacím prvku TrackBar.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Načte velikost táhla ovládacího prvku posuvníku.|
|[CSliderCtrl::GetTic](#gettic)|Načte pozici určené značky.|
|[CSliderCtrl::GetTicArray](#getticarray)|Načte pole pozic osové značky pro ovládací prvek posuvníku.|
|[CSliderCtrl::GetTicPos](#getticpos)|Načte pozici zadané osové značky v souřadnicích klienta.|
|[CSliderCtrl::GetToolTips](#gettooltips)|Načte popisovač k ovládacímu prvku ToolTip přiřazenému ovládacímu prvku posuvník, pokud existuje.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Přiřadí okno jako kamarád okno pro ovládací prvek posuvníku.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Nastaví velikost čáry ovládacího prvku posuvník.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Nastaví velikost stránky ovládacího prvku posuvník.|
|[CSliderCtrl::SetPos](#setpos)|Nastaví aktuální pozici posuvníku.|
|[CSliderCtrl::SetRange](#setrange)|Nastaví minimální a maximální polohu posuvníku.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Nastaví maximální pozici posuvníku.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Nastaví minimální pozici posuvníku.|
|[CSliderCtrl::SetSelection](#setselection)|Nastaví rozsah aktuálního výběru.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Nastaví délku posuvníku v aktuálním ovládacím prvku TrackBar.|
|[CSliderCtrl::SetTic](#settic)|Nastaví pozici zadané osové značky.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Nastaví četnost značek zaškrtnutí na přírůstek ovládacího prvku posuvníku.|
|[CSliderCtrl::SetTipSide](#settipside)|Umístí ovládací prvek ToolTip, který používá ovládací prvek TrackBar.|
|[CSliderCtrl::SetToolTips](#settooltips)|Přiřadí ovládacímu prvku posuvníku ovládací prvek ToolTip.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek posuvník" (také označovaný jako TrackBar) je okno obsahující posuvník a volitelné osové značky. Když uživatel přesune posuvník pomocí myši nebo směrového klíče, ovládací prvek odešle oznamovací zprávy, aby označoval změnu.

Ovládací prvky posuvníku jsou užitečné, pokud chcete, aby uživatel vybral diskrétní hodnotu nebo sadu po sobě jdoucích hodnot v rozsahu. Například můžete použít ovládací prvek posuvníku, který uživateli umožní nastavit rychlost opakování klávesnice přesunutím posuvníku na danou značku.

Tento ovládací prvek (a `CSliderCtrl` třída) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Posuvník se přesune v přírůstcích, které zadáte při jeho vytváření. Například pokud určíte, že posuvník by měl mít rozsah pět, může posuvník zabírat pouze šest pozic: polohu na levé straně ovládacího prvku posuvník a jednu pozici pro každý přírůstek v rozsahu. Obvykle je každá z těchto pozic identifikována osové značkou.

Vytvoříte posuvník pomocí konstruktoru a `Create` členské `CSliderCtrl`funkce. Po vytvoření ovládacího prvku posuvník můžete použít členské funkce v `CSliderCtrl` pro změnu mnoha jeho vlastností. Mezi změny, které můžete provést, patří nastavení minimální a maximální polohy pro posuvník, vykreslení značek zaškrtnutí, nastavení rozsahu výběru a změna polohy posuvníku.

Další informace o použití `CSliderCtrl`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using atributu CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="clearsel"></a>Atributu CSliderCtrl:: ClearSel

Zruší aktuální výběr v ovládacím prvku posuvník.

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bRedraw*<br/>
Příznak překreslení Pokud má tento parametr hodnotu TRUE, je po vymazání výběru překreslen posuvník. v opačném případě se posuvník nepřekreslí.

##  <a name="cleartics"></a>Atributu CSliderCtrl:: ClearTics

Odebere aktuální osové značky z ovládacího prvku posuvník.

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bRedraw*<br/>
Příznak překreslení Pokud má tento parametr hodnotu TRUE, posuvník se překreslí po vymazání značek. v opačném případě se posuvník nepřekreslí.

##  <a name="create"></a>Atributu CSliderCtrl:: Create

Vytvoří ovládací prvek posuvníku a připojí ho k `CSliderCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku posuvníku. Použití libovolné kombinace [stylů ovládacího prvku posuvníku](/windows/win32/Controls/trackbar-control-styles), které jsou popsány v Windows SDK, k ovládacímu prvku.

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku posuvníku. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku posuvník, obvykle a `CDialog`. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku posuvníku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Vytvoří `CSliderCtrl` se ve dvou krocích. Nejprve volejte konstruktor a potom zavolejte `Create`, čímž se vytvoří ovládací prvek posuvník a připojí se `CSliderCtrl` k objektu.

V závislosti na hodnotách nastavených pro *dwStyle*může mít ovládací prvek posuvník buď svislou, nebo vodorovnou orientaci. Může mít osové značky na obou stranách, na obou stranách nebo ani na žádném. Lze ji také použít k určení rozsahu po sobě jdoucích hodnot.

Chcete-li pro ovládací prvek posuvníku použít rozšířené styly [](#createex) oken, zavolejte `Create`CreateEx místo.

##  <a name="createex"></a>Atributu CSliderCtrl:: CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ho k `CSliderCtrl` objektu.

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
Určuje styl ovládacího prvku posuvníku. Použití libovolné kombinace [stylů ovládacího prvku posuvníku](/windows/win32/Controls/trackbar-control-styles), které jsou popsány v Windows SDK, k ovládacímu prvku.

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

##  <a name="csliderctrl"></a>Atributu CSliderCtrl:: atributu CSliderCtrl

`CSliderCtrl` Vytvoří objekt.

```
CSliderCtrl();
```

##  <a name="getbuddy"></a>Atributu CSliderCtrl:: getkamarád

Načte popisovač k oknu s ovládacím prvkem na posuvníku v daném umístění.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parametry

*fLocation*<br/>
Logická hodnota, která označuje, který ze dvou popisovačů okna se má načíst. Může to být jedna z následujících hodnot:

- Hodnota TRUE načte popisovač pro kamaráda vlevo od posuvníku. Pokud ovládací prvek posuvník používá styl TBS_VERT, zpráva získá kamaráda nad posuvník.

- FALSE načte popisovač pro kamaráda napravo od posuvníku. Pokud ovládací prvek posuvník používá styl TBS_VERT, zpráva získá kamaráda pod posuvníkem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je přítelm oknem v umístění určeném parametrem *fLocation*, nebo hodnotu null, pokud v daném umístění neexistuje žádné kamarád okno.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy), jak je popsáno v Windows SDK. Popis stylů ovládacího prvku posuvník naleznete v tématu [styly ovládacího prvku TrackBar](/windows/win32/Controls/trackbar-control-styles) v Windows SDK.

##  <a name="getchannelrect"></a>Atributu CSliderCtrl:: GetChannelRect

Načte velikost a polohu ohraničujícího obdélníku pro kanál ovládacího prvku posuvníku.

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Ukazatel na objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který obsahuje velikost a polohu ohraničujícího obdélníku kanálu při návratu funkce.

### <a name="remarks"></a>Poznámky

Kanál je oblast, přes kterou se pohybuje posuvník a který obsahuje zvýraznění při výběru rozsahu.

##  <a name="getlinesize"></a>Atributu CSliderCtrl:: GetLineSize

Načte velikost čáry ovládacího prvku posuvníku.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost čáry ovládacího prvku posuvník

### <a name="remarks"></a>Poznámky

Velikost čáry má vliv na to, kolik se posuvník pohybuje pro oznámení TB_LINEUP a TB_LINEDOWN. Výchozí nastavení pro velikost řádku je 1.

##  <a name="getnumtics"></a>Atributu CSliderCtrl:: GetNumTics

Načte počet značek v ovládacím prvku posuvník.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet značek v ovládacím prvku posuvník.

##  <a name="getpagesize"></a>Atributu CSliderCtrl:: GetPageSize

Načte velikost stránky ovládacího prvku posuvníku.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost stránky ovládacího prvku posuvník

### <a name="remarks"></a>Poznámky

Velikost stránky má vliv na to, kolik se posuvník pohybuje pro oznámení TB_PAGEUP a TB_PAGEDOWN.

##  <a name="getpos"></a>Atributu CSliderCtrl:: GetPos

Načte aktuální pozici posuvníku v ovládacím prvku posuvník.

```
int GetPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice.

##  <a name="getrange"></a>Atributu CSliderCtrl:: GetRange

Načte maximální a minimální polohu posuvníku v ovládacím prvku posuvník.

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Odkaz na celé číslo, které obdrží minimální pozici.

*Nmaximum*<br/>
Odkaz na celé číslo, které přijímá maximální pozici.

### <a name="remarks"></a>Poznámky

Tato funkce zkopíruje hodnoty do celých čísel, na která odkazují *nminimum* a *nmaximum*.

##  <a name="getrangemax"></a>Atributu CSliderCtrl:: GetRangeMax

Načte maximální pozici posuvníku v ovládacím prvku posuvník.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální poloha ovládacího prvku.

##  <a name="getrangemin"></a>Atributu CSliderCtrl:: GetRangeMin

Načte minimální pozici posuvníku v ovládacím prvku posuvník.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální poloha ovládacího prvku.

##  <a name="getselection"></a>Atributu CSliderCtrl:: getselect

Načte počáteční a koncovou pozici aktuálního výběru v ovládacím prvku posuvník.

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Odkaz na celé číslo, které obdrží počáteční pozici aktuálního výběru.

*Nmaximum*<br/>
Odkaz na celé číslo, které obdrží koncovou pozici aktuálního výběru.

##  <a name="getthumblength"></a>Atributu CSliderCtrl:: GetThumbLength

Načte délku posuvníku v aktuálním ovládacím prvku TrackBar.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka posuvníku v pixelech

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength) , která je popsána v Windows SDK.

##  <a name="getthumbrect"></a>Atributu CSliderCtrl:: GetThumbRect

Načte velikost a polohu ohraničujícího obdélníku pro posuvník (palec) v ovládacím prvku posuvník.

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Ukazatel na `CRect` objekt, který obsahuje ohraničující obdélník pro posuvník, když funkce vrátí.

##  <a name="gettic"></a>Atributu CSliderCtrl:: GetTic

Načte pozici osové značky v ovládacím prvku posuvník.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Index založený na nule pro identifikaci osové značky.

### <a name="return-value"></a>Návratová hodnota

Pozice zadaného osové značky nebo-1, pokud *nTic* neurčuje platný index.

##  <a name="getticarray"></a>Atributu CSliderCtrl:: GetTicArray

Načte adresu pole obsahujícího pozice značek pro ovládací prvek posuvníku.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa pole obsahujícího pozice značek pro ovládací prvek posuvník

##  <a name="getticpos"></a>Atributu CSliderCtrl:: GetTicPos

Načte aktuální fyzickou pozici osové značky v ovládacím prvku posuvník.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Index založený na nule pro identifikaci osové značky.

### <a name="return-value"></a>Návratová hodnota

Fyzická pozice v souřadnicích klienta zadaného osové značky nebo-1, pokud *nTic* neurčuje platný index.

##  <a name="gettooltips"></a>  CSliderCtrl::GetToolTips

Načte popisovač k ovládacímu prvku ToolTip přiřazenému ovládacímu prvku posuvník, pokud existuje.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) nebo hodnotu null, pokud se popisy tlačítek nepoužívají. Pokud ovládací prvek posuvník nepoužívá styl TBS_TOOLTIPS, vrácená hodnota je NULL.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips), jak je popsáno v Windows SDK. Všimněte si, že tato členská `CToolTipCtrl` funkce vrátí objekt namísto popisovače ovládacího prvku.

Popis stylů ovládacího prvku posuvník naleznete v tématu [styly ovládacího prvku TrackBar](/windows/win32/Controls/trackbar-control-styles) v Windows SDK.

##  <a name="setbuddy"></a>Atributu CSliderCtrl:: SetBuddy

Přiřadí okno jako kamarád okno pro ovládací prvek posuvníku.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parametry

*pWndBuddy*<br/>
Ukazatel na `CWnd` objekt, který bude nastaven jako přítel ovládacího prvku posuvník.

*fLocation*<br/>
Hodnota určující umístění, ve kterém se má zobrazit okno kamaráda Tato hodnota může být jedna z následujících:

- TRUE, pokud ovládací prvek TrackBar používá styl TBS_HORZ, zobrazí se vlevo od TrackBar. Pokud TrackBar používá styl TBS_VERT, zobrazí se kamarád nad ovládacím prvkem TrackBar.

- Hodnota FALSE – kamarád se zobrazí napravo od TrackBar, pokud ovládací prvek TrackBar používá styl TBS_HORZ. Pokud TrackBar používá styl TBS_VERT, zobrazí se kamarád pod ovládacím prvkem TrackBar.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který byl dříve přiřazen k ovládacímu prvku posuvník v daném umístění.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy), jak je popsáno v Windows SDK. Všimněte si, že tato členská funkce používá `CWnd` ukazatele na objekty spíše než popisovače okna pro návratovou hodnotu a parametr.

Popis stylů ovládacího prvku posuvník naleznete v tématu [styly ovládacího prvku TrackBar](/windows/win32/Controls/trackbar-control-styles) v Windows SDK.

##  <a name="setlinesize"></a>Atributu CSliderCtrl:: SetLineSize

Nastaví velikost čáry ovládacího prvku posuvník.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
Nová velikost řádku ovládacího prvku posuvník

### <a name="return-value"></a>Návratová hodnota

Velikost předchozího řádku.

### <a name="remarks"></a>Poznámky

Velikost čáry má vliv na to, kolik se posuvník pohybuje pro oznámení TB_LINEUP a TB_LINEDOWN.

##  <a name="setpagesize"></a>Atributu CSliderCtrl:: SetPageSize

Nastaví velikost stránky ovládacího prvku posuvníku.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
Nová velikost stránky ovládacího prvku posuvník

### <a name="return-value"></a>Návratová hodnota

Velikost předchozí stránky

### <a name="remarks"></a>Poznámky

Velikost stránky má vliv na to, kolik se posuvník pohybuje pro oznámení TB_PAGEUP a TB_PAGEDOWN.

##  <a name="setpos"></a>Atributu CSliderCtrl:: SetPos

Nastaví aktuální pozici posuvníku v ovládacím prvku posuvník.

```
void SetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje novou pozici posuvníku.

##  <a name="setrange"></a>Atributu CSliderCtrl:: SetRange

Nastaví rozsah (minimální a maximální umístění) posuvníku v ovládacím prvku posuvník.

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Minimální poloha posuvníku

*Nmaximum*<br/>
Maximální poloha posuvníku

*bRedraw*<br/>
Příznak překreslení. Pokud má tento parametr hodnotu TRUE, je po nastavení rozsahu posuvník překreslen. v opačném případě se posuvník nepřekreslí.

##  <a name="setrangemax"></a>Atributu CSliderCtrl:: SetRangeMax

Nastaví maximální rozsah posuvníku v ovládacím prvku posuvník.

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*Nmaximum*<br/>
Maximální poloha posuvníku

*bRedraw*<br/>
Příznak překreslení. Pokud má tento parametr hodnotu TRUE, je po nastavení rozsahu posuvník překreslen. v opačném případě se posuvník nepřekreslí.

##  <a name="setrangemin"></a>Atributu CSliderCtrl:: SetRangeMin

Nastaví minimální rozsah posuvníku v ovládacím prvku posuvník.

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Minimální poloha posuvníku

*bRedraw*<br/>
Příznak překreslení. Pokud má tento parametr hodnotu TRUE, je po nastavení rozsahu posuvník překreslen. v opačném případě se posuvník nepřekreslí.

##  <a name="setselection"></a>Atributu CSliderCtrl:: SetSelection

Nastaví počáteční a koncovou pozici pro aktuální výběr v ovládacím prvku posuvník.

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Počáteční pozice posuvníku

*Nmaximum*<br/>
Koncová pozice posuvníku

##  <a name="setthumblength"></a>Atributu CSliderCtrl:: SetThumbLength

Nastaví délku posuvníku v aktuálním ovládacím prvku TrackBar.

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nLength*|pro Délka posuvníku v pixelech|

### <a name="remarks"></a>Poznámky

Tato metoda vyžaduje, aby byl ovládací prvek TrackBar nastaven na hodnotu [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) Style.

Tato metoda pošle zprávu [TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_sliderCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku TrackBar. Příklad také definuje proměnnou, `thumbLength`která se používá k uložení výchozí délky komponenty TrackBar ovládacího prvku. Tyto proměnné jsou používány v následujícím příkladu.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví komponentu pro palec ovládacího prvku TrackBar na dvojnásobek výchozí délky.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

##  <a name="settic"></a>Atributu CSliderCtrl:: SetTic

Nastaví pozici osové značky v ovládacím prvku posuvník.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Pozice osové značky. Tento parametr musí určovat kladnou hodnotu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je značka zaškrtnutí nastavena; v opačném případě 0.

##  <a name="setticfreq"></a>Atributu CSliderCtrl:: SetTicFreq

Nastaví četnost, se kterou se budou zobrazovat osové značky v posuvníku.

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parametry

*nFreq*<br/>
Frekvence značek.

### <a name="remarks"></a>Poznámky

Například pokud je frekvence nastavená na hodnotu 2, zobrazí se značka zaškrtnutí pro každé další zvýšení v rozsahu posuvníku. Výchozí nastavení frekvence je 1 (to znamená, že každý přírůstek v rozsahu je přidružen k značce Tick).

Pro použití této funkce je nutné vytvořit ovládací prvek se stylem TBS_AUTOTICKS. Další informace naleznete v tématu [atributu CSliderCtrl:: Create](#create).

##  <a name="settipside"></a>Atributu CSliderCtrl:: SetTipSide

Umístí ovládací prvek ToolTip, který používá ovládací prvek TrackBar.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parametry

*Numístění*<br/>
Hodnota představující umístění, kde se má zobrazit ovládací prvek ToolTip Seznam možných hodnot naleznete v [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside)zprávy Win32, jak je popsáno v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která představuje předchozí umístění ovládacího prvku ToolTip. Vrácená hodnota se rovná jedné z možných hodnot pro *numístění*.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 TBM_SETTIPSIDE, jak je popsáno v Windows SDK. Ovládací prvky posuvníku, které používají popisy zobrazení ve stylu TBS_TOOLTIPS Popis stylů ovládacího prvku posuvník naleznete v tématu [styly ovládacího prvku TrackBar](/windows/win32/Controls/trackbar-control-styles) v Windows SDK.

##  <a name="settooltips"></a>Atributu CSliderCtrl:: SetToolTips

Přiřadí ovládacímu prvku posuvníku ovládací prvek ToolTip.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWndTip*<br/>
Ukazatel na objekt [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obsahující popisy tlačítek, které mají být použity s ovládacím prvkem posuvník.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips), jak je popsáno v Windows SDK. Když se vytvoří ovládací prvek posuvníku se stylem TBS_TOOLTIPS, vytvoří se výchozí ovládací prvek ToolTip, který se zobrazí vedle posuvníku, a zobrazí se aktuální pozice posuvníku. Popis stylů ovládacího prvku posuvník naleznete v tématu [styly ovládacího prvku TrackBar](/windows/win32/Controls/trackbar-control-styles) v Windows SDK.

## <a name="see-also"></a>Viz také:

[CMNCTRL2 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl – třída](../../mfc/reference/cprogressctrl-class.md)
