---
title: Cmonthcalctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0d66689071371f1e951c7f8d84fe0c4c69b4c1c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433764"
---
# <a name="cmonthcalctrl-class"></a>Cmonthcalctrl – třída

Zapouzdřuje funkce ovládací prvek měsíční kalendář.

## <a name="syntax"></a>Syntaxe

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Vytvoří `CMonthCalCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMonthCalCtrl::Create](#create)|Vytvoří ovládací prvek měsíční kalendář a připojí ho k `CMonthCalCtrl` objektu.|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Zjišťuje šířku ohraničení ovládacího prvku kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Získá počet kalendáře zobrazí v ovládacím prvku kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Načte informace o ovládacím prvku kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::GetCalID](#getcalid)|Načte identifikátor kalendáře pro ovládací prvek kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::GetColor](#getcolor)|Získá barva zadané oblasti ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Načte zobrazení, které se nyní zobrazí v ovládacím prvku kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::GetCurSel](#getcursel)|Načte systémový čas je určeno aktuálně vybrané datum.|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Získá první den v týdnu, kdy se zobrazí v levém sloupci kalendáře.|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Načte aktuální maximální počet dní, které se dají vybrat ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Získá maximální šířku ovládacího prvku Kalendář aktuální měsíc na řetězec "Dnes".|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Získá minimální velikost požadovaná k zobrazení celého měsíce v ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Načte kurz posuvníku pro ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Načte nejnovější informace, které představují vysoké a nízké omezení zobrazení prvku měsíční kalendář.|
|[CMonthCalCtrl::GetRange](#getrange)|Načte aktuální minimální a maximální datum nastaveno v ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::GetSelRange](#getselrange)|Načte informace o datu představující horní a dolní mez rozsahu kalendářních dat, který je aktuálně vybraný uživatelem.|
|[CMonthCalCtrl::GetToday](#gettoday)|Načte informace o datu kalendářní datum zadané jako "dnes" pro ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::HitTest](#hittest)|Určuje, jaké části ovládací prvek měsíční kalendář je v daném bodě na obrazovce.|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Označuje, zda je aktuální zobrazení ovládacího prvku Kalendář aktuální měsíc zobrazení století.|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Označuje, zda je aktuální zobrazení ovládacího prvku Kalendář aktuální měsíc desetiletí zobrazení.|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Označuje, zda je aktuální zobrazení ovládacího prvku Kalendář aktuální měsíc zobrazení měsíc.|
|[CMonthCalCtrl::IsYearView](#isyearview)|Označuje, zda je aktuální zobrazení ovládacího prvku Kalendář aktuální měsíc roku zobrazení.|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Nastaví šířku ohraničení ovládacího prvku kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Nastaví výchozí šířku ohraničení ovládacího prvku kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::SetCalID](#setcalid)|Nastaví identifikátor kalendáře pro ovládací prvek kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Nastaví ovládací prvek kalendáři aktuálního měsíce zobrazení století.|
|[CMonthCalCtrl::SetColor](#setcolor)|Nastavuje barvu zadané oblasti ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Nastaví ovládací prvek kalendáři aktuálního měsíce zadaného zobrazení.|
|[CMonthCalCtrl::SetCurSel](#setcursel)|Nastaví aktuálně vybrané datum pro ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::SetDayState](#setdaystate)|Nastaví zobrazení dní v ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Nastaví k zobrazení desetiletí řídit kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Nastaví dne v týdnu, kdy se zobrazí v levém sloupci kalendáře.|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Nastaví maximální počet dní, které se dají vybrat ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Nastaví frekvenci posuvníku pro ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Nastaví ovládací prvek kalendáři aktuálního měsíce zobrazení měsíc.|
|[CMonthCalCtrl::SetRange](#setrange)|Nastaví minimální a maximální počet povolených dat pro ovládací prvek měsíční kalendář.|
|[CMonthCalCtrl::SetSelRange](#setselrange)|Ovládací prvek výběru pro měsíční kalendář sady pro daný rozsah.|
|[CMonthCalCtrl::SetToday](#settoday)|Nastaví ovládací prvek kalendáři pro aktuální den.|
|[CMonthCalCtrl::SetYearView](#setyearview)|Nastaví k zobrazení rok řídit kalendáři aktuálního měsíce.|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Ovládací prvek měsíční kalendář repaints velikost minimální, jeden měsíc.|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Aktuální ovládací prvek měsíční kalendář vypočítá nejmenší obdélník, který může obsahovat všechny kalendáře, které odpovídají zadaným obdélníku.|

## <a name="remarks"></a>Poznámky

Ovládací prvek měsíční kalendář poskytuje uživatelské rozhraní jednoduché kalendáře, ze kterého může uživatel vybrat datum. Uživatel může změnit zobrazení podle:

- Posouvání zpět a vpřed, z měsíce na měsíc.

- Klikněte na text dnes zobrazíte aktuální den (Pokud se nepoužívá MCS_NOTODAY style).

- Výběr měsíc nebo rok z místní nabídky.

Můžete přizpůsobit v měsíci v kalendáři ovládacího prvku s použitím různých stylů objektu při vytváření. Tyto styly jsou popsány v [– styly ovládacích prvků kalendáře měsíce](/windows/desktop/Controls/month-calendar-control-styles) v sadě Windows SDK.

Ovládací prvek měsíční kalendář můžete zobrazení více než jednoho měsíce a může znamenat speciální dnů (například svátků) podle tučné datum.

Další informace o použití ovládací prvek měsíční kalendář, naleznete v tématu [používání atributu CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdtctl.h

##  <a name="cmonthcalctrl"></a>  CMonthCalCtrl::CMonthCalCtrl

Vytvoří `CMonthCalCtrl` objektu.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Poznámky

Je nutné volat `Create` po vytvoření objektu.

##  <a name="create"></a>  CMonthCalCtrl::Create

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
Určuje kombinaci styly Windows použité pro ovládací prvek měsíční kalendář. Zobrazit [– styly ovládacích prvků kalendáře měsíce](/windows/desktop/Controls/month-calendar-control-styles) v sadě Windows SDK pro další informace o stylech.

*Rect*<br/>
Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury. Obsahuje umístění a velikost ovládací prvek měsíční kalendář.

*PT*<br/>
Odkaz na [bodu](https://msdn.microsoft.com/library/windows/desktop/dd162805) strukturu, která identifikuje umístění ovládací prvek měsíční kalendář.

*pParentWnd*<br/>
Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno Ovládací prvek měsíční kalendář. Nesmí být NULL.

*nID*<br/>
Určuje ID ovládacího prvku měsíční kalendář

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se inicializace byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Vytvořit za měsíc v kalendáři ovládacího prvku ve dvou krocích:

1. Volání [atributu CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) k vytvoření `CMonthCalCtrl` objektu.

1. Voláním této členské funkce, která vytvoří ovládací prvek měsíční kalendář a připojí ho k `CMonthCalCtrl` objektu.

Při volání `Create`, běžné ovládací prvky jsou inicializovány. Verze `Create` je volání Určuje, jak se velikosti:

- Pokud chcete, aby automaticky velikost ovládacího prvku na jeden měsíc knihovny MFC, volat přepsání, které používá *pt* parametru.

- Chcete-li velikost ovládacího prvku, zavolejte přepsat tuto funkci, která se používá *rect* parametru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder

Zjišťuje šířku ohraničení ovládacího prvku kalendáři aktuálního měsíce.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Tloušťka ohraničení ovládacího prvku v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [MCM_GETCALENDARBORDER](/windows/desktop/Controls/mcm-getcalendarborder) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount

Získá počet kalendáře zobrazí v ovládacím prvku kalendáři aktuálního měsíce.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet aktuálně zobrazený v ovládacím prvku měsíční kalendář kalendáře. Maximální povolený počet kalendářů se 12.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [MCM_GETCALENDARCOUNT](/windows/desktop/Controls/mcm-getcalendarcount) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo

Načte informace o ovládacím prvku kalendáři aktuálního měsíce.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pmcGridInfo*|[out] Ukazatel [MCGRIDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagmcgridinfo) struktura, která obdrží informace o ovládacím prvku kalendáři aktuálního měsíce. Volající zodpovídá za přidělování a inicializaci této struktury.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [MCM_GETCALENDARGRIDINFO](/windows/desktop/Controls/mcm-getcalendargridinfo) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která je použita k programovému přístupu ke ovládací prvek měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu používá `GetCalendarGridInfo` metodu pro načtení datum kalendáře, která zobrazuje ovládací prvek aktuální měsíční kalendář.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID

Načte identifikátor kalendáře pro ovládací prvek kalendáři aktuálního měsíce.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Návratová hodnota

Jeden z [identifikátor kalendáře](/windows/desktop/Intl/calendar-identifiers) konstanty.

### <a name="remarks"></a>Poznámky

Identifikátor kalendáře označuje oblast kalendář, jako je například Gregoriánský (lokalizovaný), japonštinu nebo hidžra kalendáře. Aplikace můžete použít identifikátor kalendář, který má různé jazykové podpory funkce.

Tato metoda odesílá [MCM_GETCALID](/windows/desktop/Controls/mcm-getcalid) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor

Načte barva oblast v měsíci v kalendáři ovládací prvek určený *nRegion*.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Parametry

*nRegion*<br/>
Oblasti prvku měsíční kalendář, ze kterého je načíst barvu. Seznam hodnot, najdete v článku *nRegion* parametr [setcolor –](#setcolor).

### <a name="return-value"></a>Návratová hodnota

A [COLORREF](/windows/desktop/gdi/colorref) hodnota, která určuje barvu přidruženou s část ovládací prvek měsíční kalendář, pokud je úspěšná. V opačném případě tato členská funkce vrátí hodnotu -1.

##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView

Načte zobrazení, které se nyní zobrazí v ovládacím prvku kalendáři aktuálního měsíce.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zobrazení, který je označen pomocí jedné z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|MCMV_MONTH|Měsíční zobrazení|
|MCMV_YEAR|Roční zobrazení|
|MCMV_DECADE|Dekáda zobrazení|
|MCMV_CENTURY|Zobrazení století|

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která je použita k programovému přístupu ke ovládací prvek měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad sestavy kódu, které zobrazení měsíčního kalendáře řídit aktuálně zobrazuje.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>  CMonthCalCtrl::GetCurSel

Načte systémový čas je určeno aktuálně vybrané datum.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu. Získá aktuální čas.

*pDateTime*<br/>
Ukazatel [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která se zobrazí informace o aktuálně vybrané datum. Tento parametr musí být platnou adresou a nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. otherwize 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETCURSEL](/windows/desktop/Controls/mcm-getcursel), jak je popsáno v sadě Windows SDK.

> [!NOTE]
>  Tato členská funkce selže, pokud není nastaven styl MCS_MULTISELECT.

V implementace MFC atributu `GetCurSel`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.

##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek

Získá první den v týdnu, kdy se zobrazí v levém sloupci kalendáře.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Parametry

*pbLocal*<br/>
Ukazatel na hodnotu BOOL. Pokud je hodnota nenulová, nastavení ovládacího prvku neodpovídá nastavení v Ovládacích panelech.

### <a name="return-value"></a>Návratová hodnota

Celočíselná hodnota představující první den v týdnu. Zobrazit **poznámky** Další informace o co představují tyto celých čísel.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-getfirstdayofweek), jak je popsáno v sadě Windows SDK. Dny v týdnu jsou reprezentovány jako celá čísla, následujícím způsobem.

|Hodnota|Den v týdnu|
|-----------|---------------------|
|0|Pondělí|
|1|Úterý|
|2|Středa|
|3|Čtvrtek|
|4|Pátek|
|5|Sobota|
|6|Neděle|

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek).

##  <a name="getmaxselcount"></a>  CMonthCalCtrl::GetMaxSelCount

Načte aktuální maximální počet dní, které se dají vybrat ovládací prvek měsíční kalendář.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celočíselná hodnota představující celkový počet dnů, které lze vybrat pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETMAXSELCOUNT](/windows/desktop/Controls/mcm-getmaxselcount), jak je popsáno v sadě Windows SDK. Tuto funkci člena můžete použijte pro ovládací prvky s nastavenou MCS_MULTISELECT style.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMonthCalCtrl::SetMaxSelCount](#setmaxselcount).

##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth

Získá maximální šířku ovládacího prvku Kalendář aktuální měsíc na řetězec "Dnes".

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka v pixelech na řetězec "Dnes".

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která je použita k programovému přístupu ke ovládací prvek měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, `GetMaxTodayWidth` metody.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Poznámky

Uživatel může vrátit na aktuální datum kliknutím na řetězec "Dnes", který se zobrazí v dolní části ovládací prvek měsíční kalendář. Řetězec "Dnes" obsahuje text popisku a textového datum.

Tato metoda odesílá [MCM_GETMAXTODAYWIDTH](/windows/desktop/Controls/mcm-getmaxtodaywidth) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect

Získá minimální velikost požadovaná k zobrazení celého měsíce v ovládací prvek měsíční kalendář.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Parametry

*pRect*<br/>
Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která bude dostávat informace ohraničující obdélník. Tento parametr musí být platnou adresou a nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, tato členská funkce vrátí nenulovou hodnotu a `lpRect` obdrží příslušné ohraničující konkrétní informace. Pokud není úspěšné, členská funkce vrátí 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETMINREQRECT](/windows/desktop/Controls/mcm-getminreqrect), jak je popsáno v sadě Windows SDK.

##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta

Načte kurz posuvníku pro ovládací prvek měsíční kalendář.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Návratová hodnota

Kurz posuvníku pro ovládací prvek měsíční kalendář. Posunout míra je počet měsíců, že ovládací prvek přesune zobrazení, když uživatel klikne na tlačítko posuvníku jednou.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETMONTHDELTA](/windows/desktop/Controls/mcm-getmonthdelta), jak je popsáno v sadě Windows SDK.

##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange

Načte nejnovější informace, které představují vysoké a nízké omezení zobrazení prvku měsíční kalendář.

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
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje minimální datum, které jsou povoleny.

*refMaxRange*<br/>
Odkaz na `COleDateTime` nebo `CTime` objekt, který obsahuje maximální povolené datum.

*pMinRange*<br/>
Ukazatel [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury obsahující data na nejnižší konec rozsahu.

*pMaxRange*<br/>
Ukazatel `SYSTEMTIME` struktury obsahující datum v nejvyšší konec rozsahu.

*dwFlags*<br/>
Hodnota, která určuje obor omezení rozsahu, který se má načíst. Tato hodnota musí být jeden z následujících akcí.

|Hodnota|Význam|
|-----------|-------------|
|GMR_DAYSTATE|Zahrnout před a koncové měsíců viditelný rozsah, které jsou zobrazeny pouze částečně.|
|GMR_VISIBLE|Zahrnout jenom v měsících, které jsou zcela zobrazeny.|

### <a name="return-value"></a>Návratová hodnota

Celé číslo představující rozsah, v měsících, předané dvě omezení indikován *refMinRange* a *refMaxRange* ve verzích prvního a druhého nebo *pMinRange* a *pMaxRange* ve třetí verzi.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETMONTHRANGE](/windows/desktop/Controls/mcm-getmonthrange), jak je popsáno v sadě Windows SDK. V implementace MFC atributu `GetMonthRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMonthCalCtrl::SetDayState](#setdaystate).

##  <a name="getrange"></a>  CMonthCalCtrl::GetRange

Načte aktuální minimální a maximální datum nastaveno v ovládací prvek měsíční kalendář.

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
Ukazatel na `COleDateTime` objektu, `CTime` objektu, nebo [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury obsahující data na nejnižší konec rozsahu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objektu, `CTime` objektu, nebo [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury obsahující datum v nejvyšší konec rozsahu.

### <a name="return-value"></a>Návratová hodnota

DWORD, který může být nula (bez omezení jsou nastavené) nebo ke kombinaci komponent následující hodnoty, které určují informace o limitu.

|Hodnota|Význam|
|-----------|-------------|
|GDTR_MAX|Maximální limit nastavený pro ovládací prvek; *pMaxRange* je platný a obsahuje informace o příslušné datum.|
|GDTR_MIN|Minimální omezení je nastavena pro ovládací prvek; *pMinRange* je platný a obsahuje informace o příslušné datum.|

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETRANGE](/windows/desktop/Controls/mcm-getrange), jak je popsáno v sadě Windows SDK. V implementace MFC atributu `GetRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>  CMonthCalCtrl::GetSelRange

Načte informace o datu představující horní a dolní mez rozsahu kalendářních dat, který je aktuálně vybraný uživatelem.

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
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje minimální datum, které jsou povoleny.

*refMaxRange*<br/>
Odkaz na `COleDateTime` nebo `CTime` objekt, který obsahuje maximální povolené datum.

*pMinRange*<br/>
Ukazatel [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury obsahující data na nejnižší konec rozsahu.

*pMaxRange*<br/>
Ukazatel `SYSTEMTIME` struktury obsahující datum v nejvyšší konec rozsahu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETSELRANGE](/windows/desktop/Controls/mcm-getselrange), jak je popsáno v sadě Windows SDK. `GetSelRange` selže, pokud se použije ovládací prvek měsíční kalendář, která nepoužívá MCS_MULTISELECT styl.

V implementace MFC atributu `GetSelRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.

##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday

Načte informace o datu kalendářní datum zadané jako "dnes" pro ovládací prvek měsíční kalendář.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který označuje aktuální den.

*pDateTime*<br/>
Ukazatel [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která se zobrazí informace o datu. Tento parametr musí být platnou adresou a nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_GETTODAY](/windows/desktop/Controls/mcm-gettoday), jak je popsáno v sadě Windows SDK. V implementace MFC atributu `GetToday`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>  CMonthCalCtrl::HitTest

Určuje které ovládací prvek měsíční kalendář, pokud existuje, je na určené pozici.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Parametry

*pMCHitTest*<br/>
Ukazatel [MCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-mchittestinfo) body struktury obsahující testování přístupů pro ovládací prvek měsíční kalendář.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD. Rovná **uHit** člena `MCHITTESTINFO` struktury.

### <a name="remarks"></a>Poznámky

`HitTest` používá `MCHITTESTINFO` struktura, která obsahuje informace o volání testu.

##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView

Označuje, zda je aktuální zobrazení ovládacího prvku Kalendář aktuální měsíc zobrazení století.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je aktuální zobrazení nastaveno zobrazení století. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) zprávu, která je popsána v sadě Windows SDK. Pokud tuto zprávu vrátí MCMV_CENTURY, tato metoda vrátí hodnotu TRUE.

##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView

Označuje, zda je aktuální zobrazení ovládacího prvku Kalendář aktuální měsíc desetiletí zobrazení.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je aktuální zobrazení nastaveno desetiletí zobrazení. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) zprávu, která je popsána v sadě Windows SDK. Pokud tuto zprávu vrátí MCMV_DECADE, tato metoda vrátí hodnotu TRUE.

