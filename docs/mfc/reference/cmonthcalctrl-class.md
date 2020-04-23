---
title: Třída CMonthCalCtrl
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
ms.openlocfilehash: 8c24c638d7006be112a53ec1e4f622ad528e348c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752816"
---
# <a name="cmonthcalctrl-class"></a>Třída CMonthCalCtrl

Zapouzdřuje funkce ovládacího prvku měsíčního kalendáře.

## <a name="syntax"></a>Syntaxe

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Vytvoří `CMonthCalCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMonthCalCtrl::Vytvořit](#create)|Vytvoří ovládací prvek měsíčního kalendáře `CMonthCalCtrl` a připojí jej k objektu.|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Načte šířku ohraničení ovládacího prvku kalendáře aktuálního měsíce.|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Načte počet kalendářů zobrazených v ovládacím prvku kalendáře aktuálního měsíce.|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Načte informace o aktuálním ovládacím prvku kalendáře měsíce.|
|[CMonthCalCtrl::Getcalid](#getcalid)|Načte identifikátor kalendáře pro ovládací prvek kalendáře aktuálního měsíce.|
|[CMonthCalCtrl::GetColor](#getcolor)|Získá barvu zadané oblasti ovládacího prvku kalendář měsíce.|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Načte zobrazení, které je aktuálně zobrazeno ovládacím prvkem kalendáře aktuálního měsíce.|
|[CMonthCalCtrl::GetCurSel](#getcursel)|Načte systémový čas podle aktuálně vybraného data.|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Získá první den v týdnu, které mají být zobrazeny v levém sloupci kalendáře.|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Načte aktuální maximální počet dní, které lze vybrat v ovládacím prvku kalendář měsíce.|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Načte maximální šířku řetězce "Dnes" pro ovládací prvek kalendáře aktuálního měsíce.|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Načte minimální velikost potřebnou k zobrazení celého měsíce v ovládacím prvku kalendáře měsíce.|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Načte rychlost posouvání pro ovládací prvek měsíčního kalendáře.|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Načte informace o datu představující vysoké a nízké limity zobrazení ovládacího prvku kalendáře měsíce.|
|[CMonthCalCtrl::GetRange](#getrange)|Načte aktuální minimální a maximální data nastavená v ovládacím prvku kalendáře měsíce.|
|[CMonthCalCtrl::GetSelRange](#getselrange)|Načte informace o datu představující horní a dolní hranice rozsahu dat aktuálně vybraného uživatelem.|
|[CMonthCalCtrl::GetToday](#gettoday)|Načte informace o datu zadaném jako "dnes" pro ovládací prvek kalendáře měsíce.|
|[CMonthCalCtrl::HitTest](#hittest)|Určuje, která část ovládacího prvku měsíčního kalendáře je v daném bodě na obrazovce.|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Označuje, zda je aktuální zobrazení ovládacího prvku kalendáře aktuálního měsíce zobrazením století.|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Označuje, zda je aktuální zobrazení ovládacího prvku kalendáře aktuálního měsíce zobrazením desetiletí.|
|[CMonthCalCtrl::Zobrazení IsMonthView](#ismonthview)|Označuje, zda je aktuální zobrazení ovládacího prvku kalendáře aktuálního měsíce zobrazením měsíce.|
|[CMonthCalCtrl::Zobrazení IsYearView](#isyearview)|Označuje, zda je aktuální zobrazení ovládacího prvku kalendáře aktuálního měsíce zobrazením roku.|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Nastaví šířku ohraničení ovládacího prvku kalendáře aktuálního měsíce.|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Nastaví výchozí šířku ohraničení ovládacího prvku kalendáře aktuálního měsíce.|
|[CMonthCalCtrl::SetCalID](#setcalid)|Nastaví identifikátor kalendáře pro ovládací prvek kalendáře aktuálního měsíce.|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Nastaví ovládací prvek kalendáře aktuálního měsíce tak, aby zobrazoval zobrazení století.|
|[CMonthCalCtrl::SetColor](#setcolor)|Nastaví barvu zadané oblasti ovládacího prvku měsíčního kalendáře.|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Nastaví ovládací prvek kalendáře aktuálního měsíce tak, aby zobrazoval zadané zobrazení.|
|[CMonthCalCtrl::SetCurSel](#setcursel)|Nastaví aktuálně vybrané datum pro ovládací prvek měsíčního kalendáře.|
|[CMonthCalCtrl::SetDayState](#setdaystate)|Nastaví zobrazení na dny v ovládacím prvku kalendáře měsíce.|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Nastaví aktuální ovládací prvek kalendáře měsíce na zobrazení desetiletí.|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Nastaví den v týdnu, který se má zobrazit v levém sloupci kalendáře.|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Nastaví maximální počet dní, které lze vybrat v ovládacím prvku měsíčního kalendáře.|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Nastaví rychlost posouvání pro ovládací prvek měsíčního kalendáře.|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Nastaví ovládací prvek kalendáře aktuálního měsíce tak, aby zobrazoval zobrazení měsíce.|
|[CMonthCalCtrl::SetRange](#setrange)|Nastaví minimální a maximální povolená data pro ovládací prvek měsíčního kalendáře.|
|[CMonthCalCtrl::SetSelRange](#setselrange)|Nastaví výběr pro ovládací prvek měsíčního kalendáře na dané časové období.|
|[CMonthCalCtrl::SetToday](#settoday)|Nastaví ovládací prvek kalendáře pro aktuální den.|
|[CMonthCalCtrl::SetYearView](#setyearview)|Nastaví zobrazení aktuálního měsíčního kalendáře na rok.|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Překreslí ovládací prvek měsíčního kalendáře na minimální velikost jednoho měsíce.|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Pro ovládací prvek kalendáře aktuální měsíc vypočítá nejmenší obdélník, který může obsahovat všechny kalendáře, které se vejdou do zadaného obdélníku.|

## <a name="remarks"></a>Poznámky

Ovládací prvek měsíční kalendář poskytuje uživateli jednoduché rozhraní kalendáře, ze kterého může uživatel vybrat datum. Uživatel může změnit zobrazení takto:

- Posouvání dopředu a dozadu, z měsíce na měsíc.

- Kliknutím na text Dnes zobrazíte aktuální den (pokud není použit MCS_NOTODAY styl).

- Vybírám měsíc nebo rok z rozbalovacího menu.

Ovládací prvek měsíčního kalendáře můžete přizpůsobit použitím různých stylů na objekt při jeho vytváření. Tyto styly jsou popsány v [styly ovládacího prvku kalendář měsíce](/windows/win32/Controls/month-calendar-control-styles) v sadě Windows SDK.

Ovládací prvek kalendář měsíce může zobrazit více než jeden měsíc a může označovat zvláštní dny (například svátky) tučným písmem datum.

Další informace o použití ovládacího prvku kalendář měsíce naleznete v [tématu Použití CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdtctl.h

## <a name="cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a>CMonthCalCtrl::CMonthCalCtrl

Vytvoří `CMonthCalCtrl` objekt.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Poznámky

Musíte volat `Create` po vytvoření objektu.

## <a name="cmonthcalctrlcreate"></a><a name="create"></a>CMonthCalCtrl::Vytvořit

Vytvoří ovládací prvek měsíčního kalendáře `CMonthCalCtrl` a připojí jej k objektu.

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

*dwStyl*<br/>
Určuje kombinaci stylů systému Windows aplikovaných na ovládací prvek měsíčního kalendáře. Další informace o stylech naleznete v části [Styly ovládacího prvku Kalendář](/windows/win32/Controls/month-calendar-control-styles) měsíců v sadě Windows SDK.

*Rect*<br/>
Odkaz na strukturu [RECT.](/windows/win32/api/windef/ns-windef-rect) Obsahuje pozici a velikost ovládacího prvku kalendář měsíce.

*Pt*<br/>
Odkaz na [point](/windows/win32/api/windef/ns-windef-point) strukturu, která identifikuje umístění ovládacího prvku kalendář měsíce.

*pParentWnd*<br/>
Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku kalendář měsíce. Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku ovládacího prvku měsíčního kalendáře.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Vytvořte ovládací prvek měsíčního kalendáře ve dvou krocích:

1. Volání [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) k `CMonthCalCtrl` vytvoření objektu.

1. Volání této členské funkce, která vytvoří ovládací prvek `CMonthCalCtrl` kalendář měsíce a připojí jej k objektu.

Při volání `Create`jsou inicializovány běžné ovládací prvky. Verze `Create` volání určuje, jak je velikost:

- Chcete-li, aby knihovna MFC automaticky zvětšila ovládací prvek na jeden měsíc, zavolejte přepsání, které používá parametr *pt.*

- Chcete-li velikost ovládacího prvku sami, zavolejte přepsání této funkce, která používá parametr *rect.*

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

## <a name="cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a>CMonthCalCtrl::GetCalendarBorder

Načte šířku ohraničení ovládacího prvku kalendáře aktuálního měsíce.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka ohraničení ovládacího prvku v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu MCM_GETCALENDARBORDER,](/windows/win32/Controls/mcm-getcalendarborder) která je popsána v sadě Windows SDK.

## <a name="cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a>CMonthCalCtrl::GetCalendarCount

Načte počet kalendářů zobrazených v ovládacím prvku kalendáře aktuálního měsíce.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet kalendářů aktuálně zobrazených v ovládacím prvku kalendář měsíce. Maximální povolený počet kalendářů je 12.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu MCM_GETCALENDARCOUNT,](/windows/win32/Controls/mcm-getcalendarcount) která je popsána v sadě Windows SDK.

## <a name="cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a>CMonthCalCtrl::GetCalendarGridInfo

Načte informace o aktuálním ovládacím prvku kalendáře měsíce.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pmcGridInfo*|[out] Ukazatel na strukturu [MCGRIDINFO,](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo) která přijímá informace o aktuálním ovládacím prvku kalendáře měsíce. Volající je zodpovědný za přidělení a inicializaci této struktury.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu MCM_GETCALENDARGRIDINFO,](/windows/win32/Controls/mcm-getcalendargridinfo) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_monthCalCtrl`která se používá k programovému přístupu k ovládacímu prvku měsíčního kalendáře. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu `GetCalendarGridInfo` používá metodu k načtení kalendářního data, které zobrazuje ovládací prvek kalendáře aktuálního měsíce.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

