---
title: Atributu CMonthCalCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
ms.openlocfilehash: 1215247c194d75409c43d3fe1968ebab9ca71781
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916840"
---
# <a name="cmonthcalctrl-class"></a>Atributu CMonthCalCtrl – třída

Zapouzdřuje funkce ovládacího prvku měsíční kalendář.

## <a name="syntax"></a>Syntaxe

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|`CMonthCalCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMonthCalCtrl::Create](#create)|Vytvoří ovládací prvek měsíční kalendář a připojí ho k `CMonthCalCtrl` objektu.|
|[Atributu CMonthCalCtrl:: GetCalendarBorder](#getcalendarborder)|Načte šířku ohraničení aktuálního ovládacího prvku měsíční kalendář.|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Načte počet kalendářů zobrazených v aktuálním měsíčním ovládacím prvku kalendáře.|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Načte informace o aktuálním ovládacím prvku měsíční kalendář.|
|[CMonthCalCtrl::GetCalID](#getcalid)|Načte identifikátor kalendáře pro ovládací prvek aktuálního měsíčního kalendáře.|
|[CMonthCalCtrl::GetColor](#getcolor)|Získá barvu zadané oblasti ovládacího prvku měsíční kalendář.|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Načte zobrazení, které je aktuálně zobrazeno ovládacím prvkem aktuálního měsíčního kalendáře.|
|[CMonthCalCtrl::GetCurSel](#getcursel)|Načte systémový čas, který je označen aktuálně vybraným datem.|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Načte první den v týdnu, který se zobrazí ve sloupci v kalendáři úplně vlevo.|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Načte aktuální maximální počet dní, které lze vybrat v ovládacím prvku měsíční kalendář.|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Načte maximální šířku řetězce "Today" pro aktuální ovládací prvek měsíčního kalendáře.|
|[Atributu CMonthCalCtrl:: GetMinReqRect](#getminreqrect)|Načte minimální velikost nutnou k zobrazení celého měsíce v ovládacím prvku měsíční kalendář.|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Načte rychlost posunutí pro ovládací prvek měsíční kalendář.|
|[Atributu CMonthCalCtrl:: GetMonthRange](#getmonthrange)|Načte informace o datu, které představují vysoké a nízké limity zobrazení ovládacího prvku měsíční kalendář.|
|[CMonthCalCtrl::GetRange](#getrange)|Načte aktuální minimální a maximální kalendářní datum nastavené v ovládacím prvku měsíční kalendář.|
|[CMonthCalCtrl::GetSelRange](#getselrange)|Načte informace o datu, které představují horní a dolní meze rozsahu dat aktuálně vybraného uživatelem.|
|[Atributu CMonthCalCtrl:: gettoday](#gettoday)|Načte informace o datu pro ovládací prvek měsíční kalendář pro datum zadané jako dnešní.|
|[CMonthCalCtrl::HitTest](#hittest)|Určuje, který oddíl ovládacího prvku měsíční kalendář se na obrazovce nachází na daném místě.|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Označuje, zda je aktuální zobrazení ovládacího prvku měsíční kalendář aktuálního kalendáře v zobrazení století.|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Označuje, zda aktuální zobrazení aktuálního ovládacího prvku měsíční kalendář představuje zobrazení dekády.|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Určuje, zda aktuální zobrazení aktuálního ovládacího prvku měsíční kalendář odpovídá zobrazení měsíce.|
|[CMonthCalCtrl::IsYearView](#isyearview)|Označuje, zda aktuální zobrazení aktuálního ovládacího prvku měsíční kalendář odpovídá zobrazení roku.|
|[Atributu CMonthCalCtrl:: SetCalendarBorder](#setcalendarborder)|Nastaví šířku ohraničení aktuálního ovládacího prvku měsíční kalendář.|
|[Atributu CMonthCalCtrl:: SetCalendarBorderDefault](#setcalendarborderdefault)|Nastaví výchozí šířku ohraničení aktuálního ovládacího prvku měsíční kalendář.|
|[CMonthCalCtrl::SetCalID](#setcalid)|Nastaví identifikátor kalendáře pro ovládací prvek aktuálního měsíčního kalendáře.|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Nastaví ovládací prvek aktuálního měsíčního kalendáře pro zobrazení století.|
|[CMonthCalCtrl::SetColor](#setcolor)|Nastaví barvu zadané oblasti ovládacího prvku měsíční kalendář.|
|[Atributu CMonthCalCtrl:: SetCurrentView](#setcurrentview)|Nastaví ovládací prvek aktuálního měsíčního kalendáře pro zobrazení zadaného zobrazení.|
|[CMonthCalCtrl::SetCurSel](#setcursel)|Nastaví aktuálně vybrané datum pro ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::SetDayState](#setdaystate)|Nastaví zobrazení pro dny v ovládacím prvku měsíční kalendář.|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Nastaví ovládací prvek aktuálního měsíčního kalendáře na zobrazení dekády.|
|[Atributu CMonthCalCtrl:: SetFirstDayOfWeek](#setfirstdayofweek)|Nastaví den v týdnu, který se má zobrazit v levém sloupci kalendáře.|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Nastaví maximální počet dní, které lze vybrat v ovládacím prvku měsíční kalendář.|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Nastaví rychlost posunutí pro ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Nastaví ovládací prvek aktuálního měsíčního kalendáře k zobrazení měsíce.|
|[Atributu CMonthCalCtrl:: SetRange](#setrange)|Nastaví minimální a maximální povolená data pro ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::SetSelRange](#setselrange)|Nastaví výběr pro ovládací prvek měsíčního kalendáře na daný rozsah kalendářních dat.|
|[Atributu CMonthCalCtrl:: SetToday](#settoday)|Nastaví ovládací prvek Kalendář pro aktuální den.|
|[Atributu CMonthCalCtrl:: SetYearView](#setyearview)|Nastaví aktuální měsíční ovládací prvek kalendářního kalendáře na zobrazení roků.|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Znovu vykreslí ovládací prvek měsíčního kalendáře do jeho minimální velikosti v jednom měsíci.|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Pro ovládací prvek aktuálního měsíčního kalendáře vypočítá nejmenší obdélník, který může obsahovat všechny kalendáře, které odpovídají zadanému obdélníku.|

## <a name="remarks"></a>Poznámky

Ovládací prvek měsíční kalendář poskytuje uživateli jednoduché rozhraní kalendáře, ze kterého může uživatel vybrat datum. Uživatel může zobrazení změnit:

- Posouvání zpět a dopředu, od měsíce po měsíc.

- Kliknutím na text dnešního dne zobrazíte aktuální den (Pokud se styl MCS_NOTODAY nepoužívá).

- Výběr měsíce nebo roku z místní nabídky.

Můžete přizpůsobit ovládací prvek měsíční kalendář použitím nejrůznějších stylů objektu při jeho vytváření. Tyto styly jsou popsány v Windows SDK [styly ovládacího prvku měsíční kalendář](/windows/desktop/Controls/month-calendar-control-styles) .

Ovládací prvek měsíční kalendář může zobrazit více než jeden měsíc a může indikovat zvláštní dny (například svátky) tučným datem.

Další informace o použití ovládacího prvku měsíční kalendář naleznete v tématu [using atributu CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDTCTL. h

##  <a name="cmonthcalctrl"></a>Atributu CMonthCalCtrl:: atributu CMonthCalCtrl

`CMonthCalCtrl` Vytvoří objekt.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Poznámky

Je nutné zavolat `Create` po vytvoření objektu.

##  <a name="create"></a>Atributu CMonthCalCtrl:: Create

Vytvoří ovládací prvek měsíční kalendář a připojí ho k `CMonthCalCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(
    DWORD dwStyle,
    const POINT& pt,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje kombinaci stylů Windows použitých pro ovládací prvek měsíční kalendář. Další informace o stylech naleznete v tématu [styly ovládacích prvků měsíčního kalendáře](/windows/desktop/Controls/month-calendar-control-styles) v Windows SDK.

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) . Obsahuje pozici a velikost ovládacího prvku měsíční kalendář.