##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView

Označuje, zda je aktuální zobrazení ovládacího prvku Kalendář aktuální měsíc zobrazení měsíc.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je aktuální zobrazení nastaveno zobrazení měsíc; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) zprávu, která je popsána v sadě Windows SDK. Pokud tuto zprávu vrátí MCMV_MONTH, tato metoda vrátí hodnotu TRUE.

##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView

Označuje, zda je aktuální zobrazení ovládacího prvku Kalendář aktuální měsíc roku zobrazení.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je aktuální zobrazení nastaveno zobrazení rok. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) zprávu, která je popsána v sadě Windows SDK. Pokud tuto zprávu vrátí MCMV_YEAR, tato metoda vrátí hodnotu TRUE.

##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder

Nastaví šířku ohraničení ovládacího prvku kalendáři aktuálního měsíce.

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*cxyBorder*|[in] Šířka ohraničení v pixelech.|

### <a name="remarks"></a>Poznámky

Pokud tato metoda bude úspěšná, šířka ohraničení nastaven *cxyBorder* parametru. V opačném případě šířka ohraničení se resetují na výchozí hodnotu, která je určená aktuální [motiv](/windows/desktop/Controls/visual-styles-overview), nebo nula, pokud nejsou použity motivů.

Tato metoda odesílá [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která je použita k programovému přístupu ke ovládací prvek měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující kód příklad nastaví šířku ohraničení měsíční kalendář ovládací prvek na osm pixelů. Použití [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) metodou ke zjištění, zda tato metoda byla úspěšná.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault

Nastaví výchozí šířku ohraničení ovládacího prvku kalendáři aktuálního měsíce.

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Poznámky

Šířka ohraničení nastavena na výchozí hodnotu zadanou pomocí aktuálního [motiv](/windows/desktop/Controls/visual-styles-overview), nebo nula, pokud nejsou použity motivů.

Tato metoda odesílá [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder) zprávu, která je popsána v sadě Windows SDK.

##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID

Nastaví identifikátor kalendáře pro ovládací prvek kalendáři aktuálního měsíce.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ID_kal*|[in] Jeden z [identifikátor kalendáře](/windows/desktop/Intl/calendar-identifiers) konstanty.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Určuje identifikátor kalendáře konkrétní oblasti Kalendář, jako je například Gregoriánský (lokalizovaný), japonštinu nebo hidžra kalendáře. Použití `SetCalID` metodu pro zobrazení kalendáře, která je zadána *ID_kal* parametru národního prostředí, který obsahuje kalendář je nainstalován v počítači.

Tato metoda odesílá [MCM_SETCALID](/windows/desktop/Controls/mcm-setcalid) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která je použita k programovému přístupu ke ovládací prvek měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví ovládací prvek měsíční kalendář k zobrazení kalendáře období japonský kalendář. `SetCalID` Metoda bude úspěšná pouze v případě, že kalendář je nainstalovaná ve vašem počítači.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView

Nastaví ovládací prvek kalendáři aktuálního měsíce zobrazení století.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metody nastavte zobrazení `MCMV_CENTURY`, která představuje století zobrazení.

##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor

Nastavuje barvu zadané oblasti ovládací prvek měsíční kalendář.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Parametry

*nRegion*<br/>
Celočíselná hodnota, kterou barvu kalendáře měsíce nastavit zadání. Tato hodnota může být jedna z následujících akcí.

|Hodnota|Význam|
|-----------|-------------|
|MCSC_BACKGROUND|Barva pozadí zobrazená mezi měsíců.|
|MCSC_MONTHBK|Barva pozadí zobrazená v rámci měsíce.|
|MCSC_TEXT|Barva použitá k zobrazení textu během jednoho měsíce.|
|MCSC_TITLEBK|Barva pozadí zobrazená v nadpisu kalendáře.|
|MCSC_TITLETEXT|Barva použitá k zobrazení textu v nadpisu kalendáře.|
|MCSC_TRAILINGTEXT|Barva použitá k zobrazení textu záhlaví a na konci dne. Úvodní a koncové dny jsou dny z předchozího a následujícího měsíce, které se zobrazují na aktuální kalendář.|

*ref*<br/>
COLORREF hodnotu pro toto nové nastavení barev pro specifikovanou část ovládací prvek měsíční kalendář.

### <a name="return-value"></a>Návratová hodnota

COLORREF hodnotu, která v případě úspěšného ověření představuje předchozí nastavení barev pro specifikovanou část ovládací prvek měsíční kalendář. Tato zpráva v opačném případě vrátí hodnotu -1.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETCOLOR](/windows/desktop/Controls/mcm-setcolor), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView

