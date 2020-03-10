---
title: Atributu CProgressCtrl – třída
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
ms.openlocfilehash: 9d63a1113e521eb73c99c47b335eb7ab00ccd753
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866321"
---
# <a name="cprogressctrl-class"></a>Atributu CProgressCtrl – třída

Poskytuje funkce pro běžný ovládací prvek indikátoru průběhu Windows.

## <a name="syntax"></a>Syntaxe

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Atributu CProgressCtrl:: atributu CProgressCtrl](#cprogressctrl)|Vytvoří objekt `CProgressCtrl`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Atributu CProgressCtrl:: Create](#create)|Vytvoří ovládací prvek indikátor průběhu a připojí ho k objektu `CProgressCtrl`.|
|[Atributu CProgressCtrl:: CreateEx](#createex)|Vytvoří ovládací prvek průběh se zadanými rozšířenými styly Windows a připojí ho k objektu `CProgressCtrl`.|
|[Atributu CProgressCtrl:: GetBarColor](#getbarcolor)|Získá barvu indikátoru indikátoru průběhu pro aktuální ovládací prvek indikátoru průběhu.|
|[Atributu CProgressCtrl:: GetBkColor](#getbkcolor)|Získá barvu pozadí aktuálního indikátoru průběhu.|
|[Atributu CProgressCtrl:: GetPos](#getpos)|Získá aktuální pozici indikátoru průběhu.|
|[Atributu CProgressCtrl:: GetRange](#getrange)|Získá dolní a horní meze rozsahu ovládacího prvku indikátor průběhu.|
|[Atributu CProgressCtrl:: GetState](#getstate)|Získá stav aktuálního ovládacího prvku indikátoru průběhu.|
|[Atributu CProgressCtrl:: getstep](#getstep)|Načte krok přírůstku indikátoru průběhu aktuálního ovládacího prvku indikátor průběhu.|
|[Atributu CProgressCtrl:: OffsetPos](#offsetpos)|Posune aktuální pozici ovládacího prvku indikátor průběhu podle zadaného přírůstku a překreslí pruh tak, aby odrážel novou pozici.|
|[Atributu CProgressCtrl:: SetBarColor](#setbarcolor)|Nastaví barvu indikátoru průběhu v aktuálním ovládacím prvku indikátor průběhu.|
|[Atributu CProgressCtrl:: SetBkColor](#setbkcolor)|Nastaví barvu pozadí indikátoru průběhu.|
|[Atributu CProgressCtrl:: SetMarquee](#setmarquee)|Zapne nebo vypne režim běžícího textu pro aktuální ovládací prvek indikátoru průběhu.|
|[Atributu CProgressCtrl:: SetPos](#setpos)|Nastaví aktuální pozici ovládacího prvku indikátor průběhu a překreslí pruh tak, aby odrážel novou pozici.|
|[Atributu CProgressCtrl:: SetRange](#setrange)|Nastaví minimální a maximální rozsah pro ovládací prvek indikátoru průběhu a překreslí pruh tak, aby odrážel nové rozsahy.|
|[Atributu CProgressCtrl:: SetState](#setstate)|Nastaví stav aktuálního ovládacího prvku indikátoru průběhu.|
|[Atributu CProgressCtrl:: SetStep](#setstep)|Určuje přírůstek kroku ovládacího prvku indikátor průběhu.|
|[Atributu CProgressCtrl:: StepIt](#stepit)|Posune aktuální pozici ovládacího prvku indikátor průběhu krokový přírůstek (viz [SetStep](#setstep)) a překreslí pruh tak, aby odrážel novou pozici.|

## <a name="remarks"></a>Poznámky

Ovládací prvek indikátor průběhu je okno, které může aplikace použít k indikaci průběhu operace s délkou. Skládá se z obdélníku, který se postupně vyplní, zleva doprava a Barva zvýraznění systému jako průběh operace.

Ovládací prvek indikátoru průběhu má rozsah a aktuální pozici. Rozsah představuje celkovou dobu trvání operace a aktuální pozice představuje průběh, který aplikace provedla směrem k dokončení operace. Procedura okna používá rozsah a aktuální pozici k určení procenta indikátoru průběhu k vyplnění barvou zvýraznění. Vzhledem k tomu, že hodnoty rozsah a aktuální pozice jsou vyjádřeny jako podepsaná celá čísla, může být možný rozsah aktuálních hodnot pozice od-2 147 483 648 do 2 147 483 647 včetně.

Další informace o použití `CProgressCtrl`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using atributu CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="cprogressctrl"></a>Atributu CProgressCtrl:: atributu CProgressCtrl

Vytvoří objekt `CProgressCtrl`.

```
CProgressCtrl();
```

### <a name="remarks"></a>Poznámky

Po sestavení objektu `CProgressCtrl` volejte `CProgressCtrl::Create` k vytvoření ovládacího prvku indikátor průběhu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

##  <a name="create"></a>Atributu CProgressCtrl:: Create

Vytvoří ovládací prvek indikátor průběhu a připojí ho k objektu `CProgressCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku indikátor průběhu. Použít libovolnou kombinaci oken stylesdescribed v programu [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v Windows SDK kromě následujících stylů ovládacího prvku indikátor průběhu do ovládacího prvku:

- PBS_VERTICAL zobrazuje informace o průběhu vertikálně, shora dolů. Bez tohoto příznaku se ovládací prvek indikátoru průběhu zobrazí vodorovně, zleva doprava.

- PBS_SMOOTH ukazuje postupný, plynulý vyplňování ovládacího prvku indikátor průběhu. Bez tohoto příznaku ovládací prvek bude plnit bloky.

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku indikátor průběhu. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) . Vzhledem k tomu, že ovládací prvek musí být podřízené okno, zadané souřadnice jsou relativní vzhledem k oblasti klienta *pParentWnd*.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku indikátor průběhu, obvykle `CDialog`. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku indikátoru průběhu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je objekt `CProgressCtrl` úspěšně vytvořen; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Objekt `CProgressCtrl` vytvoříte ve dvou krocích. Nejprve volejte konstruktor, který vytvoří objekt `CProgressCtrl` a potom zavolejte `Create`, čímž se vytvoří ovládací prvek indikátor průběhu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

##  <a name="createex"></a>Atributu CProgressCtrl:: CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ho k objektu `CProgressCtrl`.

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
Určuje styl ovládacího prvku indikátor průběhu. Použití libovolné kombinace stylů oken popsaných v části [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v Windows SDK.

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) popisující velikost a umístění okna, které má být vytvořeno, v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*nID*<br/>
ID podřízeného okna ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` namísto [Create](#create) k použití rozšířených stylů Windows, které jsou určené **WS_EX_m**ve stylu rozšířených stylů Windows.

##  <a name="getbarcolor"></a>Atributu CProgressCtrl:: GetBarColor

Získá barvu indikátoru indikátoru průběhu pro aktuální ovládací prvek indikátoru průběhu.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva indikátoru aktuálního průběhu, reprezentovaná jako hodnota [COLORREF](/windows/win32/gdi/colorref) , nebo CLR_DEFAULT, pokud je barva panelu indikátoru průběhu výchozí barvou.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor) , která je popsána v Windows SDK.

##  <a name="getbkcolor"></a>Atributu CProgressCtrl:: GetBkColor

Získá barvu pozadí aktuálního indikátoru průběhu.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva pozadí aktuálního indikátoru průběhu reprezentovaná jako hodnota [COLORREF](/windows/win32/gdi/colorref)

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor) , která je popsána v Windows SDK.

##  <a name="getpos"></a>Atributu CProgressCtrl:: GetPos

Načte aktuální pozici indikátoru průběhu.

```
int GetPos();
```

### <a name="return-value"></a>Návratová hodnota

Pozice ovládacího prvku indikátor průběhu.

### <a name="remarks"></a>Poznámky

Pozice ovládacího prvku indikátoru průběhu není na obrazovce na fyzickém místě, ale je mezi horním a dolním rozsahem uvedeným v [SetRange](#setrange).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

##  <a name="getrange"></a>Atributu CProgressCtrl:: GetRange

Získá aktuální dolní a horní meze nebo rozsah ovládacího prvku indikátoru průběhu.

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Parametry

*nLower*<br/>
Odkaz na celé číslo, které přijímá dolní limit ovládacího prvku indikátoru průběhu.

*nUpper*<br/>
Odkaz na celé číslo, které přijímá horní limit ovládacího prvku indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Tato funkce kopíruje hodnoty dolních a horních omezení na celá čísla, na která odkazují *nLower* a *nUpper*, v uvedeném pořadí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

##  <a name="getstate"></a>Atributu CProgressCtrl:: GetState

Získá stav aktuálního ovládacího prvku indikátoru průběhu.

```
int GetState() const;
```

### <a name="return-value"></a>Návratová hodnota

Stav aktuálního ovládacího prvku indikátor průběhu, což je jedna z následujících hodnot:

|Hodnota|Stav|
|-----------|-----------|
|PBST_NORMAL|Probíhá|
|PBST_ERROR|Chyba|
|PBST_PAUSED|Pozastaveno|

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PBM_GETSTATE](/windows/win32/Controls/pbm-getstate) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu načte stav aktuálního ovládacího prvku indikátoru průběhu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

##  <a name="getstep"></a>Atributu CProgressCtrl:: getstep

Načte krok přírůstku indikátoru průběhu aktuálního ovládacího prvku indikátor průběhu.

```
int GetStep() const;
```

### <a name="return-value"></a>Návratová hodnota

Krokový přírůstek indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Krok přírůstek je hodnota, o kterou volání [atributu CProgressCtrl:: StepIt](#stepit) zvyšuje aktuální pozici indikátoru průběhu.

Tato metoda pošle zprávu [PBM_GETSTEP](/windows/win32/Controls/pbm-getstep) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu načte krok přírůstku aktuálního ovládacího prvku indikátor průběhu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

##  <a name="offsetpos"></a>Atributu CProgressCtrl:: OffsetPos

Přesune aktuální pozici ovládacího prvku indikátoru průběhu na základě přírůstku zadaného parametrem *nPos* a překreslí pruh tak, aby odrážel novou pozici.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Velikost, která se má posunout na pozici

### <a name="return-value"></a>Návratová hodnota

Předchozí pozice ovládacího prvku indikátor průběhu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

##  <a name="setbarcolor"></a>Atributu CProgressCtrl:: SetBarColor

Nastaví barvu indikátoru průběhu v aktuálním ovládacím prvku indikátor průběhu.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*clrBar*|pro Hodnota [COLORREF](/windows/win32/gdi/colorref) , která určuje novou barvu řádku indikátoru průběhu. Zadejte CLR_DEFAULT, který způsobí, že indikátor průběhu bude používat výchozí barvu.|

### <a name="return-value"></a>Návratová hodnota

Předchozí Barva řádku indikátoru průběhu, reprezentovaná jako [COLORREFá](/windows/win32/gdi/colorref) hodnota, nebo CLR_DEFAULT, pokud je barva řádku indikátoru průběhu výchozí barvou.

### <a name="remarks"></a>Poznámky

Metoda `SetBarColor` nastaví barvu indikátoru průběhu pouze v případě, že [motiv](/windows/win32/Controls/visual-styles-overview) systému Windows Vista není platný.

Tato metoda pošle zprávu [PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu změní barvu indikátoru průběhu na červenou, zelenou, modrou nebo výchozí hodnotu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

##  <a name="setbkcolor"></a>Atributu CProgressCtrl:: SetBkColor

Nastaví barvu pozadí indikátoru průběhu.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Parametry

*clrNew*<br/>
Hodnota COLORREF, která určuje novou barvu pozadí. Zadejte hodnotu CLR_DEFAULT pro použití výchozí barvy pozadí pro indikátor průběhu.

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) označující předchozí barvu pozadí nebo CLR_DEFAULT, pokud je barva pozadí výchozí barvou.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

##  <a name="setmarquee"></a>Atributu CProgressCtrl:: SetMarquee

Zapne nebo vypne režim běžícího textu pro aktuální ovládací prvek indikátoru průběhu.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*fMarqueeMode*|pro TRUE pro zapnutí režimu hranice výběru nebo FALSE pro vypnutí režimu výběru.|
|*nInterval*|pro Doba v milisekundách mezi aktualizacemi animace běžícího výběru.|

### <a name="return-value"></a>Návratová hodnota

Tato metoda vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Když je režim běžícího textu zapnutý, je indikátor průběhu animovaný a posouvá se jako znak pro výběr v kino.

Tato metoda pošle zprávu [PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu začíná a zastaví animaci posouvání běžícího rámečku.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

##  <a name="setpos"></a>Atributu CProgressCtrl:: SetPos

Nastaví aktuální pozici ovládacího prvku indikátoru průběhu zadanou v *nPos* a překreslí pruh tak, aby odrážel novou pozici.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Nová pozice ovládacího prvku indikátor průběhu

### <a name="return-value"></a>Návratová hodnota

Předchozí pozice ovládacího prvku indikátor průběhu.

### <a name="remarks"></a>Poznámky

Pozice ovládacího prvku indikátoru průběhu není na obrazovce na fyzickém místě, ale je mezi horním a dolním rozsahem uvedeným v [SetRange](#setrange).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

##  <a name="setrange"></a>Atributu CProgressCtrl:: SetRange

Nastaví horní a dolní limity rozsahu ovládacího prvku indikátoru průběhu a překreslí pruh tak, aby odrážel nové rozsahy.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parametry

*nLower*<br/>
Určuje dolní limit rozsahu (výchozí hodnota je nula).

*nUpper*<br/>
Určuje horní limit rozsahu (výchozí hodnota je 100).

### <a name="remarks"></a>Poznámky

Členská funkce `SetRange32` nastaví rozsah 32 pro ovládací prvek průběh.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

##  <a name="setstate"></a>Atributu CProgressCtrl:: SetState

Nastaví stav aktuálního ovládacího prvku indikátoru průběhu.

```
int SetState(int iState);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*v-Tate*|pro Stav pro nastavení indikátoru průběhu. Použijte jednu z následujících hodnot:<br /><br /> -Probíhá PBST_NORMAL<br />-PBST_ERROR – chyba<br />-PBST_PAUSED – pozastaveno|

### <a name="return-value"></a>Návratová hodnota

Předchozí stav aktuálního ovládacího prvku indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PBM_SETSTATE](/windows/win32/Controls/pbm-setstate) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která se používá k programovému přístupu k ovládacímu prvku indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví stav aktuálního ovládacího prvku indikátoru průběhu na pozastaveno nebo probíhá.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

##  <a name="setstep"></a>Atributu CProgressCtrl:: SetStep

Určuje přírůstek kroku ovládacího prvku indikátor průběhu.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Parametry

*nStep*<br/>
Přírůstek nového kroku

### <a name="return-value"></a>Návratová hodnota

Krok v předchozím kroku.

### <a name="remarks"></a>Poznámky

Krok přírůstek je hodnota, o kterou volání `CProgressCtrl::StepIt` zvyšuje aktuální pozici indikátoru průběhu.

Výchozí přírůstkový krok je 10.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

##  <a name="stepit"></a>Atributu CProgressCtrl:: StepIt

Posune aktuální pozici ovládacího prvku indikátor průběhu krok za krokem a překreslí pruh tak, aby odrážel novou pozici.

```
int StepIt();
```

### <a name="return-value"></a>Návratová hodnota

Předchozí pozice ovládacího prvku indikátor průběhu.

### <a name="remarks"></a>Poznámky

Krokový přírůstek je nastaven pomocí členské funkce `CProgressCtrl::SetStep`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Viz také

[CMNCTRL2 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