*bodů*<br/>
Odkaz na strukturu [bodu](/previous-versions/dd162805\(v=vs.85\)) , která určuje umístění ovládacího prvku měsíční kalendář.

*pParentWnd*<br/>
Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je nadřazeným oknem ovládacího prvku měsíční kalendář. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku měsíčního kalendáře.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Vytvořte ovládací prvek měsíční kalendář ve dvou krocích:

1. Volání [atributu CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) k vytvoření `CMonthCalCtrl` objektu.

1. Zavolejte tuto členskou funkci, která vytvoří ovládací prvek měsíční kalendář a připojí ho k `CMonthCalCtrl` objektu.

Při volání `Create`jsou inicializovány běžné ovládací prvky. Způsob volání Určuje `Create` , jak má vaše verze:

- Chcete-li, aby knihovna MFC automaticky změnila velikost ovládacího prvku na jeden měsíc, zavolejte přepsání, které používá parametr *PT* .

- Chcete-li změnit velikost ovládacího prvku sami, zavolejte přepsání této funkce, která používá parametr *Rect* .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>Atributu CMonthCalCtrl:: GetCalendarBorder

Načte šířku ohraničení aktuálního ovládacího prvku měsíční kalendář.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka ohraničení ovládacího prvku (v pixelech)

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [MCM_GETCALENDARBORDER](/windows/desktop/Controls/mcm-getcalendarborder) , která je popsána v Windows SDK.