## <a name="cmonthcalctrlgetcalid"></a><a name="getcalid"></a>CMonthCalCtrl::Getcalid

Načte identifikátor kalendáře pro ovládací prvek kalendáře aktuálního měsíce.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedna z konstant [identifikátorů kalendáře.](/windows/win32/Intl/calendar-identifiers)

### <a name="remarks"></a>Poznámky

Identifikátor kalendáře označuje kalendář specifický pro oblast, například gregoriánský (lokalizovaný), japonský nebo hidžra kalendář. Aplikace může používat identifikátor kalendáře, který má různé funkce podpory jazyků.

Tato metoda odešle [zprávu MCM_GETCALID,](/windows/win32/Controls/mcm-getcalid) která je popsána v sadě Windows SDK.

## <a name="cmonthcalctrlgetcolor"></a><a name="getcolor"></a>CMonthCalCtrl::GetColor

Načte barvu oblasti ovládacího prvku kalendáře měsíce *určeného nRegion*.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Parametry

*nRegion*<br/>
Oblast ovládacího prvku kalendáře měsíce, ze kterého je načtena barva. Seznam hodnot naleznete v parametru *nRegion* [v parametru SetColor](#setcolor).

### <a name="return-value"></a>Návratová hodnota

[ColorREF](/windows/win32/gdi/colorref) hodnota určující barvu přidruženou k části ovládacího prvku kalendáře měsíce, pokud je úspěšná. V opačném případě vrátí tato členská funkce -1.

## <a name="cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a>CMonthCalCtrl::GetCurrentView

Načte zobrazení, které je aktuálně zobrazeno ovládacím prvkem kalendáře aktuálního měsíce.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zobrazení, které je označeno jednou z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|MCMV_MONTH|Měsíční zobrazení|
|MCMV_YEAR|Roční pohled|
|MCMV_DECADE|Desetiletý pohled|
|MCMV_CENTURY|Století pohled|

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_monthCalCtrl`která se používá k programovému přístupu k ovládacímu prvku měsíčního kalendáře. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu hlásí, které aktuálně zobrazují ovládací prvek měsíčního kalendáře.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

## <a name="cmonthcalctrlgetcursel"></a><a name="getcursel"></a>CMonthCalCtrl::GetCurSel

Načte systémový čas podle aktuálně vybraného data.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt u cTime nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu. Přijme aktuální čas.

*čas data*<br/>
Ukazatel na strukturu [SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) která obdrží aktuálně vybrané informace o datu. Tento parametr musí být platnou adresou a nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; otherwize 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/mcm-getcursel)Win32 MCM_GETCURSEL , jak je popsáno v sadě Windows SDK.

> [!NOTE]
> Tato členská funkce se nezdaří, pokud je nastaven a MCS_MULTISELECT stylu.

V implementaci `GetCurSel`knihovny MFC můžete `COleDateTime` určit využití, `CTime` použití `SYSTEMTIME` nebo využití struktury.

## <a name="cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a>CMonthCalCtrl::GetFirstDayOfWeek

Získá první den v týdnu, které mají být zobrazeny v levém sloupci kalendáře.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Parametry

*pbMístní*<br/>
Ukazatel na hodnotu BOOL. Pokud je hodnota nenulová, nastavení ovládacího prvku neodpovídá nastavení v ovládacím panelu.

### <a name="return-value"></a>Návratová hodnota

Celá hodnota, která představuje první den v týdnu. Další informace o tom, co tato celá čísla představují, naleznete v **tématu Poznámky.**

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek)zprávy Win32 , jak je popsáno v sadě Windows SDK. Dny v týdnu jsou reprezentovány jako celá čísla, takto.

|Hodnota|Den v týdnu|
|-----------|---------------------|
|0|Monday|
|1|Úterý|
|2|Středa|
|3|Čtvrtek|
|4|Pátek|
|5|Sobota|
|6|Neděle|

### <a name="example"></a>Příklad

  Viz příklad [cMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek).

## <a name="cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a>CMonthCalCtrl::GetMaxSelCount

Načte aktuální maximální počet dní, které lze vybrat v ovládacím prvku kalendář měsíce.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celá hodnota představující celkový počet dní, které lze vybrat pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount)zprávy Win32 , jak je popsáno v sadě Windows SDK. Tuto členskou funkci použijte pro ovládací prvky se sadou MCS_MULTISELECT stylu.

### <a name="example"></a>Příklad

  Viz příklad [cMonthCalCtrl::SetMaxSelCount](#setmaxselcount).

## <a name="cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a>CMonthCalCtrl::GetMaxTodayWidth

Načte maximální šířku řetězce "Dnes" pro ovládací prvek kalendáře aktuálního měsíce.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka řetězce "Dnes" v pixelech.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_monthCalCtrl`která se používá k programovému přístupu k ovládacímu prvku měsíčního kalendáře. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `GetMaxTodayWidth` metodu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Poznámky

Uživatel se může vrátit k aktuálnímu datu kliknutím na řetězec "Dnes", který se zobrazí v dolní části ovládacího prvku kalendáře měsíce. Řetězec "Dnes" obsahuje text popisku a text data.

Tato metoda odešle [zprávu MCM_GETMAXTODAYWIDTH,](/windows/win32/Controls/mcm-getmaxtodaywidth) která je popsána v sadě Windows SDK.

## <a name="cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a>CMonthCalCtrl::GetMinReqRect

Načte minimální velikost potřebnou k zobrazení celého měsíce v ovládacím prvku kalendáře měsíce.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Parametry

*pRect*<br/>
Ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu, která obdrží informace ohraničující obdélník. Tento parametr musí být platnou adresou a nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, tato `lpRect` členská funkce vrátí nenulovou hodnotu a obdrží příslušné ohraničující informace. Pokud není úspěšná, vrátí členská funkce 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/mcm-getminreqrect)Win32 MCM_GETMINREQRECT , jak je popsáno v sadě Windows SDK.