Nastaví ovládací prvek kalendáři aktuálního měsíce zadaného zobrazení.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwNewView*|[in] Jeden z následujících hodnot, které určuje měsíční, roční, deset nebo zobrazení století.<br /><br /> MCMV_MONTH: Zobrazení měsíčního<br /><br /> MCMV_YEAR: Roční zobrazení<br /><br /> MCMV_DECADE: Zobrazení desetiletí<br /><br /> MCMV_CENTURY: Zobrazení století|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [MCM_SETCURRENTVIEW](/windows/desktop/Controls/mcm-setcurrentview) zprávu, která je popsána v sadě Windows SDK.

##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel

Nastaví aktuálně vybrané datum pro ovládací prvek měsíční kalendář.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který označuje ovládací prvek aktuálně vybrané měsíční kalendář.

*pDateTime*<br/>
Ukazatel [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturu, která obsahuje datum nastavit jako aktuální výběr.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETCURSEL](/windows/desktop/Controls/mcm-setcursel), jak je popsáno v sadě Windows SDK. V implementace MFC atributu `SetCurSel`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>  CMonthCalCtrl::SetDayState

Nastaví zobrazení dní v ovládací prvek měsíční kalendář.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Parametry

*nMonths*<br/>
Hodnota označující počet prvků v poli, která *pStates* odkazuje na.