##  <a name="getcalendarcount"></a>Atributu CMonthCalCtrl:: GetCalendarCount

Načte počet kalendářů zobrazených v aktuálním měsíčním ovládacím prvku kalendáře.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet kalendářů, které jsou aktuálně zobrazeny v ovládacím prvku měsíční kalendář. Maximální povolený počet kalendářů je 12.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [MCM_GETCALENDARCOUNT](/windows/desktop/Controls/mcm-getcalendarcount) , která je popsána v Windows SDK.

##  <a name="getcalendargridinfo"></a>Atributu CMonthCalCtrl:: GetCalendarGridInfo

Načte informace o aktuálním ovládacím prvku měsíční kalendář.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pmcGridInfo*|mimo Ukazatel na strukturu [MCGRIDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagmcgridinfo) , která přijímá informace o aktuálním ovládacím prvku měsíční kalendář. Volající je zodpovědný za přidělení a inicializaci této struktury.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [MCM_GETCALENDARGRIDINFO](/windows/desktop/Controls/mcm-getcalendargridinfo) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která se používá k programovému přístupu k ovládacímu prvku měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu používá `GetCalendarGridInfo` metodu k načtení kalendářního data, které ovládací prvek aktuálního měsíčního kalendáře zobrazuje.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>Atributu CMonthCalCtrl:: GetCalID

Načte identifikátor kalendáře pro ovládací prvek aktuálního měsíčního kalendáře.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedna z konstant [identifikátoru kalendáře](/windows/desktop/Intl/calendar-identifiers) .

### <a name="remarks"></a>Poznámky

Identifikátor kalendáře označuje kalendář specifický pro oblast, jako je například gregoriánský (lokalizovaný), japonské nebo hidžra kalendáře. Vaše aplikace může používat identifikátor kalendáře s různými funkcemi podpory jazyka.

Tato metoda pošle zprávu [MCM_GETCALID](/windows/desktop/Controls/mcm-getcalid) , která je popsána v Windows SDK.

##  <a name="getcolor"></a>Atributu CMonthCalCtrl:: GetColor

Načte barvu oblasti ovládacího prvku měsíční kalendář určený parametrem *nRegion*.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Parametry

*nRegion*<br/>
Oblast ovládacího prvku měsíční kalendář, ze které je barva načtena. Seznam hodnot naleznete v parametru *NRegion* [SetColor](#setcolor).

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/desktop/gdi/colorref) určující barvu spojenou s částí ovládacího prvku měsíční kalendář, pokud byla úspěšná. V opačném případě vrátí tato členská funkce hodnotu-1.

##  <a name="getcurrentview"></a>Atributu CMonthCalCtrl:: GetCurrentView

Načte zobrazení, které je aktuálně zobrazeno ovládacím prvkem aktuálního měsíčního kalendáře.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zobrazení, které je označeno jednou z následujících hodnot:

|Value|Význam|
|-----------|-------------|
|MCMV_MONTH|Měsíční zobrazení|
|MCMV_YEAR|Roční zobrazení|
|MCMV_DECADE|Zobrazení dekády|
|MCMV_CENTURY|Zobrazení století|

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která se používá k programovému přístupu k ovládacímu prvku měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu hlásí zobrazení ovládacího prvku měsíční kalendář, který je aktuálně zobrazen.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>Atributu CMonthCalCtrl::

Načte systémový čas, který je označen aktuálně vybraným datem.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) . Přijme aktuální čas.

*pDateTime*<br/>
Ukazatel na strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) , která bude dostávat aktuálně vybrané informace o datu. Tento parametr musí být platná adresa a nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; otherwize 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETCURSEL](/windows/desktop/Controls/mcm-getcursel), jak je popsáno v Windows SDK.

> [!NOTE]
>  Tato členská funkce se nezdařila, pokud je nastaven styl MCS_MULTISELECT.

V implementaci `GetCurSel`knihovny MFC můžete `COleDateTime` určit použití, `CTime` použití nebo `SYSTEMTIME` strukturu použití.

##  <a name="getfirstdayofweek"></a>Atributu CMonthCalCtrl:: getprvní_den_v_týdnu

Načte první den v týdnu, který se zobrazí ve sloupci v kalendáři úplně vlevo.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Parametry

*pbLocal*<br/>
Ukazatel na hodnotu BOOL. Pokud je hodnota nenulová, nastavení ovládacího prvku se neshoduje s nastavením v Ovládacích panelech.

### <a name="return-value"></a>Návratová hodnota

Celočíselná hodnota, která představuje první den v týdnu. Další informace o tom, jaká celá čísla představuje, najdete v tématu **poznámky** .

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-getfirstdayofweek), jak je popsáno v Windows SDK. Dny v týdnu jsou reprezentovány jako celá čísla, a to následujícím způsobem.