## <a name="cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a>CMonthCalCtrl::GetMonthDelta

Načte rychlost posouvání pro ovládací prvek měsíčního kalendáře.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Návratová hodnota

Rychlost posouvání pro ovládací prvek kalendář měsíce. Rychlost posouvání je počet měsíců, po které ovládací prvek přesune zobrazení, když uživatel jednou klepne na tlačítko pro posouvání.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a>CMonthCalCtrl::GetMonthRange

Načte informace o datu představující vysoké a nízké limity zobrazení ovládacího prvku kalendáře měsíce.

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
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující minimální datum povoleno.

*refMaxRange*<br/>
Odkaz na `COleDateTime` objekt `CTime` nebo objekt obsahující maximální povolené datum.

*pMinRange*<br/>
Ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu obsahující datum na nejnižší konec rozsahu.

*pMaxRange*<br/>
Ukazatel na `SYSTEMTIME` strukturu obsahující datum na nejvyšším konci rozsahu.

*dwFlags*<br/>
Hodnota určující rozsah omezení rozsahu, které mají být načteny. Tato hodnota musí být jedna z následujících.

|Hodnota|Význam|
|-----------|-------------|
|GMR_DAYSTATE|Zahrnout předchozí a koncové měsíce viditelného rozsahu, které jsou zobrazeny pouze částečně.|
|GMR_VISIBLE|Zahrňte pouze ty měsíce, které jsou zcela zobrazeny.|

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které představuje rozsah v měsících, rozložené dvěma limity označenými *refMinRange* a *refMaxRange* v první a druhé verzi nebo *pMinRange* a *pMaxRange* ve třetí verzi.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange)zprávy Win32 , jak je popsáno v sadě Windows SDK. V `GetMonthRange`implementaci knihovny MFC můžete `COleDateTime` určit `CTime` využití, využití `SYSTEMTIME` nebo využití struktury.