*pStates*<br/>
Ukazatel [MONTHDAYSTATE](/windows/desktop/Controls/monthdaystate) pole hodnot, které definují, jak bude ovládací prvek měsíční kalendář kreslení každý den v jeho zobrazení. Datový typ MONTHDAYSTATE je bitové pole, přičemž každý bit (1 až 31) představuje stavu za den v měsíci. Pokud bit zapnutý, zobrazí se odpovídající den v bold; v opačném případě se zobrazí s žádné zvýraznění.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETDAYSTATE](/windows/desktop/Controls/mcm-setdaystate), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView

Nastaví k zobrazení desetiletí řídit kalendáři aktuálního měsíce.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metody nastavte zobrazení `MCMV_DECADE`, která představuje zobrazení deset let.

##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek

Nastaví dne v týdnu, kdy se zobrazí v levém sloupci kalendáře.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Parametry

*iDay*<br/>
Celočíselná hodnota představující den, kdy má být nastavena jako první den v týdnu. Tato hodnota musí být jeden z čísla dne. Zobrazit [GetFirstDayOfWeek](#getfirstdayofweek) popis čísla dne.

*lpnOld*<br/>
Nastavte ukazatel na celé číslo označující první den v týdnu dříve.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud předchozí první den v týdnu je nastavena na jinou hodnotu než u LOCALE_IFIRSTDAYOFWEEK, což je den uvedené v nastavení ovládacího panelu. V opačném případě vrátí 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-setfirstdayofweek), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount

Nastaví maximální počet dní, které se dají vybrat ovládací prvek měsíční kalendář.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Parametry

*Nmaximum*<br/>
Hodnota, která bude nastavena na představuje maximální počet volitelných dnů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETMAXSELCOUNT](/windows/desktop/Controls/mcm-setmaxselcount), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta

Nastaví frekvenci posuvníku pro ovládací prvek měsíční kalendář.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Parametry

*položky iDelta*<br/>
Počet měsíců nastavit jako míra ovládacího prvku posuvníku. Pokud tato hodnota je nula, rozdílového měsíc resetuje na výchozí, což je počet měsíců zobrazí v ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Předchozí kurz posuvníku. Pokud frekvence posuvníku nebyla dříve nastavena, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETMONTHDELTA](/windows/desktop/Controls/mcm-setmonthdelta), jak je popsáno v sadě Windows SDK.

##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView

Nastaví ovládací prvek kalendáři aktuálního měsíce zobrazení měsíc.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metody nastavte zobrazení MCMV_MONTH, který představuje zobrazení měsíc.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, která je použita k programovému přístupu ke ovládací prvek měsíční kalendář. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví ovládací prvek měsíční kalendář zobrazíte měsíc, rok, deset let a zobrazení století.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>  CMonthCalCtrl::SetRange

