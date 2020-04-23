---
title: CProgressCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
ms.openlocfilehash: c9e94e334318b32efcf8c9de681a78349ab12151
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751134"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl – třída

Poskytuje funkce ovládacího prvku Windows common progress bar.

## <a name="syntax"></a>Syntaxe

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Vytvoří `CProgressCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CProgressCtrl::Vytvořit](#create)|Vytvoří ovládací prvek indikátor průběhu a `CProgressCtrl` připojí jej k objektu.|
|[CProgressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek průběhu se zadanými rozšířenými `CProgressCtrl` styly systému Windows a připojí jej k objektu.|
|[CProgressCtrl::GetBarColor](#getbarcolor)|Získá barvu indikátoru průběhu pro aktuální ovládací prvek indikátor průběhu.|
|[CProgressCtrl::GetBkColor](#getbkcolor)|Získá barvu pozadí aktuální indikátor průběhu.|
|[CProgressCtrl::GetPos](#getpos)|Získá aktuální pozici indikátoru průběhu.|
|[CProgressCtrl::GetRange](#getrange)|Získá dolní a horní hranice rozsahu ovládacího prvku indikátor průběhu.|
|[CProgressCtrl::GetState](#getstate)|Získá stav aktuálního ovládacího prvku indikátoru průběhu.|
|[CProgressCtrl::GetStep](#getstep)|Načte přírůstek kroku pro indikátor průběhu aktuálního ovládacího prvku indikátoru průběhu.|
|[CProgressCtrl::OffsetPos](#offsetpos)|Posune aktuální pozici ovládacího prvku indikátoru průběhu o zadaný přírůstek a překreslí pruh tak, aby odrážel novou pozici.|
|[CProgressCtrl::SetBarColor](#setbarcolor)|Nastaví barvu indikátoru průběhu v aktuálním ovládacím prvku indikátoru průběhu.|
|[CProgressCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí pro indikátor průběhu.|
|[CProgressCtrl::SetMarquee](#setmarquee)|Zapne nebo vypne režim výběru pro aktuální ovládací prvek indikátoru průběhu.|
|[CProgressCtrl::SetPos](#setpos)|Nastaví aktuální pozici pro ovládací prvek indikátoru průběhu a překreslí pruh tak, aby odrážel novou pozici.|
|[CProgressCtrl::SetRange](#setrange)|Nastaví minimální a maximální rozsahy pro ovládací prvek indikátoru průběhu a překreslí pruh tak, aby odrážel nové rozsahy.|
|[CProgressCtrl::SetState](#setstate)|Nastaví stav aktuálního ovládacího prvku indikátoru průběhu.|
|[CProgressCtrl::SetStep](#setstep)|Určuje přírůstek kroku pro ovládací prvek indikátoru průběhu.|
|[CProgressCtrl::StepIt](#stepit)|Posune aktuální pozici ovládacího prvku indikátoru průběhu o krokový přírůstek (viz [SetStep)](#setstep)a překreslí pruh tak, aby odrážel novou pozici.|

## <a name="remarks"></a>Poznámky

Ovládací prvek indikátor průběhu je okno, které aplikace může použít k označení průběhu zdlouhavé operace. Skládá se z obdélníku, který je postupně vyplněn, zleva doprava, s barvou zvýraznění systému v průběhu operace.

Ovládací prvek indikátoru průběhu má rozsah a aktuální pozici. Rozsah představuje celkovou dobu trvání operace a aktuální pozice představuje pokrok, který aplikace provedla k dokončení operace. Procedura okna používá rozsah a aktuální pozici k určení procenta indikátoru průběhu, který má být vyplnín barvou zvýraznění. Vzhledem k tomu, že hodnoty rozsahu a aktuální pozice jsou vyjádřeny jako podepsaná celá čísla, možný rozsah hodnot aktuální pozice je od -2,147,483,648 do 2,147,483,647 včetně.

Další informace o `CProgressCtrl`použití naleznete v [tématech Ovládací prvky](../../mfc/controls-mfc.md) a [Použití kláves CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="cprogressctrlcprogressctrl"></a><a name="cprogressctrl"></a>CProgressCtrl::CProgressCtrl

Vytvoří `CProgressCtrl` objekt.

```
CProgressCtrl();
```

### <a name="remarks"></a>Poznámky

Po vytvoření `CProgressCtrl` objektu `CProgressCtrl::Create` volejte k vytvoření ovládacího prvku indikátoru průběhu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

## <a name="cprogressctrlcreate"></a><a name="create"></a>CProgressCtrl::Vytvořit

Vytvoří ovládací prvek indikátor průběhu a `CProgressCtrl` připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl ovládacího prvku indikátoru průběhu. Použijte libovolnou kombinaci stylů oken popsané v [createwindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v sadě Windows SDK, kromě následujících stylů řízení indikátoru průběhu, na ovládací prvek:

- PBS_VERTICAL Zobrazí informace o průběhu svisle, shora dolů. Bez tohoto příznaku se ovládací prvek indikátoru průběhu zobrazí vodorovně zleva doprava.

- PBS_SMOOTH Zobrazí postupné a hladké vyplnění ovládacího prvku indikátoru průběhu. Bez tohoto příznaku se ovládací prvek naplní bloky.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku indikátoru průběhu. Může to být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/windows/win32/api/windef/ns-windef-rect) struktury. Vzhledem k tomu, že ovládací prvek musí být podřízené okno, zadané souřadnice jsou relativní vzhledem k klientské oblasti *pParentWnd*.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího `CDialog`prvku indikátoru průběhu, obvykle . Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku indikátoru průběhu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, `CProgressCtrl` pokud je objekt úspěšně vytvořen; jinak FALSE.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CProgressCtrl` dvou krocích. Nejprve zavolejte konstruktor, `CProgressCtrl` který vytvoří objekt, a potom volání `Create`, který vytvoří ovládací prvek indikátor průběhu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