### <a name="example"></a>Příklad

  Viz příklad [cmonthcalctrl::SetDayState](#setdaystate).

## <a name="cmonthcalctrlgetrange"></a><a name="getrange"></a>CMonthCalCtrl::GetRange

Načte aktuální minimální a maximální data nastavená v ovládacím prvku kalendáře měsíce.

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
Ukazatel na `COleDateTime` objekt, `CTime` objekt nebo [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu obsahující datum na nejnižším konci rozsahu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objekt, `CTime` objekt nebo [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu obsahující datum na nejvyšším konci rozsahu.

### <a name="return-value"></a>Návratová hodnota

DWORD, který může být nula (jsou nastaveny žádné limity) nebo kombinace následujících hodnot, které určují informace o omezení.

|Hodnota|Význam|
|-----------|-------------|
|GDTR_MAX|Pro ovládací prvek je nastaven maximální limit. *pMaxRange* je platný a obsahuje příslušné informace o datu.|
|GDTR_MIN|Pro ovládací prvek je nastaven minimální limit. *pMinRange* je platný a obsahuje příslušné informace o datu.|

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/mcm-getrange)Win32 MCM_GETRANGE , jak je popsáno v sadě Windows SDK. V implementaci `GetRange`knihovny MFC můžete `COleDateTime` určit využití, `CTime` použití `SYSTEMTIME` nebo využití struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

## <a name="cmonthcalctrlgetselrange"></a><a name="getselrange"></a>CMonthCalCtrl::GetSelRange

Načte informace o datu představující horní a dolní hranice rozsahu dat aktuálně vybraného uživatelem.

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
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující minimální datum povoleno.

*refMaxRange*<br/>
Odkaz na `COleDateTime` objekt `CTime` nebo objekt obsahující maximální povolené datum.

*pMinRange*<br/>
Ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu obsahující datum na nejnižší konec rozsahu.

*pMaxRange*<br/>
Ukazatel na `SYSTEMTIME` strukturu obsahující datum na nejvyšším konci rozsahu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange)zprávy Win32 , jak je popsáno v sadě Windows SDK. `GetSelRange`se nezdaří, pokud se použije na ovládací prvek měsíčního kalendáře, který nepoužívá styl MCS_MULTISELECT.

V `GetSelRange`implementaci knihovny MFC můžete `COleDateTime` určit `CTime` využití, využití `SYSTEMTIME` nebo využití struktury.

## <a name="cmonthcalctrlgettoday"></a><a name="gettoday"></a>CMonthCalCtrl::GetToday

Načte informace o datu zadaném jako "dnes" pro ovládací prvek kalendáře měsíce.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt označující aktuální den.

*čas data*<br/>
Ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu, která obdrží informace o datu. Tento parametr musí být platnou adresou a nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday)zprávy Win32 , jak je popsáno v sadě Windows SDK. V implementaci `GetToday`knihovny MFC můžete `COleDateTime` určit využití, `CTime` použití `SYSTEMTIME` nebo využití struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

