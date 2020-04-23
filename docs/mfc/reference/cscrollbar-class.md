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
ms.openlocfilehash: 2079e12eccde42fe8c456a7852a029f44ae3cd77
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754399"
---
# <a name="cscrollbar-class"></a>CScrollBar – třída

Poskytuje funkce ovládacího prvku posouvání systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CScrollBar : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CScrollBar::CScrollBar](#cscrollbar)|Vytvoří `CScrollBar` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CScrollBar::Vytvořit](#create)|Vytvoří posuvník systému Windows `CScrollBar` a připojí jej k objektu.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Povolí nebo zakáže jednu nebo obě šipky posuvníku.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Načte informace o posuvníku `SCROLLBARINFO` pomocí struktury.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Načte informace o posuvníku.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Načte limit posuvníku.|
|[CScrollBar::GetScrollPos](#getscrollpos)|Načte aktuální pozici posuvníku.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Načte aktuální minimální a maximální pozice posuvníku pro daný posuvník.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Nastaví informace o posuvníku.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Nastaví aktuální pozici posuvníku.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Nastaví minimální a maximální hodnoty polohy pro daný posuvník.|
|[CScrollBar::Zobrazit posuvník](#showscrollbar)|Zobrazí nebo skryje posuvník.|

## <a name="remarks"></a>Poznámky

Ovládací prvek posuvníku vytvoříte ve dvou krocích. Nejprve zavolejte `CScrollBar` konstruktoru `CScrollBar` k vytvoření objektu a pak [voláním](#create) create member function `CScrollBar` vytvořte ovládací prvek posuvníku systému Windows a připojte jej k objektu.

Pokud vytvoříte `CScrollBar` objekt v dialogovém okně (prostřednictvím prostředku dialogového okna), `CScrollBar` bude automaticky zničen, když uživatel zavře dialogové okno.

Pokud vytvoříte `CScrollBar` objekt v okně, může být také nutné jej zničit.

Pokud vytvoříte `CScrollBar` objekt v zásobníku, je automaticky zničen. Pokud vytvoříte `CScrollBar` objekt na haldě pomocí **nové** funkce, musíte volat **delete** na objekt zničit, když uživatel ukončí posuvník systému Windows.

Pokud přidělíte všechny `CScrollBar` paměti v `CScrollBar` objektu, přepsat destruktor k vyřazení přidělení.

Související informace o `CScrollBar`použití naleznete v [tématu Controls](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar::Vytvořit

Vytvoří posuvník systému Windows `CScrollBar` a připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl posuvníku. Na posuvník použijte libovolnou [kombinaci stylů posuvníku.](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)

*Rect*<br/>
Určuje velikost a umístění posuvníku. Může být `RECT` buď struktura `CRect` nebo objekt.

*pParentWnd*<br/>
Určuje nadřazené okno posuvníku, obvykle `CDialog` objekt. Nesmí být null.

*Nid*<br/>
ID ovládacího prvku posuvníku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CScrollBar` dvou krocích. Nejprve volání konstruktoru, který `CScrollBar` vytvoří objekt; potom `Create`volání , který vytvoří a inicializuje přidružené posuvníku systému Windows a připojí jej k objektu. `CScrollBar`

Na posuvníku použijte následující [styly oken:](../../mfc/reference/styles-used-by-mfc.md#window-styles)

- WS_CHILD vždy

- WS_VISIBLE Obvykle

- WS_DISABLED Zřídka

- WS_GROUP Chcete-li seskupit ovládací prvky

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar::CScrollBar

Vytvoří `CScrollBar` objekt.

```
CScrollBar();
```

### <a name="remarks"></a>Poznámky

Po vytvoření objektu volejte `Create` členská funkci k vytvoření a inicializaci posuvníku systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar::EnableScrollBar

Povolí nebo zakáže jednu nebo obě šipky posuvníku.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parametry

*nArrowFlags*<br/>
Určuje, zda jsou šipky posuvníku povoleny nebo zakázány a které šipky jsou povoleny nebo zakázány. Tento parametr může být jedna z následujících hodnot:

- ESB_ENABLE_BOTH Povolí obě šipky posuvníku.

- ESB_DISABLE_LTUP Zakáže levou šipku vodorovného posuvníku nebo šipku nahoru svislého posuvníku.

- ESB_DISABLE_RTDN Zakáže pravou šipku vodorovného posuvníku nebo šipku dolů svislého posuvníku.

- ESB_DISABLE_BOTH Zakáže obě šipky posuvníku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou šipky povoleny nebo zakázány podle specifikace; jinak 0, což znamená, že šipky jsou již v požadovaném stavu nebo že došlo k chybě.

### <a name="example"></a>Příklad

  Viz příklad pro [CScrollBar::SetScrollRange](#setscrollrange).

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar::GetScrollBarInfo

Načte informace, `SCROLLBARINFO` které struktura udržuje o posuvníku.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parametry

*pScrollInfo*<br/>
Ukazatel na strukturu [SCROLLBARINFO.](/windows/win32/api/winuser/ns-winuser-scrollbarinfo)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [zprávy SBM_SCROLLBARINFO,](/windows/win32/Controls/sbm-getscrollbarinfo) jak je popsáno v sadě Windows SDK.

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

Načte informace, `SCROLLINFO` které struktura udržuje o posuvníku.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Ukazatel na strukturu [SCROLLINFO.](/windows/win32/api/winuser/ns-winuser-scrollinfo) Další informace o této struktuře naleznete v ksouboru Windows SDK.

*nMaska*<br/>
Určuje parametry posuvníku, které chcete načíst. Typické použití, SIF_ALL, určuje kombinaci SIF_PAGE, SIF_POS, SIF_TRACKPOS a SIF_RANGE. Další `SCROLLINFO` informace o hodnotách nMask naleznete v tématu.

### <a name="return-value"></a>Návratová hodnota

Pokud zpráva načetla všechny hodnoty, je vrácena hodnota TRUE. V opačném případě je false.

### <a name="remarks"></a>Poznámky

`GetScrollInfo`umožňuje aplikacím používat 32bitové polohy posouvání.

Struktura [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) obsahuje informace o posuvníku, včetně minimálnía maximální polohy posouvání, velikosti stránky a umístění posuvníku (palce). Další `SCROLLINFO` informace o změně výchozích hodnot struktury naleznete v tématu struktury v sadě Windows SDK.

Obslužné rutiny zpráv knihovny MFC Windows, které označují pozici posuvníku [CWnd::OnHScroll a [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), poskytují pouze 16 bitů dat polohy. `GetScrollInfo`a `SetScrollInfo` poskytují 32 bitů dat polohy posuvníku. Aplikace tedy může `GetScrollInfo` volat při `CWnd::OnHScroll` `CWnd::OnVScroll` zpracování buď nebo získat 32bitová data polohy posuvníku.

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

Načte maximální polohu posouvání posuvníku.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Návratová hodnota

Určuje maximální polohu posuvníku, pokud je úspěšný; jinak 0.

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar::GetScrollPos

Načte aktuální pozici posuvníku.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Určuje aktuální pozici posuvníku, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aktuální pozice je relativní hodnota, která závisí na aktuální rozsah posouvání. Pokud je například rozsah posouvání 100 až 200 a posuvník je uprostřed panelu, je aktuální pozice 150.

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::GetScrollRange

Zkopíruje aktuální minimální a maximální pozice posuvníku pro daný posuvník do umístění určených *lpMinPos* a *lpMaxPos*.

```cpp
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parametry

*lpMinPos*<br/>
Odkazuje na celou proměnnou, která má získat minimální pozici.

*lpMaxPos*<br/>
Odkazuje na celou proměnnou, která má získat maximální pozici.

### <a name="remarks"></a>Poznámky

Výchozí rozsah pro ovládací prvek posuvníku je prázdný (obě hodnoty jsou 0).

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

Nastaví informace, `SCROLLINFO` které struktura udržuje o posuvníku.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Ukazatel na strukturu [SCROLLINFO.](/windows/win32/api/winuser/ns-winuser-scrollinfo)

*bPřekreslit*<br/>
Určuje, zda má být posuvník překreslen tak, aby odrážel nové informace. Pokud *je bRedraw* TRUE, posuvník se překreslí. Pokud je false, není překreslena. Posuvník je ve výchozím nastavení překreslen.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, je vrácena pravda. V opačném případě je false.

### <a name="remarks"></a>Poznámky

Je nutné zadat hodnoty `SCROLLINFO` vyžadované parametry struktury, včetně hodnoty příznaku.

Struktura `SCROLLINFO` obsahuje informace o posuvníku, včetně minimální a maximální polohy posouvání, velikoststránky a umístění posuvníku (palec). Další informace o změně výchozích hodnot struktury naleznete v tématu struktury [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::SetScrollPos

Nastaví aktuální pozici posuvníku na pozici určenou *nPos* a pokud je zadána, překreslí posuvník tak, aby odrážel novou pozici.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje novou pozici posuvníku. Musí být v rozsahu posouvání.

*bPřekreslit*<br/>
Určuje, zda má být posuvník překreslen tak, aby odrážel novou pozici. Pokud *je bRedraw* TRUE, posuvník se překreslí. Pokud je false, není překreslena. Posuvník je ve výchozím nastavení překreslen.

### <a name="return-value"></a>Návratová hodnota

Určuje předchozí pozici posuvníku, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nastavte *bRedraw* na FALSE vždy, když posuvník bude překreslen následným voláním na jinou funkci, aby se zabránilo překreslení posuvníku dvakrát v krátkém intervalu.

### <a name="example"></a>Příklad

  Viz příklad pro [CScrollBar::SetScrollRange](#setscrollrange).

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::SetScrollRange

Nastaví minimální a maximální hodnoty polohy pro daný posuvník.

```cpp
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nMinPos*<br/>
Určuje minimální polohu posouvání.

*nMaxPos*<br/>
Určuje maximální polohu posouvání.

*bPřekreslit*<br/>
Určuje, zda má být posuvník překreslen tak, aby odrážel změnu. Pokud *je bRedraw* TRUE, posuvník se překreslí; pokud false, není překreslena. Ve výchozím nastavení je překreslen.

### <a name="remarks"></a>Poznámky

Nastavte *nMinPos* a *nMaxPos* na 0, chcete-li skrýt standardní posuvníky.

Nevolat tuto funkci skrýt posuvník při zpracování oznámení posuvníku.

Pokud volání `SetScrollRange` bezprostředně následuje volání `SetScrollPos` členské funkce, nastavte *bRedraw* v `SetScrollPos` 0 zabránit posuvníku překreslit dvakrát.

Rozdíl mezi hodnotami určenými *nMinPos* a *nMaxPos* nesmí být větší než 32 767. Výchozí oblast pro ovládací prvek posuvníku je prázdná *(nMinPos* i *nMaxPos* jsou 0).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar::Zobrazit posuvník

Zobrazí nebo skryje posuvník.

```cpp
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
Určuje, zda je posuvník zobrazen nebo skryt. Pokud je tento parametr TRUE, zobrazí se posuvník; jinak je skrytý.

### <a name="remarks"></a>Poznámky

Aplikace by neměla volat tuto funkci skrýt posuvník při zpracování oznámení posuvníku.

### <a name="example"></a>Příklad

  Viz příklad [cscrollbar::create](#create).

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[Třída CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[CStatic – třída](../../mfc/reference/cstatic-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