Nastaví minimální a maximální povolený data pro ovládací prvek měsíční kalendář.

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
Ukazatel na `COleDateTime` objektu, `CTime` objektu, nebo [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury obsahující data na nejnižší konec rozsahu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objektu, `CTime` objektu, nebo `SYSTEMTIME` struktury obsahující datum v nejvyšší konec rozsahu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETRANGE](/windows/desktop/Controls/mcm-setrange), jak je popsáno v sadě Windows SDK. V implementace MFC atributu `SetRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMonthCalCtrl::GetRange](#getrange).

##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange

Ovládací prvek výběru pro měsíční kalendář sady pro daný rozsah.

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
Ukazatel na `COleDateTime` objektu, `CTime` objektu, nebo [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury obsahující data na nejnižší konec rozsahu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objektu, `CTime` objektu, nebo `SYSTEMTIME` struktury obsahující datum v nejvyšší konec rozsahu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETSELRANGE](/windows/desktop/Controls/mcm-setselrange), jak je popsáno v sadě Windows SDK. V implementace MFC atributu `SetSelRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.

##  <a name="settoday"></a>  CMonthCalCtrl::SetToday

Nastaví ovládací prvek kalendáři pro aktuální den.

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
  void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parametry

*refDateTime*<br/>
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje aktuální datum.