## <a name="cmonthcalctrlhittest"></a><a name="hittest"></a>CMonthCalCtrl::HitTest

Určuje, který ovládací prvek kalendáře měsíce, pokud existuje, je na zadané pozici.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Parametry

*pMCHitTest*<br/>
Ukazatel na strukturu [MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo) obsahující body testování přístupů pro ovládací prvek kalendář měsíce.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD. Rovná se **uHit** člen `MCHITTESTINFO` struktury.

### <a name="remarks"></a>Poznámky

`HitTest`používá `MCHITTESTINFO` strukturu, která obsahuje informace o testu přístupů.

## <a name="cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a>CMonthCalCtrl::IsCenturyView

Označuje, zda je aktuální zobrazení ovládacího prvku kalendáře aktuálního měsíce zobrazením století.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je aktuální zobrazení zobrazení století; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) která je popsána v sadě Windows SDK. Pokud tato zpráva vrátí MCMV_CENTURY, tato metoda vrátí hodnotu TRUE.

## <a name="cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a>CMonthCalCtrl::IsDecadeView

Označuje, zda je aktuální zobrazení ovládacího prvku kalendáře aktuálního měsíce zobrazením desetiletí.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je aktuální zobrazení zobrazení desetiletí; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) která je popsána v sadě Windows SDK. Pokud tato zpráva vrátí MCMV_DECADE, tato metoda vrátí hodnotu TRUE.

## <a name="cmonthcalctrlismonthview"></a><a name="ismonthview"></a>CMonthCalCtrl::Zobrazení IsMonthView

Označuje, zda je aktuální zobrazení ovládacího prvku kalendáře aktuálního měsíce zobrazením měsíce.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je aktuální zobrazení zobrazení měsíce; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) která je popsána v sadě Windows SDK. Pokud tato zpráva vrátí MCMV_MONTH, vrátí tato metoda hodnotu TRUE.

## <a name="cmonthcalctrlisyearview"></a><a name="isyearview"></a>CMonthCalCtrl::Zobrazení IsYearView