## <a name="cprogressctrlcreateex"></a><a name="createex"></a>CProgressCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a `CProgressCtrl` přidruží jej k objektu.

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
Určuje styl ovládacího prvku indikátoru průběhu. Použijte libovolnou kombinaci stylů oken popsanou v [createwindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v sadě Windows SDK.

*Rect*<br/>
Odkaz na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu popisující velikost a umístění okna, které mají být vytvořeny, v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*Nid*<br/>
ID podřízeného okna ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` funkce [Vytvořit](#create) použijte použití rozšířených stylů systému Windows určených **předmluvou**rozšířeného stylu systému Windows WS_EX_ .

## <a name="cprogressctrlgetbarcolor"></a><a name="getbarcolor"></a>CProgressCtrl::GetBarColor

Získá barvu indikátoru průběhu pro aktuální ovládací prvek indikátor průběhu.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva aktuálního indikátoru průběhu, reprezentovaná jako hodnota [COLORREF,](/windows/win32/gdi/colorref) nebo CLR_DEFAULT, zda je výchozí barvou indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PBM_GETBARCOLOR,](/windows/win32/Controls/pbm-getbarcolor) která je popsána v sadě Windows SDK.

## <a name="cprogressctrlgetbkcolor"></a><a name="getbkcolor"></a>CProgressCtrl::GetBkColor

Získá barvu pozadí aktuální indikátor průběhu.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva pozadí aktuálního indikátoru průběhu reprezentovaná jako hodnota [COLORREF.](/windows/win32/gdi/colorref)

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PBM_GETBKCOLOR,](/windows/win32/Controls/pbm-getbkcolor) která je popsána v sadě Windows SDK.

## <a name="cprogressctrlgetpos"></a><a name="getpos"></a>CProgressCtrl::GetPos

Načte aktuální pozici indikátoru průběhu.

```
int GetPos();
```

### <a name="return-value"></a>Návratová hodnota

Pozice ovládacího prvku indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Pozice ovládacího prvku indikátor průběhu není fyzické umístění na obrazovce, ale je spíše mezi horní a dolní rozsah je uvedeno v [SetRange](#setrange).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

## <a name="cprogressctrlgetrange"></a><a name="getrange"></a>CProgressCtrl::GetRange

Získá aktuální dolní a horní limity nebo rozsah ovládacího prvku indikátor průběhu.

```cpp
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Parametry

*nNižší*<br/>
Odkaz na celé číslo, které přijímá dolní limit ovládacího prvku indikátoru průběhu.

*nHorní*<br/>
Odkaz na celé číslo, které přijímá horní limit ovládacího prvku indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Tato funkce zkopíruje hodnoty dolní a horní hranice na celá čísla odkazuje *nLower* a *nUpper*, resp.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

## <a name="cprogressctrlgetstate"></a><a name="getstate"></a>CProgressCtrl::GetState

Získá stav aktuálního ovládacího prvku indikátoru průběhu.

```
int GetState() const;
```

### <a name="return-value"></a>Návratová hodnota

Stav aktuálního ovládacího prvku indikátoru průběhu, který je jednou z následujících hodnot:

|Hodnota|Stav|
|-----------|-----------|
|PBST_NORMAL|Probíhá|
|PBST_ERROR|Chyba|
|PBST_PAUSED|Pozastaveno|

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PBM_GETSTATE,](/windows/win32/Controls/pbm-getstate) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_progressCtrl`která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu načte stav aktuálního ovládacího prvku indikátoru průběhu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

## <a name="cprogressctrlgetstep"></a><a name="getstep"></a>CProgressCtrl::GetStep

Načte přírůstek kroku pro indikátor průběhu aktuálního ovládacího prvku indikátoru průběhu.

```
int GetStep() const;
```

### <a name="return-value"></a>Návratová hodnota

Přírůstek kroku indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Krok přírůstek je částka, o kterou volání [CProgressCtrl::StepZvyšuje](#stepit) aktuální pozici indikátoru průběhu.

Tato metoda odešle [zprávu PBM_GETSTEP,](/windows/win32/Controls/pbm-getstep) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_progressCtrl`která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu načte krok přírůstek aktuální ho dimenzačního ovládacího prvku.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