|Value|Den v týdnu|
|-----------|---------------------|
|0|Pondělí|
|1|Úterý|
|2|Středa|
|3|Čtvrtek|
|4|Pátek|
|5|Sobota|
|6|Neděle|

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CMonthCalCtrl:: SetFirstDayOfWeek](#setfirstdayofweek).

##  <a name="getmaxselcount"></a>Atributu CMonthCalCtrl:: GetMaxSelCount

Načte aktuální maximální počet dní, které lze vybrat v ovládacím prvku měsíční kalendář.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celočíselná hodnota, která představuje celkový počet dní, které lze vybrat pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETMAXSELCOUNT](/windows/desktop/Controls/mcm-getmaxselcount), jak je popsáno v Windows SDK. Tuto členskou funkci použijte pro ovládací prvky se sadou stylů MCS_MULTISELECT.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CMonthCalCtrl:: SetMaxSelCount](#setmaxselcount).

##  <a name="getmaxtodaywidth"></a>Atributu CMonthCalCtrl:: GetMaxTodayWidth

Načte maximální šířku řetězce "Today" pro aktuální ovládací prvek měsíčního kalendáře.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka řetězce "Today" (v pixelech).

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která se používá k programovému přístupu k ovládacímu prvku měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `GetMaxTodayWidth` metodu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Poznámky

Uživatel se může vrátit k aktuálnímu datu kliknutím na řetězec "dnes", který se zobrazí v dolní části ovládacího prvku měsíční kalendář. Řetězec "Today" obsahuje text popisku a text data.

Tato metoda pošle zprávu [MCM_GETMAXTODAYWIDTH](/windows/desktop/Controls/mcm-getmaxtodaywidth) , která je popsána v Windows SDK.

##  <a name="getminreqrect"></a>Atributu CMonthCalCtrl:: GetMinReqRect

Načte minimální velikost nutnou k zobrazení celého měsíce v ovládacím prvku měsíční kalendář.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Parametry

*pRect*<br/>
Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která bude přijímat informace o ohraničujícím obdélníku. Tento parametr musí být platná adresa a nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu tato členská funkce vrátí nenulovou `lpRect` hodnotu a získá příslušné informace o vazbě. V případě neúspěchu vrátí členská funkce hodnotu 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETMINREQRECT](/windows/desktop/Controls/mcm-getminreqrect), jak je popsáno v Windows SDK.

##  <a name="getmonthdelta"></a>Atributu CMonthCalCtrl:: GetMonthDelta

Načte rychlost posunutí pro ovládací prvek měsíční kalendář.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Návratová hodnota

Frekvence posunutí ovládacího prvku měsíční kalendář Rychlost posunutí je počet měsíců, po které ovládací prvek přesune zobrazení, když uživatel klikne na tlačítko posuvníku jednou.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETMONTHDELTA](/windows/desktop/Controls/mcm-getmonthdelta), jak je popsáno v Windows SDK.

##  <a name="getmonthrange"></a>Atributu CMonthCalCtrl:: GetMonthRange

Načte informace o datu, které představují vysoké a nízké limity zobrazení ovládacího prvku měsíční kalendář.

```
int GetMonthRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    CTime& refMinRange,
    CTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange,
    DWORD dwFlags) const;
```

### <a name="parameters"></a>Parametry

*refMinRange*<br/>
Odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který obsahuje minimální povolený datum.

*refMaxRange*<br/>
Odkaz na `COleDateTime` objekt nebo `CTime` obsahující maximální povolené datum.

*pMinRange*<br/>
Ukazatel na strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) , která obsahuje datum na nejnižším konci rozsahu.

*pMaxRange*<br/>
Ukazatel na `SYSTEMTIME` strukturu, která obsahuje datum na nejvyšší straně rozsahu.

*dwFlags*<br/>
Hodnota určující rozsah omezení rozsahu, které mají být načteny. Tato hodnota musí být jedna z následujících hodnot:

|Value|Význam|
|-----------|-------------|
|GMR_DAYSTATE|Zahrne předchozí a koncové měsíce viditelného rozsahu, který je zobrazen pouze částečně.|
|GMR_VISIBLE|Zahrnutí pouze těch měsíců, které jsou zcela zobrazeny.|

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které představuje rozsah v měsících, rozložené dvěma omezeními, která jsou uvedena v *refMinRange* a *refMaxRange* v první a druhé verzi, nebo *pMinRange* a *pMaxRange* v třetí verzi.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETMONTHRANGE](/windows/desktop/Controls/mcm-getmonthrange), jak je popsáno v Windows SDK. V implementaci `GetMonthRange`knihovny MFC můžete určit `COleDateTime` použití, `CTime` použití nebo `SYSTEMTIME` strukturu použití.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CMonthCalCtrl:: SetDayState](#setdaystate).

##  <a name="getrange"></a>Atributu CMonthCalCtrl:: GetRange

Načte aktuální minimální a maximální kalendářní datum nastavené v ovládacím prvku měsíční kalendář.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;

DWORD GetRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Parametry

*pMinRange*<br/>
Ukazatel na `COleDateTime` objekt `CTime` , objekt nebo strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) obsahující datum na nejnižším konci rozsahu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objekt `CTime` , objekt nebo strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) , která obsahuje datum na nejvyšší straně rozsahu.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, která může být nulová (nejsou nastavena žádná omezení) nebo kombinace následujících hodnot, které určují informace o limitu.