Označuje, zda je aktuální zobrazení ovládacího prvku kalendáře aktuálního měsíce zobrazením roku.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je aktuální zobrazení zobrazení rok; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) která je popsána v sadě Windows SDK. Pokud tato zpráva vrátí MCMV_YEAR, tato metoda vrátí hodnotu TRUE.

## <a name="cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a>CMonthCalCtrl::SetCalendarBorder

Nastaví šířku ohraničení ovládacího prvku kalendáře aktuálního měsíce.

```cpp
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*cxyHraniční*|[v] Šířka ohraničení v pixelech.|

### <a name="remarks"></a>Poznámky

Pokud je tato metoda úspěšná, šířka ohraničení je nastavena na parametr *cxyBorder.* V opačném případě se šířka ohraničení obnoví na výchozí hodnotu určenou aktuálním [motivem](/windows/win32/Controls/visual-styles-overview)nebo nulu, pokud nejsou použity motivy.

Tato metoda odešle [zprávu MCM_SETCALENDARBORDER,](/windows/win32/Controls/mcm-setcalendarborder) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_monthCalCtrl`která se používá k programovému přístupu k ovládacímu prvku měsíčního kalendáře. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví šířku ohraničení ovládacího prvku kalendáře měsíce na osm pixelů. Pomocí metody [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) určete, zda byla tato metoda úspěšná.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

## <a name="cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a>CMonthCalCtrl::SetCalendarBorderDefault

Nastaví výchozí šířku ohraničení ovládacího prvku kalendáře aktuálního měsíce.

```cpp
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Poznámky

Šířka ohraničení je nastavena na výchozí hodnotu určenou aktuálním [motivem](/windows/win32/Controls/visual-styles-overview)nebo nulu, pokud nejsou použity motivy.

Tato metoda odešle [zprávu MCM_SETCALENDARBORDER,](/windows/win32/Controls/mcm-setcalendarborder) která je popsána v sadě Windows SDK.

## <a name="cmonthcalctrlsetcalid"></a><a name="setcalid"></a>CMonthCalCtrl::SetCalID

Nastaví identifikátor kalendáře pro ovládací prvek kalendáře aktuálního měsíce.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*calid*|[v] Jedna z konstant [identifikátorů kalendáře.](/windows/win32/Intl/calendar-identifiers)|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Identifikátor kalendáře určuje kalendář specifický pro oblast, například gregoriánský (lokalizovaný), japonský nebo hidžra kalendář. `SetCalID` Pomocí metody můžete zobrazit kalendář určený parametrem *calid,* pokud je v počítači nainstalováno národní prostředí obsahující kalendář.

Tato metoda odešle [zprávu MCM_SETCALID,](/windows/win32/Controls/mcm-setcalid) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_monthCalCtrl`která se používá k programovému přístupu k ovládacímu prvku měsíčního kalendáře. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví ovládací prvek měsíčního kalendáře tak, aby se zobrazil kalendář Éry japonského císaře. Metoda `SetCalID` je úspěšná pouze v případě, že je tento kalendář nainstalován v počítači.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

## <a name="cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a>CMonthCalCtrl::SetCenturyView

Nastaví ovládací prvek kalendáře aktuálního měsíce tak, aby zobrazoval zobrazení století.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda používá [Metodu CMonthCalCtrl::SetCurrentView](#setcurrentview) `MCMV_CENTURY`k nastavení zobrazení , která představuje zobrazení století.

## <a name="cmonthcalctrlsetcolor"></a><a name="setcolor"></a>CMonthCalCtrl::SetColor

Nastaví barvu zadané oblasti ovládacího prvku měsíčního kalendáře.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Parametry

*nRegion*<br/>
Celá hodnota určující, kterou barvu měsíčního kalendáře má nastavit. Tato hodnota může být jedna z následujících.

|Hodnota|Význam|
|-----------|-------------|
|MCSC_BACKGROUND|Barva pozadí zobrazená mezi měsíci.|
|MCSC_MONTHBK|Barva pozadí zobrazená během měsíce.|
|MCSC_TEXT|Barva použitá k zobrazení textu do jednoho měsíce.|
|MCSC_TITLEBK|Barva pozadí zobrazená v názvu kalendáře.|
|MCSC_TITLETEXT|Barva použitá k zobrazení textu v názvu kalendáře.|
|MCSC_TRAILINGTEXT|Barva použitá k zobrazení textu záhlaví a koncového dne. Dny záhlaví a koncové dny jsou dny z předchozích a následujících měsíců, které se zobrazují v aktuálním kalendáři.|

*ref*<br/>
Hodnota COLORREF pro nové nastavení barev pro zadanou část ovládacího prvku kalendáře měsíce.

### <a name="return-value"></a>Návratová hodnota

Colorref hodnota, která představuje předchozí nastavení barev pro zadanou část ovládacího prvku kalendáře měsíce, pokud je úspěšná. V opačném případě tato zpráva vrátí -1.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor)zprávy Win32 , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