## <a name="cprogressctrloffsetpos"></a><a name="offsetpos"></a>CProgressCtrl::OffsetPos

Posune aktuální pozici ovládacího prvku indikátoru průběhu o přírůstek určený *nPos* a překreslí pruh tak, aby odrážel novou pozici.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Částka pro zálohu na pozici.

### <a name="return-value"></a>Návratová hodnota

Předchozí pozice ovládacího prvku indikátorprůběhu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

## <a name="cprogressctrlsetbarcolor"></a><a name="setbarcolor"></a>CProgressCtrl::SetBarColor

Nastaví barvu indikátoru průběhu v aktuálním ovládacím prvku indikátoru průběhu.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*clrBar*|[v] Hodnota [COLORREF,](/windows/win32/gdi/colorref) která určuje novou barvu indikátoru průběhu. Určete CLR_DEFAULT, aby se indikátor průběhu použil jako výchozí barva.|

### <a name="return-value"></a>Návratová hodnota

Předchozí barva indikátoru průběhu, reprezentovaná jako hodnota [COLORREF,](/windows/win32/gdi/colorref) nebo CLR_DEFAULT, pokud je barva indikátoru průběhu výchozí barvou.

### <a name="remarks"></a>Poznámky

Metoda `SetBarColor` nastaví barvu indikátoru průběhu pouze v případě, že [motiv systému](/windows/win32/Controls/visual-styles-overview) Windows Vista není v platnosti.