|Value|Význam|
|-----------|-------------|
|GDTR_MAX|Pro ovládací prvek je nastaven maximální limit. *pMaxRange* je platný a obsahuje informace o příslušném datu.|
|GDTR_MIN|Pro ovládací prvek je nastaven minimální limit. *pMinRange* je platný a obsahuje informace o příslušném datu.|

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETRANGE](/windows/desktop/Controls/mcm-getrange), jak je popsáno v Windows SDK. V implementaci `GetRange`knihovny MFC můžete `COleDateTime` určit použití, `CTime` použití nebo `SYSTEMTIME` strukturu použití.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>Atributu CMonthCalCtrl:: GetSelRange

Načte informace o datu, které představují horní a dolní meze rozsahu dat aktuálně vybraného uživatelem.

```
BOOL GetSelRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange) const;

BOOL GetSelRange(
    CTime& refMinRange,
    CTime& refMaxRange) const;

BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Parametry

*refMinRange*<br/>
Odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který obsahuje minimální povolený datum.

*refMaxRange*<br/>
Odkaz na `COleDateTime` objekt nebo `CTime` obsahující maximální povolené datum.

*pMinRange*<br/>
Ukazatel na strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) , která obsahuje datum na nejnižším konci rozsahu.

*pMaxRange*<br/>
Ukazatel na `SYSTEMTIME` strukturu, která obsahuje datum na nejvyšší straně rozsahu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETSELRANGE](/windows/desktop/Controls/mcm-getselrange), jak je popsáno v Windows SDK. `GetSelRange`dojde k chybě při použití ovládacího prvku měsíční kalendář, který nepoužívá styl MCS_MULTISELECT.

V implementaci `GetSelRange`knihovny MFC můžete určit `COleDateTime` použití, `CTime` použití nebo `SYSTEMTIME` strukturu použití.

##  <a name="gettoday"></a>Atributu CMonthCalCtrl:: gettoday

Načte informace o datu pro ovládací prvek měsíční kalendář pro datum zadané jako dnešní.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který indikuje aktuální den.

*pDateTime*<br/>
Ukazatel na strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) , která bude dostávat informace o datu. Tento parametr musí být platná adresa a nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETTODAY](/windows/desktop/Controls/mcm-gettoday), jak je popsáno v Windows SDK. V implementaci `GetToday`knihovny MFC můžete `COleDateTime` určit použití, `CTime` použití nebo `SYSTEMTIME` strukturu použití.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>Atributu CMonthCalCtrl:: HitTest

Určuje, který ovládací prvek měsíčního kalendáře (pokud existuje) je na zadané pozici.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Parametry

*pMCHitTest*<br/>
Ukazatel na strukturu [MCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-mchittestinfo) obsahující body testování přístupů pro ovládací prvek měsíční kalendář.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD. Je rovno **uHit** členu `MCHITTESTINFO` struktury.

### <a name="remarks"></a>Poznámky

`HitTest``MCHITTESTINFO` používá strukturu, která obsahuje informace o testu přístupů.

##  <a name="iscenturyview"></a>Atributu CMonthCalCtrl:: IsCenturyView

Označuje, zda je aktuální zobrazení ovládacího prvku měsíční kalendář aktuálního kalendáře v zobrazení století.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud aktuální zobrazení je zobrazení století; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , která je popsána v Windows SDK. Pokud tato zpráva vrátí MCMV_CENTURY, vrátí tato metoda hodnotu TRUE.

##  <a name="isdecadeview"></a>Atributu CMonthCalCtrl:: IsDecadeView

Označuje, zda aktuální zobrazení aktuálního ovládacího prvku měsíční kalendář představuje zobrazení dekády.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud aktuální zobrazení je zobrazení dekády; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , která je popsána v Windows SDK. Pokud tato zpráva vrátí MCMV_DECADE, vrátí tato metoda hodnotu TRUE.

##  <a name="ismonthview"></a>Atributu CMonthCalCtrl:: IsMonthView

Určuje, zda aktuální zobrazení aktuálního ovládacího prvku měsíční kalendář odpovídá zobrazení měsíce.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud aktuální zobrazení je měsíc. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , která je popsána v Windows SDK. Pokud tato zpráva vrátí MCMV_MONTH, vrátí tato metoda hodnotu TRUE.

##  <a name="isyearview"></a>Atributu CMonthCalCtrl:: IsYearView

Označuje, zda aktuální zobrazení aktuálního ovládacího prvku měsíční kalendář odpovídá zobrazení roku.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud aktuální zobrazení je zobrazení rok; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , která je popsána v Windows SDK. Pokud tato zpráva vrátí MCMV_YEAR, vrátí tato metoda hodnotu TRUE.

##  <a name="setcalendarborder"></a>Atributu CMonthCalCtrl:: SetCalendarBorder

Nastaví šířku ohraničení aktuálního ovládacího prvku měsíční kalendář.

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*cxyBorder*|pro Šířka ohraničení v pixelech|

### <a name="remarks"></a>Poznámky

Pokud je tato metoda úspěšná, Šířka ohraničení je nastavená na parametr *cxyBorder* . V opačném případě se šířka ohraničení obnoví na výchozí hodnotu, která je určena aktuálním [motivem](/windows/desktop/Controls/visual-styles-overview), nebo nula, pokud motivy nejsou použity.

Tato metoda pošle zprávu [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která se používá k programovému přístupu k ovládacímu prvku měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví šířku ohraničení ovládacího prvku měsíční kalendář na osm pixelů. K určení, zda byla tato metoda úspěšná, použijte metodu [atributu CMonthCalCtrl:: GetCalendarBorder](#getcalendarborder) .

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>Atributu CMonthCalCtrl:: SetCalendarBorderDefault

Nastaví výchozí šířku ohraničení aktuálního ovládacího prvku měsíční kalendář.

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Poznámky

Šířka ohraničení je nastavena na výchozí hodnotu určenou aktuálním motivem nebo nula [](/windows/desktop/Controls/visual-styles-overview), pokud nejsou použity motivy.

Tato metoda pošle zprávu [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder) , která je popsána v Windows SDK.

##  <a name="setcalid"></a>Atributu CMonthCalCtrl:: SetCalID

Nastaví identifikátor kalendáře pro ovládací prvek aktuálního měsíčního kalendáře.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*calid*|pro Jedna z konstant [identifikátoru kalendáře](/windows/desktop/Intl/calendar-identifiers) .|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Identifikátor kalendáře určuje kalendář specifický pro oblast, jako je například gregoriánský (lokalizovaný), japonské nebo hidžra kalendáře. Použijte metodu k zobrazení kalendáře zadaného parametrem CALID, pokud je národní prostředí obsahující kalendář nainstalované v počítači. `SetCalID`

Tato metoda pošle zprávu [MCM_SETCALID](/windows/desktop/Controls/mcm-setcalid) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která se používá k programovému přístupu k ovládacímu prvku měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví ovládací prvek měsíční kalendář k zobrazení japonského kalendáře císaře období. Metoda `SetCalID` bude úspěšná pouze v případě, že je tento kalendář nainstalován v počítači.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>Atributu CMonthCalCtrl:: SetCenturyView

Nastaví ovládací prvek aktuálního měsíčního kalendáře pro zobrazení století.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá metodu [atributu CMonthCalCtrl:: SetCurrentView](#setcurrentview) k nastavení zobrazení na `MCMV_CENTURY`, které představuje zobrazení století.

##  <a name="setcolor"></a>Atributu CMonthCalCtrl:: SetColor

Nastaví barvu zadané oblasti ovládacího prvku měsíční kalendář.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Parametry

*nRegion*<br/>
Celočíselná hodnota určující, která barva měsíčního kalendáře se má nastavit. Tato hodnota může být jedna z následujících.

|Value|Význam|
|-----------|-------------|
|MCSC_BACKGROUND|Barva pozadí zobrazená mezi měsíci|
|MCSC_MONTHBK|Barva pozadí zobrazená v rámci měsíce.|
|MCSC_TEXT|Barva použitá k zobrazení textu v rámci měsíce.|
|MCSC_TITLEBK|Barva pozadí zobrazená v nadpisu kalendáře.|
|MCSC_TITLETEXT|Barva použitá k zobrazení textu v nadpisu kalendáře|
|MCSC_TRAILINGTEXT|Barva použitá k zobrazení záhlaví a koncového textu. Záhlaví a koncové dny jsou dny z předchozích a následujících měsíců, které se zobrazí v aktuálním kalendáři.|

*ref*<br/>
Hodnota COLORREF pro nové nastavení barvy pro zadanou část ovládacího prvku měsíční kalendář.

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF, která představuje předchozí nastavení barvy pro zadanou část ovládacího prvku měsíční kalendář, pokud je úspěšná. V opačném případě se tato zpráva vrátí na hodnotu-1.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETCOLOR](/windows/desktop/Controls/mcm-setcolor), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>Atributu CMonthCalCtrl:: SetCurrentView

Nastaví ovládací prvek aktuálního měsíčního kalendáře pro zobrazení zadaného zobrazení.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwNewView*|pro Jedna z následujících hodnot, které určují měsíční, roční, dekáda nebo zobrazení století.<br /><br /> MCMV_MONTH: Měsíční zobrazení<br /><br /> MCMV_YEAR: Roční zobrazení<br /><br /> MCMV_DECADE: Zobrazení dekády<br /><br /> MCMV_CENTURY: Zobrazení století|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [MCM_SETCURRENTVIEW](/windows/desktop/Controls/mcm-setcurrentview) , která je popsána v Windows SDK.

##  <a name="setcursel"></a>Atributu CMonthCalCtrl:: SetCurSel

Nastaví aktuálně vybrané datum pro ovládací prvek měsíční kalendář.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který označuje aktuálně vybraný ovládací prvek měsíčního kalendáře.

*pDateTime*<br/>
Ukazatel na strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) , která obsahuje datum, které se má nastavit jako aktuální výběr.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETCURSEL](/windows/desktop/Controls/mcm-setcursel), jak je popsáno v Windows SDK. V implementaci `SetCurSel`knihovny MFC můžete `COleDateTime` určit použití, `CTime` použití nebo `SYSTEMTIME` strukturu použití.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>Atributu CMonthCalCtrl:: SetDayState

Nastaví zobrazení pro dny v ovládacím prvku měsíční kalendář.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Parametry

*nMonths*<br/>
Hodnota označující, kolik prvků je v poli, na které odkazuje *pStates* .

*pStates*<br/>
Ukazatel na [MONTHDAYSTATE](/windows/desktop/Controls/monthdaystate) pole hodnot, které definují, jak bude ovládací prvek měsíční kalendář vykreslovat každý den v zobrazení. Datový typ MONTHDAYSTATE je bitové pole, kde každý bit (1 až 31) představuje stav dne v měsíci. Pokud je bit zapnutý, zobrazí se odpovídající den tučně. v opačném případě se zobrazí bez zdůraznění.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETDAYSTATE](/windows/desktop/Controls/mcm-setdaystate), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>Atributu CMonthCalCtrl:: SetDecadeView

Nastaví ovládací prvek aktuálního měsíčního kalendáře na zobrazení dekády.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pomocí metody [atributu CMonthCalCtrl:: SetCurrentView](#setcurrentview) nastaví zobrazení na `MCMV_DECADE`hodnotu, která představuje zobrazení dekády.

##  <a name="setfirstdayofweek"></a>Atributu CMonthCalCtrl:: SetFirstDayOfWeek

Nastaví den v týdnu, který se má zobrazit v levém sloupci kalendáře.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Parametry

*iDay*<br/>
Celočíselná hodnota představující, který den má být nastaven jako první den v týdnu. Tato hodnota musí být jedno z čísel dnů. Popis [](#getfirstdayofweek) čísel dnů najdete v tématu getprvní_den_v_týdnu.

*lpnOld*<br/>
Ukazatel na celé číslo označující první den v týdnu, který jste dříve nastavili.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je předchozí první den v týdnu nastavený na jinou hodnotu než LOCALE_IFIRSTDAYOFWEEK, což je den uvedený v nastavení ovládacích panelů. V opačném případě tato funkce vrátí 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-setfirstdayofweek), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>Atributu CMonthCalCtrl:: SetMaxSelCount

Nastaví maximální počet dní, které lze vybrat v ovládacím prvku měsíční kalendář.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Parametry

*Nmaximum*<br/>
Hodnota, která bude nastavena pro reprezentaci maximálního počtu vybraných dnů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETMAXSELCOUNT](/windows/desktop/Controls/mcm-setmaxselcount), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>Atributu CMonthCalCtrl:: SetMonthDelta

Nastaví rychlost posunutí pro ovládací prvek měsíční kalendář.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Parametry

*iDelta*<br/>
Počet měsíců, které mají být nastaveny jako posunutí ovládacího prvku Pokud je tato hodnota nula, bude rozdíl v měsíci obnoven na výchozí hodnotu, což je počet měsíců zobrazených v ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Předchozí rychlost posunutí. Pokud se frekvence posunutí dřív nestavila, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETMONTHDELTA](/windows/desktop/Controls/mcm-setmonthdelta), jak je popsáno v Windows SDK.

##  <a name="setmonthview"></a>Atributu CMonthCalCtrl:: SetMonthView

Nastaví ovládací prvek aktuálního měsíčního kalendáře k zobrazení měsíce.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá metodu [atributu CMonthCalCtrl:: SetCurrentView](#setcurrentview) k nastavení zobrazení na MCMV_MONTH, které představuje zobrazení měsíc.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která se používá k programovému přístupu k ovládacímu prvku měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví ovládací prvek měsíční kalendář k zobrazení zobrazení měsíc, rok, dekáda a století.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>Atributu CMonthCalCtrl:: SetRange

Nastaví minimální a maximální povolená data pro ovládací prvek měsíční kalendář.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);

BOOL SetRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Parametry

*pMinRange*<br/>
Ukazatel na `COleDateTime` objekt `CTime` , objekt nebo strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) obsahující datum na nejnižším konci rozsahu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objekt `CTime` , objekt nebo `SYSTEMTIME` strukturu obsahující datum na nejvyšší straně rozsahu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETRANGE](/windows/desktop/Controls/mcm-setrange), jak je popsáno v Windows SDK. V implementaci `SetRange`knihovny MFC můžete určit `COleDateTime` použití, `CTime` použití nebo `SYSTEMTIME` strukturu použití.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CMonthCalCtrl:: GetRange](#getrange).

##  <a name="setselrange"></a>Atributu CMonthCalCtrl:: SetSelRange

Nastaví výběr pro ovládací prvek měsíčního kalendáře na daný rozsah kalendářních dat.

```
BOOL SetSelRange(
    const COleDateTime& pMinRange,
    const COleDateTime& pMaxRange);

