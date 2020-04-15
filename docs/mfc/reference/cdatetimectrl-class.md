---
title: Třída CDateTimeCtrl
ms.date: 11/04/2016
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
ms.openlocfilehash: d0433507c32c7359f8033836bf845defa8ad7f7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321903"
---
# <a name="cdatetimectrl-class"></a>Třída CDateTimeCtrl

Zapouzdřuje funkce ovládacího prvku pro výběr data a času.

## <a name="syntax"></a>Syntaxe

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Vytvoří `CDateTimeCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDateTimeCtrl::ZavřítMonthCal](#closemonthcal)|Zavře aktuální ovládací prvek pro výběr data a času.|
|[CDateTimeCtrl::Vytvořit](#create)|Vytvoří ovládací prvek pro výběr data a `CDateTimeCtrl` času a připojí jej k objektu.|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Načte informace o aktuálním ovládacím prvku výběru data a času.|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Vrátí ideální velikost ovládacího prvku pro výběr data a času, který je nutný k zobrazení aktuálního data nebo času.|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Načte barvu pro danou část měsíčního kalendáře v rámci ovládacího prvku výběru data a času.|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Načte `CMonthCalCtrl` objekt přidružený k ovládacímu prvku výběru data a času.|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Načte písmo aktuálně používané ovládacího prvku pro výběr data a času podřízeného měsíčního kalendářního ovládacího prvku.|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Získá styl aktuální ho ovládacího prvku pro výběr data a času.|
|[CDateTimeCtrl::GetRange](#getrange)|Načte aktuální minimální a maximální povolené systémové časy pro ovládací prvek výběru data a času.|
|[CDateTimeCtrl::GetTime](#gettime)|Načte aktuálně vybraný čas z ovládacího prvku výběru data `SYSTEMTIME` a času a vloží jej do zadané struktury.|
|[CDateTimeCtrl::SetFormat](#setformat)|Nastaví zobrazení ovládacího prvku pro výběr data a času v souladu s daným formátovacím řetězcem.|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Nastaví barvu pro danou část měsíčního kalendáře v rámci ovládacího prvku výběru data a času.|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Nastaví písmo, které bude používat ovládací prvek kalendáře podřízeného měsíce ovládacího prvku pro výběr data a času.|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Nastaví styl aktuálního ovládacího prvku pro výběr data a času.|
|[CDateTimeCtrl::SetRange](#setrange)|Nastaví minimální a maximální povolené systémové časy pro ovládací prvek výběru data a času.|
|[CDateTimeCtrl::SetTime](#settime)|Nastaví čas v ovládacím prvku výběru data a času.|

## <a name="remarks"></a>Poznámky

Ovládací prvek výběru data a času (dtp ovládací prvek) poskytuje jednoduché rozhraní pro výměnu informací o datu a čase s uživatelem. Toto rozhraní obsahuje pole, z nichž každé zobrazuje část informací o datu a čase uložených v ovládacím prvku. Uživatel může změnit informace uložené v ovládacím prvku změnou obsahu řetězce v daném poli. Uživatel může přejít z pole do pole pomocí myši nebo klávesnice.

Ovládací prvek výběru data a času můžete přizpůsobit použitím různých stylů na objekt při jeho vytváření. Další informace o stylech specifických pro ovládací prvek výběru data a času v části Styly výběru dat a času v části Windows SDK naleznete v tématu [Styly](/windows/win32/Controls/date-and-time-picker-control-styles) ovládacího prvku výběr u data a času. Formát zobrazení ovládacího prvku DTP můžete nastavit pomocí stylů formátu. Tyto styly formátu jsou popsány v části Styly formátu v tématu Sady Windows [Datum a Styly ovládacího prvku výběr u času](/windows/win32/Controls/date-and-time-picker-control-styles).

Ovládací prvek pro výběr data a času také používá oznámení a zpětná volání, které jsou popsány v [části Použití CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdtctl.h

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl

Vytvoří `CDateTimeCtrl` objekt.

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a>CDateTimeCtrl::ZavřítMonthCal

Zavře aktuální ovládací prvek pro výběr data a času.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu DTM_CLOSEMONTHCAL,](/windows/win32/Controls/dtm-closemonthcal) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou *m_dateTimeCtrl*, která se používá k programovému přístupu k ovládacímu prvku výběru data a času. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zavře rozevírací kalendář pro aktuální ovládací prvek pro výběr data a času.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a>CDateTimeCtrl::Vytvořit

Vytvoří ovládací prvek pro výběr data a `CDateTimeCtrl` času a připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje kombinaci stylů časového řízení. Další informace o stylech výběru data a času v části Windows SDK naleznete v [tématu Styly ovládacího prvku](/windows/win32/Controls/date-and-time-picker-control-styles) výběru data a času v sadě Windows SDK.

*Rect*<br/>
Odkaz na [rect](/previous-versions/dd162897\(v=vs.85\)) struktury, což je umístění a velikost ovládacího prvku výběr u data a času.

*pParentWnd*<br/>
Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku pro výběr data a času. Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku ovládacího prvku pro výběr data a času.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo vytvoření úspěšné; jinak 0.

### <a name="remarks"></a>Poznámky

##### <a name="to-create-a-date-and-time-picker-control"></a>Vytvoření ovládacího prvku pro výběr data a času

1. Volání [CDateTimeCtrl](#cdatetimectrl) k `CDateTimeCtrl` vytvoření objektu.

1. Volání této členské funkce, která vytvoří ovládací prvek výběr u `CDateTimeCtrl` data a času systému Windows a připojí jej k objektu.

Při volání `Create`jsou inicializovány běžné ovládací prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo

Načte informace o aktuálním ovládacím prvku výběru data a času.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pDateTimePickerInfo*|[out] Ukazatel na strukturu [DATETIMEPICKERINFO,](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) která obdrží popis aktuálního ovládacího prvku pro výběr data a času.<br /><br /> Volající je zodpovědný za přidělení této struktury. Tato metoda však inicializuje *cbSize* člen struktury.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu DTM_GETDATETIMEPICKERINFO,](/windows/win32/Controls/dtm-getdatetimepickerinfo) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou *m_dateTimeCtrl*, která se používá k programovému přístupu k ovládacímu prvku výběru data a času. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu označuje, zda úspěšně načte informace o aktuálním ovládacím prvku pro výběr data a času.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor

Načte barvu pro danou část měsíčního kalendáře v rámci ovládacího prvku výběru data a času.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parametry

*iBarva*<br/>
Hodnota **int** určující, kterou barevnou oblast měsíčního kalendáře má být načtena. Seznam hodnot naleznete v parametru *iColor* pro [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF, která představuje nastavení barev pro zadanou část ovládacího prvku kalendáře měsíce, pokud je úspěšná. Funkce vrátí hodnotu -1, pokud není úspěšná.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/dtm-getmccolor)Win32 DTM_GETMCCOLOR , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a>CDateTimeCtrl::GetMonthCalCtrl

Načte `CMonthCalCtrl` objekt přidružený k ovládacímu prvku výběru data a času.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) objekt u null, pokud neúspěšné nebo pokud okno není viditelné.

### <a name="remarks"></a>Poznámky

Ovládací prvky pro výběr data a času vytvoří ovládací prvek kalendáře podřízeného měsíce, když uživatel klikne na šipku rozevíracího seznamu. Pokud `CMonthCalCtrl` objekt již není potřeba, je zničen, takže aplikace nesmí spoléhat na uložení objektu představující kalendář podřízeného měsíce ovládacího prvku pro výběr data.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont

Získá písmo aktuálně používané ovládacího prvku měsíc měsíc měsíc ovládacího prvku data a času.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [cfont](../../mfc/reference/cfont-class.md) objekt nebo NULL, pokud neúspěšné.

### <a name="remarks"></a>Poznámky

Objekt, `CFont` na který se vztahuje vrácená hodnota, je dočasný objekt a je zničen během další doby zpracování nečinnosti.

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle

Získá styl ovládacího prvku kalendáře rozevíracího seznamu měsíc, který je přidružen k aktuálnímu ovládacímu prvku pro výběr data a času.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Styl ovládacího prvku kalendáře rozevíracího seznamu měsíců, což je bitová kombinace (OR) stylů ovládacího prvku výběru data a času. Další informace naleznete v tématu [Styly ovládacího prvku kalendář měsíce](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu DTM_GETMCSTYLE,](/windows/win32/Controls/dtm-getmcstyle) která je popsána v sadě Windows SDK.

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a>CDateTimeCtrl::GetRange

Načte aktuální minimální a maximální povolené systémové časy pro ovládací prvek výběru data a času.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>Parametry

*pMinRange*<br/>
Ukazatel na [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující nejbližší `CDateTimeCtrl` čas povolený v objektu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objekt nebo `CTime` objekt obsahující poslední čas `CDateTimeCtrl` povolený v objektu.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD obsahující příznaky, které označují, které rozsahy jsou nastaveny. Pokud uživatel

`return value & GDTR_MAX`== 0

pak je platný druhý parametr. Podobně, pokud

`return value & GDTR_MIN`== 0

pak je platný první parametr.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)zprávy Win32 , jak je popsáno v sadě Windows SDK. V implementaci knihovny MFC můžete `COleDateTime` `CTime` zadat buď nebo použití.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a>CDateTimeCtrl::GetTime

Načte aktuálně vybraný čas z ovládacího prvku výběru data `SYSTEMTIME` a času a vloží jej do zadané struktury.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
V první verzi odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obdrží informace o systémovém čase. Ve druhé verzi odkaz na [ctime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obdrží informace o systémovém čase.

*pTimeDest*<br/>
Ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu přijímat informace o systémovém čase. Nesmí být null.

### <a name="return-value"></a>Návratová hodnota

V první verzi nenulová, pokud je čas `COleDateTime` úspěšně zapsán do objektu; jinak 0. Ve druhé a třetí verzi dword hodnotu rovnající se *dwFlag* člen nastavit ve struktuře [NMDATETIMECHANGE.](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) Další informace naleznete v části **Poznámky** níže.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/dtm-getsystemtime)Win32 DTM_GETSYSTEMTIME , jak je popsáno v sadě Windows SDK. V implementaci knihovny `GetTime`MFC `COleDateTime` můžete `CTime` použít nebo třídy `SYSTEMTIME` nebo můžete použít strukturu k uložení informací o čase.

Vrácená hodnota DWORD ve druhé a třetí verzi výše označuje, zda je ovládací prvek výběru data a času nastaven na stav "no date", jak je uvedeno v členu struktury *DWFlags* [.](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) Pokud se vrácená hodnota rovná GDT_NONE, je ovládací prvek nastaven na stav "žádné datum" a používá styl DTS_SHOWNONE. Pokud se vrácená hodnota rovná GDT_VALID, systémový čas je úspěšně uložen v cílovém umístění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize

Vrátí ideální velikost ovládacího prvku pro výběr data a času, který je nutný k zobrazení aktuálního data nebo času.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pvelikost*|[out] Ukazatel na [size](/windows/win32/api/windef/ns-windef-size) strukturu, která obsahuje ideální velikost pro ovládací prvek.|

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je vždy TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu DTM_GETIDEALSIZE,](/windows/win32/Controls/dtm-getidealsize) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou *m_dateTimeCtrl*, která se používá k programovému přístupu k ovládacímu prvku výběru data a času. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu načte ideální velikost pro zobrazení ovládacího prvku výběru data a času.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a>CDateTimeCtrl::SetFormat

Nastaví zobrazení ovládacího prvku pro výběr data a času v souladu s daným formátovacím řetězcem.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parametry

*pstrFormat*<br/>
Ukazatel na formátovací řetězec s nulovým ukončením, který definuje požadované zobrazení. Nastavením tohoto parametru na hodnotu NULL se obnoví výchozí formátovací řetězec pro aktuální styl.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

> [!NOTE]
> Vstup uživatele neurčuje úspěch nebo neúspěch pro toto volání.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)zprávy Win32 , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor

Nastaví barvu pro danou část měsíčního kalendáře v rámci ovládacího prvku výběru data a času.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parametry

*iBarva*<br/>
**int** hodnotu určující, kterou oblast ovládacího prvku kalendáře měsíce nastavit. Tato hodnota může být jedna z následujících.

|Hodnota|Význam|
|-----------|-------------|
|MCSC_BACKGROUND|Nastavte barvu pozadí zobrazenou mezi měsíci.|
|MCSC_MONTHBK|Nastavte barvu pozadí zobrazenou do měsíce.|
|MCSC_TEXT|Nastavte barvu použitou k zobrazení textu do jednoho měsíce.|
|MCSC_TITLEBK|Nastavte barvu pozadí zobrazenou v názvu kalendáře.|
|MCSC_TITLETEXT|Nastavte barvu použitou k zobrazení textu v názvu kalendáře.|
|MCSC_TRAILINGTEXT|Nastavte barvu použitou k zobrazení textu záhlaví a koncového dne. Dny záhlaví a koncové dny jsou dny z předchozích a následujících měsíců, které se zobrazují v aktuálním kalendáři.|

*ref*<br/>
Hodnota COLORREF představující barvu, která bude nastavena pro zadanou oblast měsíčního kalendáře.

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF, která představuje předchozí nastavení barev pro zadanou část ovládacího prvku kalendáře měsíce, pokud je úspěšná. V opačném případě vrátí zpráva -1.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/dtm-setmccolor)Win32 DTM_SETMCCOLOR , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [cdatetimectrl::GetMonthCalColor](#getmonthcalcolor).

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a>CDateTimeCtrl::SetMonthCalFont

Nastaví písmo, které bude používat ovládací prvek kalendáře podřízeného měsíce ovládacího prvku pro výběr data a času.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*hPísmo*<br/>
Zpracovat písmo, které bude nastaveno.

*bPřekreslit*<br/>
Určuje, zda má být ovládací prvek překreslen okamžitě po nastavení písma. Nastavení tohoto parametru na hodnotu TRUE způsobí, že ovládací prvek překreslí sám.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)zprávy Win32 , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> Pokud použijete tento kód, budete chtít, aby `CDialog`člen vaší odvozené `CFont`třídy s názvem *m_MonthFont* typu .

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle

Nastaví styl ovládacího prvku kalendáře rozevíracího seznamu měsíců, který je přidružen k aktuálnímu ovládacímu prvku pro výběr data a času.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwStyl*|[v] Nový styl ovládacího prvku kalendáře měsíce, což je bitová kombinace (OR) stylů ovládacího prvku kalendáře měsíce. Další informace naleznete v tématu [Styly ovládacího prvku kalendář měsíce](/windows/win32/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Předchozí styl ovládacího prvku kalendáře rozevíracího seznamu měsíců.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu DTM_SETMCSTYLE,](/windows/win32/Controls/dtm-setmcstyle) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou *m_dateTimeCtrl*, která se používá k programovému přístupu k ovládacímu prvku výběru data a času. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví ovládací prvek výběru data a času tak, aby zobrazoval čísla týdnů, zkrácené názvy dnů v týdnu a žádný indikátor dnešního dne.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a>CDateTimeCtrl::SetRange

Nastaví minimální a maximální povolené systémové časy pro ovládací prvek výběru data a času.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>Parametry

*pMinRange*<br/>
Ukazatel na [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující nejbližší `CDateTimeCtrl` čas povolený v objektu.

*pMaxRange*<br/>
Ukazatel na `COleDateTime` objekt nebo `CTime` objekt obsahující poslední čas `CDateTimeCtrl` povolený v objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/dtm-setrange)Win32 DTM_SETRANGE , jak je popsáno v sadě Windows SDK. V implementaci knihovny MFC můžete `COleDateTime` `CTime` zadat buď nebo použití. Pokud `COleDateTime` má objekt stav NULL, bude oblast odebrána. Pokud `CTime` je ukazatel `COleDateTime` nebo ukazatel NULL, rozsah bude odebrán.

### <a name="example"></a>Příklad

  Viz příklad pro [CDateTimeCtrl::GetRange](#getrange).

## <a name="cdatetimectrlsettime"></a><a name="settime"></a>CDateTimeCtrl::SetTime

Nastaví čas v ovládacím prvku výběru data a času.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parametry

*timeNew*<br/>
Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující, na které bude nastaven ovládací prvek.

*pTimeNew*<br/>
Ve druhé verzi výše ukazatel na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující čas, na který bude nastaven ovládací prvek. Ve třetí verzi výše ukazatel na [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) struktury obsahující čas, na který bude nastaven ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/dtm-setsystemtime)Win32 DTM_SETSYSTEMTIME , jak je popsáno v sadě Windows SDK. V implementaci knihovny `SetTime`MFC můžete `COleDateTime` `CTime` použít třídy or `SYSTEMTIME` nebo můžete použít strukturu k nastavení informací o čase.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)
