---
title: CScrollBar – třída
ms.date: 11/04/2016
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
ms.openlocfilehash: 5bc9c0190ea200b25b8ea3b20311c98c1c131838
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821267"
---
# <a name="cscrollbar-class"></a>CScrollBar – třída

Poskytuje funkce ovládacího prvku posuvník systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CScrollBar : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CScrollBar::CScrollBar](#cscrollbar)|`CScrollBar` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CScrollBar:: Create](#create)|Vytvoří posuvník Windows a připojí ho k `CScrollBar` objektu.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Povolí nebo zakáže jednu nebo obě šipky posuvníku.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Načte informace o posuvníku pomocí `SCROLLBARINFO` struktury.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Načte informace o posuvníku.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Načte limit posuvníku.|
|[CScrollBar::GetScrollPos](#getscrollpos)|Načte aktuální pozici rolovacího pole.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Načte aktuální minimální a maximální pozice posuvníku pro daný posuvník.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Nastaví informace o posuvníku.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Nastaví aktuální pozici rolovacího pole.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Nastaví minimální a maximální hodnoty pozice pro daný posuvník.|
|[CScrollBar::ShowScrollBar](#showscrollbar)|Zobrazí nebo skryje posuvník.|

## <a name="remarks"></a>Poznámky

Ovládací prvek posuvníku vytvoříte ve dvou krocích. Nejprve zavolejte konstruktor `CScrollBar` pro `CScrollBar` vytvoření objektu a potom zavolejte funkci [vytvořit](#create) členskou funkci pro vytvoření ovládacího prvku okna posuvníku a připojte jej k `CScrollBar` objektu.

Vytvoříte- `CScrollBar` li objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna), dojde k `CScrollBar` automatickému zničení, když uživatel zavře dialogové okno.

Pokud vytvoříte `CScrollBar` objekt v rámci okna, může být také nutné jej zničit.

Vytvoříte-li `CScrollBar` objekt v zásobníku, bude automaticky zničen. Vytvoříte `CScrollBar` -li objekt na haldě pomocí **nové** funkce, je nutné volat metodu **Delete** u objektu, aby jej bylo možné zničit, když uživatel ukončí posuvník systému Windows.

Pokud přidělíte paměť v `CScrollBar` objektu, `CScrollBar` přepište destruktor k Dispose přidělení.

Související informace o použití `CScrollBar`naleznete v tématu [Controls](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="create"></a>CScrollBar:: Create

Vytvoří posuvník Windows a připojí ho k `CScrollBar` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl posuvníku. Použít libovolnou kombinaci [stylů posuvníku](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) na posuvník.

*OBD*<br/>
Určuje velikost a polohu posuvníku. Může být buď `RECT` struktura, `CRect` nebo objekt.

*pParentWnd*<br/>
Určuje nadřazené okno posuvníku, obvykle `CDialog` objekt. Nesmí mít hodnotu NULL.

*nID*<br/>
ID ovládacího prvku posuvníku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CScrollBar` Vytvoříte objekt ve dvou krocích. Nejprve volejte konstruktor, který sestaví `CScrollBar` objekt a potom zavolejte `Create`, který vytvoří a inicializuje přidružený posuvník systému Windows a `CScrollBar` připojí ho k objektu.

Použijte následující [Styly okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) pro posuvník:

- WS_CHILD vždycky

- WS_VISIBLE obvykle

- WS_DISABLED málokdy

- WS_GROUP do skupinových ovládacích prvků

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

##  <a name="cscrollbar"></a>CScrollBar::CScrollBar

`CScrollBar` Vytvoří objekt.

```
CScrollBar();
```

### <a name="remarks"></a>Poznámky

Po sestavení objektu volejte `Create` členskou funkci pro vytvoření a inicializaci posuvníku Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

##  <a name="enablescrollbar"></a>CScrollBar::EnableScrollBar

Povolí nebo zakáže jednu nebo obě šipky posuvníku.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parametry

*nArrowFlags*<br/>
Určuje, zda jsou povoleny nebo zakázány šipky posuvníku a jsou povoleny nebo zakázány šipky. Tento parametr může být jedna z následujících hodnot:

- ESB_ENABLE_BOTH povolí obě šipky posuvníku.

- ESB_DISABLE_LTUP zakáže levou šipku vodorovného posuvníku nebo šipku nahoru svislého posuvníku.

- ESB_DISABLE_RTDN zakáže pravou šipku vodorovného posuvníku nebo šipky dolů svislého posuvníku.

- ESB_DISABLE_BOTH zakáže obě šipky posuvníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou šipky povoleny nebo zakázány, jak je uvedeno. jinak 0, což znamená, že šipky jsou již v požadovaném stavu nebo došlo k chybě.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CScrollBar:: SetScrollRange](#setscrollrange).

##  <a name="getscrollbarinfo"></a>CScrollBar:: GetScrollBarInfo

Načte informace, které `SCROLLBARINFO` struktura udržuje o posuvníku.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parametry

*pScrollInfo*<br/>
Ukazatel na strukturu [SCROLLBARINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollbarinfo) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [SBM_SCROLLBARINFO](/windows/desktop/Controls/sbm-getscrollbarinfo) zprávy, jak je popsáno v Windows SDK.

##  <a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

Načte informace, které `SCROLLINFO` struktura udržuje o posuvníku.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Ukazatel na strukturu [ScrollInfo](/windows/win32/api/winuser/ns-winuser-scrollinfo) . Další informace o této struktuře najdete v Windows SDK.

*nMask*<br/>
Určuje parametry posouvaných panelů, které se mají načíst. Typické použití, SIF_ALL, určuje kombinaci SIF_PAGE, SIF_POS, SIF_TRACKPOS a SIF_RANGE. Další `SCROLLINFO` informace o hodnotách nMask najdete v tématu.

### <a name="return-value"></a>Návratová hodnota

Pokud zpráva načetla jakékoli hodnoty, vrátí se hodnota TRUE. V opačném případě je hodnota FALSE.

### <a name="remarks"></a>Poznámky

`GetScrollInfo`umožňuje aplikacím používat 32 pozice posunutí.

Struktura [ScrollInfo](/windows/win32/api/winuser/ns-winuser-scrollinfo) obsahuje informace o posuvníku, včetně minimální a maximální pozice pro posouvání, velikosti stránky a polohy rolovacího pole (palec). Další informace o změně výchozího nastavení struktury najdete v tématu strukturavWindowsSDK.`SCROLLINFO`

Obslužné rutiny zpráv systému Windows knihovny MFC, které označují pozici posuvníku, [CWnd:: OnHScroll a [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), poskytují pouze 16 bitů dat o poloze. `GetScrollInfo`a `SetScrollInfo` poskytují 32 bitů dat pozice posuvníku. Proto aplikace může volat `GetScrollInfo` během zpracování buď `CWnd::OnHScroll` nebo `CWnd::OnVScroll` , aby získala 32 data pozice posuvníku.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

Načte maximální polohu posouvání posuvníku.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Návratová hodnota

Určuje maximální umístění posuvníku, pokud bylo úspěšné. v opačném případě 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrollpos"></a>CScrollBar::GetScrollPos

Načte aktuální pozici rolovacího pole.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Určuje aktuální pozici rolovacího pole, pokud bylo úspěšné. v opačném případě 0.

### <a name="remarks"></a>Poznámky

Aktuální pozice je relativní hodnota, která závisí na aktuálním rozsahu posouvání. Pokud je například rozsah posouvání 100 až 200 a rolovací pole je uprostřed panelu, aktuální pozice je 150.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrollrange"></a>CScrollBar::GetScrollRange

Zkopíruje aktuální minimální a maximální polohu posuvníku pro daný posuvník do umístění určených parametrem *lpMinPos* a *lpMaxPos*.

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parametry

*lpMinPos*<br/>
Odkazuje na celočíselnou proměnnou, která má přijmout minimální pozici.

*lpMaxPos*<br/>
Odkazuje na celočíselnou proměnnou, která má přijmout maximální pozici.

### <a name="remarks"></a>Poznámky

Výchozí rozsah ovládacího prvku posuvníku je prázdný (obě hodnoty jsou 0).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

Nastaví informace o tom, `SCROLLINFO` že struktura udržuje o posuvníku.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Ukazatel na strukturu [ScrollInfo](/windows/win32/api/winuser/ns-winuser-scrollinfo) .

*bRedraw*<br/>
Určuje, zda má být překreslen posuvník, aby odrážel nové informace. Pokud má *bRedraw* hodnotu true, posun posuvníku se překreslí. Pokud je hodnota FALSE, není překreslena. Posunutí posuvníku se ve výchozím nastavení překreslí.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu se vrátí hodnota TRUE. V opačném případě je hodnota FALSE.

### <a name="remarks"></a>Poznámky

Je nutné zadat hodnoty požadované `SCROLLINFO` parametry struktury, včetně hodnot příznaků.

`SCROLLINFO` Struktura obsahuje informace o posuvníku, včetně minimální a maximální pozice pro posouvání, velikosti stránky a polohy rolovacího pole (palec). Další informace o změně výchozího nastavení struktury najdete v tématu struktura [ScrollInfo](/windows/win32/api/winuser/ns-winuser-scrollinfo) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

##  <a name="setscrollpos"></a>CScrollBar::SetScrollPos

Nastaví aktuální pozici rolovacího pole na hodnotu zadanou v *nPos* a pokud je tato funkce zadána, překreslí posuvník tak, aby odrážel novou pozici.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje novou pozici pro rolovací okno. Musí být v rozsahu posouvání.

*bRedraw*<br/>
Určuje, zda má být překreslen posuvník, aby odrážel novou pozici. Pokud má *bRedraw* hodnotu true, posun posuvníku se překreslí. Pokud je hodnota FALSE, není překreslena. Posunutí posuvníku se ve výchozím nastavení překreslí.

### <a name="return-value"></a>Návratová hodnota

Určuje předchozí pozici rolovacího pole, pokud bylo úspěšné. v opačném případě 0.

### <a name="remarks"></a>Poznámky

Nastavte *bRedraw* na hodnotu false vždy, když se posuvník bude překreslovat následným voláním jiné funkce, aby se předešlo tomu, že se posuvník v krátkém intervalu znovu vykreslí dvakrát.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CScrollBar:: SetScrollRange](#setscrollrange).

##  <a name="setscrollrange"></a>CScrollBar::SetScrollRange

Nastaví minimální a maximální hodnoty pozice pro daný posuvník.

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nMinPos*<br/>
Určuje minimální pozici posouvání.

*nMaxPos*<br/>
Určuje maximální pozici posouvání.

*bRedraw*<br/>
Určuje, zda má být překreslen posuvník, aby odrážel změnu. Pokud má *bRedraw* hodnotu true, posuvník se překreslí; Pokud je hodnota FALSE, není překreslena. Ve výchozím nastavení se překreslí.

### <a name="remarks"></a>Poznámky

Chcete-li skrýt standardní posuvníky, nastavte *nMinPos* a *nMaxPos* na 0.

Nevolejte tuto funkci, pokud chcete skrýt posuvník při zpracování zprávy s upozorněním na posuvníku.

Pokud volání `SetScrollRange` bezprostředně následuje volání `SetScrollPos` členské `SetScrollPos` funkce, nastavte *bRedraw* na hodnotu 0, aby se předešlo překreslování posuvníku dvakrát.

Rozdíl mezi hodnotami zadanými v *nMinPos* a *nMaxPos* nesmí být větší než 32 767. Výchozí rozsah ovládacího prvku posuvníku je prázdný ( *nMinPos* i *nMaxPos* jsou 0).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

##  <a name="showscrollbar"></a>CScrollBar:: ShowScrollBar

Zobrazí nebo skryje posuvník.

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Určuje, zda je zobrazen posuvník nebo skrytý. Pokud má tento parametr hodnotu TRUE, zobrazí se posuvník. v opačném případě je skrytá.

### <a name="remarks"></a>Poznámky

Aplikace by neměla volat tuto funkci, aby se skryl posuvník při zpracování zprávy s upozorněním na posuvníku.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CScrollBar:: Create](#create).

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[CStatic – třída](../../mfc/reference/cstatic-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