BOOL SetSelRange(
    const CTime& pMinRange,
    const CTime& pMaxRange);

BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Parametry

*pMinRange*<br/>
Ukazatel na `COleDateTime` objekt `CTime` , objekt nebo strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) obsahující datum na nejnižším konci rozsahu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objekt `CTime` , objekt nebo `SYSTEMTIME` strukturu obsahující datum na nejvyšší straně rozsahu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETSELRANGE](/windows/desktop/Controls/mcm-setselrange), jak je popsáno v Windows SDK. V implementaci `SetSelRange`knihovny MFC můžete určit `COleDateTime` použití, `CTime` použití nebo `SYSTEMTIME` strukturu použití.

##  <a name="settoday"></a>Atributu CMonthCalCtrl:: SetToday

Nastaví ovládací prvek Kalendář pro aktuální den.

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , který obsahuje aktuální datum.

*pDateTime*<br/>
Ve druhé verzi je ukazatel na objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) obsahující aktuální informace o datu. Třetí verze, ukazatel na strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) , která obsahuje informace o aktuálním datu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETTODAY](/windows/desktop/Controls/mcm-settoday), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CMonthCalCtrl:: gettoday](#gettoday).

##  <a name="setyearview"></a>Atributu CMonthCalCtrl:: SetYearView

Nastaví aktuální měsíční ovládací prvek kalendářního kalendáře na zobrazení roků.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá metodu [atributu CMonthCalCtrl:: SetCurrentView](#setcurrentview) k nastavení zobrazení na MCMV_YEAR, které představuje roční zobrazení.

##  <a name="sizeminreq"></a>Atributu CMonthCalCtrl:: SizeMinReq

Zobrazí ovládací prvek měsíční kalendář na minimální velikost, která zobrazuje jeden měsíc.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Parametry

*bRepaint*<br/>
Určuje, zda má být ovládací prvek překreslen. Ve výchozím nastavení má hodnotu TRUE. Pokud je hodnota FALSE, nebude provedena žádná remalování.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud má ovládací prvek měsíční kalendář velikost na minimum; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Při `SizeMinReq` volání se úspěšně zobrazí celý ovládací prvek měsíční kalendář pro kalendář na jeden měsíc.

##  <a name="sizerecttomin"></a>Atributu CMonthCalCtrl:: SizeRectToMin

Pro ovládací prvek aktuálního měsíčního kalendáře vypočítá nejmenší obdélník, který může obsahovat všechny kalendáře, které odpovídají zadanému obdélníku.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpRect*|pro Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) definující obdélník, který obsahuje požadovaný počet kalendářů.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) definující obdélník, jehož velikost je menší nebo rovna obdélníku definovanému parametrem *lpRect* .

### <a name="remarks"></a>Poznámky

Tato metoda vypočítá, kolik kalendářů se může vejít do obdélníku určeného parametrem *lpRect* , a vrátí nejmenší obdélník, který může obsahovat daný počet kalendářů. V důsledku toho tato metoda zmenší zadaný obdélník tak, aby přesně vyhovoval požadovanému počtu kalendářů.

Tato metoda pošle zprávu [MCM_SIZERECTTOMIN](/windows/desktop/Controls/mcm-sizerecttomin) , která je popsána v Windows SDK.

## <a name="see-also"></a>Viz také:

[CMNCTRL1 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl – třída](../../mfc/reference/cdatetimectrl-class.md)