## <a name="cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a>CMonthCalCtrl::SetCurrentView

Nastaví ovládací prvek kalendáře aktuálního měsíce tak, aby zobrazoval zadané zobrazení.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwNewView*|[v] Jedna z následujících hodnot, která určuje měsíční, roční, deset let nebo století zobrazení.<br /><br /> MCMV_MONTH: Měsíční zobrazení<br /><br /> MCMV_YEAR: Roční pohled<br /><br /> MCMV_DECADE: Desetiletí pohled<br /><br /> MCMV_CENTURY: Century pohled|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu MCM_SETCURRENTVIEW,](/windows/win32/Controls/mcm-setcurrentview) která je popsána v sadě Windows SDK.

## <a name="cmonthcalctrlsetcursel"></a><a name="setcursel"></a>CMonthCalCtrl::SetCurSel

Nastaví aktuálně vybrané datum pro ovládací prvek měsíčního kalendáře.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt označující aktuálně vybraný ovládací prvek kalendáře měsíce.

*čas data*<br/>
Ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu, která obsahuje datum, které má být nastaveno jako aktuální výběr.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/mcm-setcursel)Win32 MCM_SETCURSEL , jak je popsáno v sadě Windows SDK. V implementaci `SetCurSel`knihovny MFC můžete `COleDateTime` určit využití, `CTime` použití `SYSTEMTIME` nebo využití struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

## <a name="cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a>CMonthCalCtrl::SetDayState

Nastaví zobrazení na dny v ovládacím prvku kalendáře měsíce.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Parametry

*nMěsíce*<br/>
Hodnota označující, kolik prvků jsou v poli, které *pStates* odkazuje.

*pstátyy*<br/>
Ukazatel na [pole MONTHDAYSTATE](/windows/win32/Controls/monthdaystate) hodnot, které definují, jak bude ovládací prvek kalendáře měsíce kreslit každý den v jeho zobrazení. Datový typ MONTHDAYSTATE je bitové pole, kde každý bit (1 až 31) představuje stav dne v měsíci. Pokud je bit zapnutý, odpovídající den se zobrazí tučně; v opačném případě se zobrazí bez důrazu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate)zprávy Win32 , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

## <a name="cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a>CMonthCalCtrl::SetDecadeView

Nastaví aktuální ovládací prvek kalendáře měsíce na zobrazení desetiletí.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metoda nastavit `MCMV_DECADE`zobrazení , což představuje zobrazení desetiletí.

## <a name="cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a>CMonthCalCtrl::SetFirstDayOfWeek

Nastaví den v týdnu, který se má zobrazit v levém sloupci kalendáře.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Parametry

*iDay*<br/>
Celá hodnota představující den, který má být nastaven jako první den v týdnu. Tato hodnota musí být jedním z čísel dne. Viz [GetFirstDayOfWeek](#getfirstdayofweek) pro popis denních čísel.

*lpnStarý*<br/>
Ukazatel na celé číslo označující první den v týdnu dříve nastavena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je předchozí první den v týdnu nastaven na jinou hodnotu než hodnotu LOCALE_IFIRSTDAYOFWEEK, což je den uvedený v nastavení ovládacího panelu. V opačném případě vrátí tato funkce hodnotu 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek)zprávy Win32 , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

## <a name="cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a>CMonthCalCtrl::SetMaxSelCount

Nastaví maximální počet dní, které lze vybrat v ovládacím prvku měsíčního kalendáře.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Parametry

*nMax*<br/>
Hodnota, která bude nastavena tak, aby představovala maximální počet volitelných dnů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/mcm-setmaxselcount)Win32 MCM_SETMAXSELCOUNT , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

## <a name="cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a>CMonthCalCtrl::SetMonthDelta

Nastaví rychlost posouvání pro ovládací prvek měsíčního kalendáře.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Parametry

*iDelta*<br/>
Počet měsíců, které mají být nastaveny jako rychlost posouvání ovládacího prvku. Pokud je tato hodnota nulová, rozdíl měsíce se obnoví na výchozí hodnotu, což je počet měsíců zobrazených v ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Předchozí rychlost posouvání. Pokud rychlost posouvání nebyla dříve nastavena, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/mcm-setmonthdelta)Win32 MCM_SETMONTHDELTA , jak je popsáno v sadě Windows SDK.