*pDateTime*<br/>
V druhou verzi, ukazatel [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje informace o aktuálním datem. Ve třetí verzi ukazatel [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturu, která obsahuje informace o aktuálním datem.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [MCM_SETTODAY](/windows/desktop/Controls/mcm-settoday), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMonthCalCtrl::GetToday](#gettoday).

##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView

Nastaví k zobrazení rok řídit kalendáři aktuálního měsíce.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metody nastavte zobrazení MCMV_YEAR, který představuje roční zobrazení.

##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq

Zobrazí měsíc ovládacího prvku kalendáře na minimální velikost, která zobrazuje jeden měsíc.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Parametry

*bRepaint*<br/>
Určuje, zda je ovládací prvek překreslen. Ve výchozím nastavení hodnotu TRUE. Pokud má hodnotu FALSE, žádné překreslení vyvolá.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud ovládací prvek měsíční kalendář přizpůsoben pro minimální; jinak 0.

### <a name="remarks"></a>Poznámky

Volání `SizeMinReq` úspěšně zobrazí ovládací prvek celý měsíční kalendář pro jeden měsíční kalendář.

##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin

Aktuální ovládací prvek měsíční kalendář vypočítá nejmenší obdélník, který může obsahovat všechny kalendáře, které odpovídají zadaným obdélníku.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lprect –*|[in] Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturu, která definuje obdélník, který obsahuje požadované číslo kalendáře.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturu, která definuje obdélníku, jehož velikost je menší než nebo rovna obdélníku definovaném *lprect –* parametru.

### <a name="remarks"></a>Poznámky

Tato metoda vypočítá počet kalendáře lze zobrazit v obdélníku určené *lprect –* parametr a potom vrátí nejmenší obdélník, který může obsahovat tento počet kalendáře. V důsledku toho tato metoda zmenšuje zadané obdélník přesně podle požadovaného počtu kalendáře.

Tato metoda odesílá [MCM_SIZERECTTOMIN](/windows/desktop/Controls/mcm-sizerecttomin) zprávu, která je popsána v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Ukázka CMNCTRL1 knihovny MFC](../../visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl – třída](../../mfc/reference/cdatetimectrl-class.md)