Tato metoda odešle [zprávu PBM_SETBARCOLOR,](/windows/win32/Controls/pbm-setbarcolor) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_progressCtrl`která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu změní barvu indikátoru průběhu na červenou, zelenou, modrou nebo výchozí.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

## <a name="cprogressctrlsetbkcolor"></a><a name="setbkcolor"></a>CProgressCtrl::SetBkColor

Nastaví barvu pozadí pro indikátor průběhu.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Parametry

*clrNové*<br/>
Hodnota COLORREF, která určuje novou barvu pozadí. Určete CLR_DEFAULT hodnotu, která má použít výchozí barvu pozadí pro indikátor průběhu.

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) označující předchozí barvu pozadí nebo CLR_DEFAULT, zda je barva pozadí výchozí barvou.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

## <a name="cprogressctrlsetmarquee"></a><a name="setmarquee"></a>CProgressCtrl::SetMarquee

Zapne nebo vypne režim výběru pro aktuální ovládací prvek indikátoru průběhu.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*fMarqueeMode*|[v] TRUE zapnutí režimu výběru nebo NEPRAVDA pro vypnutí režimu výběru.|
|*nInterval*|[v] Čas v milisekundách mezi aktualizacemi animace výběru.|

### <a name="return-value"></a>Návratová hodnota

Tato metoda vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Když je režim výběru zapnutý, indikátor průběhu se animuje a posouvá se jako značka na rámečku divadla.

Tato metoda odešle [zprávu PBM_SETMARQUEE,](/windows/win32/Controls/pbm-setmarquee) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_progressCtrl`která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu spustí a zastaví animace posouvání výběru.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

## <a name="cprogressctrlsetpos"></a><a name="setpos"></a>CProgressCtrl::SetPos

Nastaví aktuální pozici ovládacího prvku indikátoru průběhu podle potřeby *nPos* a překreslí pruh tak, aby odrážel novou pozici.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Nová pozice ovládacího prvku indikátoru průběhu.

### <a name="return-value"></a>Návratová hodnota

Předchozí pozice ovládacího prvku indikátorprůběhu.

### <a name="remarks"></a>Poznámky

Pozice ovládacího prvku indikátor průběhu není fyzické umístění na obrazovce, ale je spíše mezi horní a dolní rozsah je uvedeno v [SetRange](#setrange).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

## <a name="cprogressctrlsetrange"></a><a name="setrange"></a>CProgressCtrl::SetRange

Nastaví horní a dolní meze rozsahu ovládacího prvku indikátoru průběhu a překreslí pruh tak, aby odrážel nové rozsahy.

```cpp
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parametry

*nNižší*<br/>
Určuje dolní hranici rozsahu (výchozí hodnota je nula).

*nHorní*<br/>
Určuje horní limit rozsahu (výchozí hodnota je 100).

### <a name="remarks"></a>Poznámky

Členská `SetRange32` funkce nastaví 32bitový rozsah pro řízení průběhu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

## <a name="cprogressctrlsetstate"></a><a name="setstate"></a>CProgressCtrl::SetState

Nastaví stav aktuálního ovládacího prvku indikátoru průběhu.

```
int SetState(int iState);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iState*|[v] Stav pro nastavení indikátoru průběhu. Použijte jednu z následujících hodnot:<br /><br /> - PBST_NORMAL - Probíhá<br />- PBST_ERROR - Chyba<br />- PBST_PAUSED - Pozastaveno|

### <a name="return-value"></a>Návratová hodnota

Předchozí stav aktuálního ovládacího prvku indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PBM_SETSTATE,](/windows/win32/Controls/pbm-setstate) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_progressCtrl`která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví stav aktuálního ovládacího prvku indikátoru průběhu na Pozastaveno nebo Probíhá.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

## <a name="cprogressctrlsetstep"></a><a name="setstep"></a>CProgressCtrl::SetStep

Určuje přírůstek kroku pro ovládací prvek indikátoru průběhu.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Parametry

*nKrok*<br/>
Nový krok přírůstek.

### <a name="return-value"></a>Návratová hodnota

Předchozí krok přírůstek.

### <a name="remarks"></a>Poznámky

Zvýšení kroku je částka, o kterou `CProgressCtrl::StepIt` volání zvyšuje aktuální pozici indikátoru průběhu.

Výchozí přírůstek kroku je 10.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

## <a name="cprogressctrlstepit"></a><a name="stepit"></a>CProgressCtrl::StepIt

Posune aktuální pozici ovládacího prvku indikátoru průběhu o krokový přírůstek a překreslí pruh tak, aby odrážel novou pozici.

```
int StepIt();
```

### <a name="return-value"></a>Návratová hodnota

Předchozí pozice ovládacího prvku indikátorprůběhu.

### <a name="remarks"></a>Poznámky

Přírůstek kroku je nastaven `CProgressCtrl::SetStep` členovou funkcí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