## <a name="cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a>CMonthCalCtrl::SetMonthView

Nastaví ovládací prvek kalendáře aktuálního měsíce tak, aby zobrazoval zobrazení měsíce.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda používá [Metodu CMonthCalCtrl::SetCurrentView](#setcurrentview) k nastavení zobrazení na MCMV_MONTH, což představuje zobrazení měsíce.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_monthCalCtrl`která se používá k programovému přístupu k ovládacímu prvku měsíčního kalendáře. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví ovládací prvek kalendáře měsíce pro zobrazení měsíc, rok, desetiletí a století.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

## <a name="cmonthcalctrlsetrange"></a><a name="setrange"></a>CMonthCalCtrl::SetRange

Nastaví minimální a maximální povolená data pro ovládací prvek měsíčního kalendáře.

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
Ukazatel na `COleDateTime` objekt, `CTime` objekt nebo [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu obsahující datum na nejnižším konci rozsahu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objekt, `CTime` objekt nebo `SYSTEMTIME` strukturu obsahující datum na nejvyšším konci rozsahu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/mcm-setrange)Win32 MCM_SETRANGE , jak je popsáno v sadě Windows SDK. V `SetRange`implementaci knihovny MFC můžete `COleDateTime` určit `CTime` využití, využití `SYSTEMTIME` nebo využití struktury.

### <a name="example"></a>Příklad

  Viz příklad [cmonthcalctrl::GetRange](#getrange).

## <a name="cmonthcalctrlsetselrange"></a><a name="setselrange"></a>CMonthCalCtrl::SetSelRange

Nastaví výběr pro ovládací prvek měsíčního kalendáře na dané časové období.

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
Ukazatel na `COleDateTime` objekt, `CTime` objekt nebo [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu obsahující datum na nejnižším konci rozsahu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objekt, `CTime` objekt nebo `SYSTEMTIME` strukturu obsahující datum na nejvyšším konci rozsahu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/mcm-setselrange)Win32 MCM_SETSELRANGE , jak je popsáno v sadě Windows SDK. V `SetSelRange`implementaci knihovny MFC můžete `COleDateTime` určit `CTime` využití, využití `SYSTEMTIME` nebo využití struktury.

## <a name="cmonthcalctrlsettoday"></a><a name="settoday"></a>CMonthCalCtrl::SetToday

Nastaví ovládací prvek kalendáře pro aktuální den.

```cpp
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje aktuální datum.

*čas data*<br/>
Ve druhé verzi ukazatel na [ctime](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující aktuální informace o datu. Ve třetí verzi ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu, která obsahuje aktuální informace o datu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/mcm-settoday)Win32 MCM_SETTODAY , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [cMonthCalCtrl::GetToday](#gettoday).

## <a name="cmonthcalctrlsetyearview"></a><a name="setyearview"></a>CMonthCalCtrl::SetYearView

Nastaví zobrazení aktuálního měsíčního kalendáře na rok.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metoda nastavit zobrazení MCMV_YEAR, který představuje roční zobrazení.

## <a name="cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a>CMonthCalCtrl::SizeMinReq

Zobrazí ovládací prvek kalendář měsíce na minimální velikost, která zobrazuje jeden měsíc.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Parametry

*bPřekreslit*<br/>
Určuje, zda má být ovládací prvek překreslen. Ve výchozím nastavení true. Pokud false, nedojde k žádné překreslení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je velikost ovládacího prvku kalendáře měsíce na jeho minimum; jinak 0.

### <a name="remarks"></a>Poznámky

Volání `SizeMinReq` úspěšně zobrazí ovládací prvek kalendáře celého měsíce pro kalendář jednoho měsíce.

## <a name="cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a>CMonthCalCtrl::SizeRectToMin

Pro ovládací prvek kalendáře aktuální měsíc vypočítá nejmenší obdélník, který může obsahovat všechny kalendáře, které se vejdou do zadaného obdélníku.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpRect*|[v] Ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu, která definuje obdélník, který obsahuje požadovaný počet kalendářů.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu, která definuje obdélník, jehož velikost je menší nebo rovna obdélník definované *lpRect* parametr.

### <a name="remarks"></a>Poznámky

Tato metoda vypočítá, kolik kalendářů se vejde do obdélníku určeného parametrem *lpRect* a potom vrátí nejmenší obdélník, který může obsahovat tento počet kalendářů. Ve skutečnosti tato metoda zmenší zadaný obdélník přesně přizpůsobit požadovaný počet kalendářů.

Tato metoda odešle [zprávu MCM_SIZERECTTOMIN,](/windows/win32/Controls/mcm-sizerecttomin) která je popsána v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)
