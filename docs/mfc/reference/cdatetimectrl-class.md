---
title: Atributu CDateTimeCtrl – třída
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
ms.openlocfilehash: ec9060ba60c4d9877e5ee32bc68da0134f0ccf20
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866931"
---
# <a name="cdatetimectrl-class"></a>Atributu CDateTimeCtrl – třída

Zapouzdřuje funkce ovládacího prvku pro výběr data a času.

## <a name="syntax"></a>Syntaxe

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Atributu CDateTimeCtrl:: atributu CDateTimeCtrl](#cdatetimectrl)|Vytvoří objekt `CDateTimeCtrl`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Atributu CDateTimeCtrl:: CloseMonthCal](#closemonthcal)|Zavře aktuální ovládací prvek pro výběr data a času.|
|[Atributu CDateTimeCtrl:: Create](#create)|Vytvoří ovládací prvek pro výběr data a času a připojí ho k objektu `CDateTimeCtrl`.|
|[Atributu CDateTimeCtrl:: GetDateTimePickerInfo](#getdatetimepickerinfo)|Načte informace o aktuálním ovládacím prvku pro výběr data a času.|
|[Atributu CDateTimeCtrl:: GetIdealSize](#getidealsize)|Vrátí ideální velikost ovládacího prvku pro výběr data a času, který je požadován k zobrazení aktuálního data nebo času.|
|[Atributu CDateTimeCtrl:: GetMonthCalColor](#getmonthcalcolor)|Načte barvu pro danou část měsíčního kalendáře v rámci ovládacího prvku pro výběr data a času.|
|[Atributu CDateTimeCtrl:: GetMonthCalCtrl](#getmonthcalctrl)|Načte objekt `CMonthCalCtrl` přidružený k ovládacímu prvku pro výběr data a času.|
|[Atributu CDateTimeCtrl:: GetMonthCalFont](#getmonthcalfont)|Načte písmo, které je aktuálně použito ovládacím prvkem pro výběr data a času v ovládacím prvku měsíční kalendář.|
|[Atributu CDateTimeCtrl:: GetMonthCalStyle](#getmonthcalstyle)|Získá styl aktuálního ovládacího prvku pro výběr data a času.|
|[Atributu CDateTimeCtrl:: GetRange](#getrange)|Načte aktuální minimální a maximální povolené systémové časy pro ovládací prvek pro výběr data a času.|
|[Atributu CDateTimeCtrl:: GetTime](#gettime)|Načte aktuálně vybraný čas z ovládacího prvku pro výběr data a času a umístí jej do zadané struktury `SYSTEMTIME`.|
|[Atributu CDateTimeCtrl:: SetFormat](#setformat)|Nastaví zobrazení ovládacího prvku pro výběr data a času v souladu s daným formátovacím řetězcem.|
|[Atributu CDateTimeCtrl:: SetMonthCalColor](#setmonthcalcolor)|Nastaví barvu pro danou část měsíčního kalendáře v rámci ovládacího prvku pro výběr data a času.|
|[Atributu CDateTimeCtrl:: SetMonthCalFont](#setmonthcalfont)|Nastaví písmo, které bude používat ovládací prvek měsíčního kalendáře ovládacího prvku pro výběr data a času.|
|[Atributu CDateTimeCtrl:: SetMonthCalStyle](#setmonthcalstyle)|Nastaví styl aktuálního ovládacího prvku pro výběr data a času.|
|[Atributu CDateTimeCtrl:: SetRange](#setrange)|Nastaví minimální a maximální povolené systémové časy pro ovládací prvek pro výběr data a času.|
|[Atributu CDateTimeCtrl:: SetTime –](#settime)|Nastaví čas v ovládacím prvku pro výběr data a času.|

## <a name="remarks"></a>Poznámky

Ovládací prvek pro výběr data a času (ovládací prvek DTP) poskytuje jednoduché rozhraní pro výměnu informací o datu a času s uživatelem. Toto rozhraní obsahuje pole, z nichž každý zobrazuje část informací o datu a čase uložených v ovládacím prvku. Uživatel může změnit informace uložené v ovládacím prvku změnou obsahu řetězce v daném poli. Uživatel může přejít z pole do pole pomocí myši nebo klávesnice.

Můžete přizpůsobit ovládací prvek pro výběr data a času použitím nejrůznějších stylů objektu při jeho vytváření. Další informace o stylech specifických pro ovládací prvek pro výběr data a času naleznete v tématu [styly ovládacích prvků pro výběr data a času](/windows/win32/Controls/date-and-time-picker-control-styles) v Windows SDK. Můžete nastavit formát zobrazení ovládacího prvku DTP pomocí stylů formátu. Tyto styly formátu jsou popsané v části "styly formátu" ve [stylu ovládacího prvku pro výběr data a času](/windows/win32/Controls/date-and-time-picker-control-styles)v tématu Windows SDK.

Ovládací prvek pro výběr data a času používá také oznámení a zpětná volání, která jsou popsána v tématu [using atributu CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDTCTL. h

##  <a name="cdatetimectrl"></a>Atributu CDateTimeCtrl:: atributu CDateTimeCtrl

Vytvoří objekt `CDateTimeCtrl`.

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>Atributu CDateTimeCtrl:: CloseMonthCal

Zavře aktuální ovládací prvek pro výběr data a času.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_dateTimeCtrl*, která se používá pro programový přístup k ovládacímu prvku pro výběr data a času. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zavírá rozevírací kalendář pro aktuální ovládací prvek pro výběr data a času.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>Atributu CDateTimeCtrl:: Create

Vytvoří ovládací prvek pro výběr data a času a připojí ho k objektu `CDateTimeCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje kombinaci stylů ovládacího prvku data a času. Další informace o stylech výběru data a času naleznete v tématu [styly ovládacích prvků pro výběr data a času](/windows/win32/Controls/date-and-time-picker-control-styles) v Windows SDK.

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , což je pozice a velikost ovládacího prvku pro výběr data a času.

*pParentWnd*<br/>
Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je nadřazené okno ovládacího prvku pro výběr data a času. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku pro výběr data a času.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo vytváření úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

##### <a name="to-create-a-date-and-time-picker-control"></a>Vytvoření ovládacího prvku pro výběr data a času

1. Voláním [atributu CDateTimeCtrl](#cdatetimectrl) vytvořte objekt `CDateTimeCtrl`.

1. Zavolejte tuto členskou funkci, která vytvoří ovládací prvek pro výběr data a času v systému Windows a připojí ho k objektu `CDateTimeCtrl`.

Při volání `Create`jsou inicializovány běžné ovládací prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>Atributu CDateTimeCtrl:: GetDateTimePickerInfo

Načte informace o aktuálním ovládacím prvku pro výběr data a času.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pDateTimePickerInfo*|mimo Ukazatel na strukturu [DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) , která přijímá popis aktuálního ovládacího prvku pro výběr data a času.<br /><br /> Volající je zodpovědný za přidělování této struktury. Tato metoda však inicializuje člen *cbSize* struktury.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_dateTimeCtrl*, která se používá pro programový přístup k ovládacímu prvku pro výběr data a času. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu označuje, zda úspěšně načte informace o aktuálním ovládacím prvku pro výběr data a času.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>Atributu CDateTimeCtrl:: GetMonthCalColor

Načte barvu pro danou část měsíčního kalendáře v rámci ovládacího prvku pro výběr data a času.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parametry

*iColor*<br/>
Hodnota typu **int** určující, která barevná oblast měsíčního kalendáře má být načtena. Seznam hodnot naleznete v parametru *iColor* pro [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF, která představuje nastavení barvy pro zadanou část ovládacího prvku měsíční kalendář, pokud je úspěšná. Funkce vrátí hodnotu-1, pokud je neúspěšná.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>Atributu CDateTimeCtrl:: GetMonthCalCtrl

Načte objekt `CMonthCalCtrl` přidružený k ovládacímu prvku pro výběr data a času.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [atributu CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) nebo hodnota null, pokud je neúspěšná, nebo pokud není okno viditelné.

### <a name="remarks"></a>Poznámky

Ovládací prvky pro výběr data a času vytvoří podřízený ovládací prvek měsíčního kalendáře, když uživatel klikne na šipku rozevíracího seznamu. Když objekt `CMonthCalCtrl` již není potřeba, je zničen, takže aplikace nesmí spoléhat na uložení objektu představujícího měsíc podřízeného kalendáře ovládacího prvku Výběr data a času.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>Atributu CDateTimeCtrl:: GetMonthCalFont

Načte písmo aktuálně používané ovládacím prvkem měsíční kalendář pro výběr data a času.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CFont –](../../mfc/reference/cfont-class.md) nebo hodnota null, pokud je neúspěšná.

### <a name="remarks"></a>Poznámky

Objekt `CFont` odkazoval návratovou hodnotou je dočasný objekt a je zničen během příštího nečinného času zpracování.

##  <a name="getmonthcalstyle"></a>Atributu CDateTimeCtrl:: GetMonthCalStyle

Získá styl ovládacího prvku kalendáře s rozevíracím seznamem, který je přidružen k aktuálnímu ovládacímu prvku pro výběr data a času.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Styl ovládacího prvku kalendáře pro rozevírací seznam měsíce, což je bitová kombinace stylů ovládacího prvku pro výběr data a času. Další informace naleznete v tématu [styly ovládacího prvku měsíční kalendář](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle) , která je popsána v Windows SDK.

##  <a name="getrange"></a>Atributu CDateTimeCtrl:: GetRange

Načte aktuální minimální a maximální povolené systémové časy pro ovládací prvek pro výběr data a času.

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
Ukazatel na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který obsahuje Nejdřívější čas povolený v objektu `CDateTimeCtrl`.

*pMaxRange*<br/>
Ukazatel na objekt `COleDateTime` nebo objekt `CTime` obsahující nejnovější čas povolený v objektu `CDateTimeCtrl`.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD obsahující příznaky, které označují, které rozsahy jsou nastaveny. Pokud uživatel

`return value & GDTR_MAX` = = 0

pak je druhý parametr platný. Podobně, pokud

`return value & GDTR_MIN` = = 0

pak je první parametr platný.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange), jak je popsáno v Windows SDK. V implementaci knihovny MFC můžete zadat buď `COleDateTime`, nebo `CTime` použití.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>Atributu CDateTimeCtrl:: GetTime

Načte aktuálně vybraný čas z ovládacího prvku pro výběr data a času a umístí jej do zadané struktury `SYSTEMTIME`.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*Časově omezená*<br/>
V první verzi odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , který obdrží informace o čase systému. Ve druhé verzi odkaz na objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který obdrží informace o čase systému.

*pTimeDest*<br/>
Ukazatel na strukturu [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , který obdrží informace o čase systému. Nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

V první verzi, nenulové, pokud je čas úspěšně zapsán do objektu `COleDateTime`; v opačném případě 0. Ve druhé a třetí verzi se hodnota DWORD rovná sadě členů *dwFlag* ve struktuře [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) . Další informace najdete níže v části s **poznámkami** .

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime), jak je popsáno v Windows SDK. V implementaci knihovny MFC `GetTime`lze použít třídy `COleDateTime` nebo `CTime`, případně můžete použít strukturu `SYSTEMTIME` k uložení informací o času.

Návratová hodnota DWORD v druhé a třetí verzi (výše) označuje, zda je ovládací prvek pro výběr data a času nastaven na stav "bez data", jak je uvedeno v členu struktury [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) *dwFlags*. Pokud se hodnota vrátí GDT_NONE, je ovládací prvek nastaven na hodnotu "bez data" a používá DTS_SHOWNONE styl. Pokud se hodnota vrátila jako GDT_VALID, je systémový čas úspěšně uložen do cílového umístění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>Atributu CDateTimeCtrl:: GetIdealSize

Vrátí ideální velikost ovládacího prvku pro výběr data a času, který je požadován k zobrazení aktuálního data nebo času.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*psize*|mimo Ukazatel na strukturu [velikosti](/windows/win32/api/windef/ns-windef-size) , která obsahuje ideální velikost ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je vždycky TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_dateTimeCtrl*, která se používá pro programový přístup k ovládacímu prvku pro výběr data a času. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu načte ideální velikost pro zobrazení ovládacího prvku pro výběr data a času.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>Atributu CDateTimeCtrl:: SetFormat

Nastaví zobrazení ovládacího prvku pro výběr data a času v souladu s daným formátovacím řetězcem.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parametry

*pstrFormat*<br/>
Ukazatel na řetězec formátu zakončený nulou, který definuje požadovaný displej. Nastavením tohoto parametru na hodnotu NULL dojde k resetování ovládacího prvku na výchozí formátovací řetězec pro aktuální styl.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

> [!NOTE]
>  Uživatelský vstup neurčuje úspěch nebo neúspěch tohoto volání.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>Atributu CDateTimeCtrl:: SetMonthCalColor

Nastaví barvu pro danou část měsíčního kalendáře v rámci ovládacího prvku pro výběr data a času.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parametry

*iColor*<br/>
hodnota typu **int** určující, která oblast ovládacího prvku měsíční kalendář se má nastavit. Tato hodnota může být jedna z následujících.

|Hodnota|Význam|
|-----------|-------------|
|MCSC_BACKGROUND|Nastaví barvu pozadí zobrazenou mezi měsíci.|
|MCSC_MONTHBK|Nastaví barvu pozadí zobrazenou v rámci měsíce.|
|MCSC_TEXT|Nastaví barvu použitou k zobrazení textu v rámci měsíce.|
|MCSC_TITLEBK|Nastaví barvu pozadí zobrazenou v nadpisu kalendáře.|
|MCSC_TITLETEXT|Nastaví barvu použitou k zobrazení textu v nadpisu kalendáře.|
|MCSC_TRAILINGTEXT|Nastaví barvu použitou k zobrazení záhlaví a koncového textu. Záhlaví a koncové dny jsou dny z předchozích a následujících měsíců, které se zobrazí v aktuálním kalendáři.|

*ref*<br/>
Hodnota COLORREF představující barvu, která bude nastavena pro zadanou oblast měsíčního kalendáře.

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF, která představuje předchozí nastavení barvy pro zadanou část ovládacího prvku měsíční kalendář, pokud je úspěšná. V opačném případě se zpráva vrátí-1.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CDateTimeCtrl:: GetMonthCalColor](#getmonthcalcolor).

##  <a name="setmonthcalfont"></a>Atributu CDateTimeCtrl:: SetMonthCalFont

Nastaví písmo, které bude používat ovládací prvek měsíčního kalendáře ovládacího prvku pro výběr data a času.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*hFont*<br/>
Pořídí písmo, které bude nastaveno.

*bRedraw*<br/>
Určuje, zda má být ovládací prvek překreslen ihned po nastavení písma. Nastavením tohoto parametru na hodnotu TRUE dojde k tomu, že ovládací prvek překreslí sám sebe.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  Použijete-li tento kód, budete chtít vytvořit člena vaší `CDialog`odvozené třídy nazvané *m_MonthFont* typu `CFont`.

##  <a name="setmonthcalstyle"></a>Atributu CDateTimeCtrl:: SetMonthCalStyle

Nastaví styl ovládacího prvku kalendáře s rozevíracími čárkami, který je přidružen k aktuálnímu ovládacímu prvku pro výběr data a času.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwStyle*|pro Nový styl ovládacího prvku měsíční kalendář, což je bitová kombinace stylů ovládacího prvku měsíčního kalendáře. Další informace naleznete v tématu [styly ovládacího prvku měsíční kalendář](/windows/win32/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Předchozí styl ovládacího prvku kalendáře pro místní měsíc

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_dateTimeCtrl*, která se používá pro programový přístup k ovládacímu prvku pro výběr data a času. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví ovládací prvek pro výběr data a času pro zobrazení čísel týdnů, zkrácených názvů dní v týdnu a indikátoru dnešního dne.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>Atributu CDateTimeCtrl:: SetRange

Nastaví minimální a maximální povolené systémové časy pro ovládací prvek pro výběr data a času.

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
Ukazatel na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který obsahuje Nejdřívější čas povolený v objektu `CDateTimeCtrl`.

*pMaxRange*<br/>
Ukazatel na objekt `COleDateTime` nebo objekt `CTime` obsahující nejnovější čas povolený v objektu `CDateTimeCtrl`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange), jak je popsáno v Windows SDK. V implementaci knihovny MFC můžete zadat buď `COleDateTime`, nebo `CTime` použití. Pokud má objekt `COleDateTime` stav NULL, rozsah bude odstraněn. Pokud je ukazatel `CTime` nebo ukazatel `COleDateTime` NULL, rozsah se odebere.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CDateTimeCtrl:: GetRange](#getrange).

##  <a name="settime"></a>Atributu CDateTimeCtrl:: SetTime –

Nastaví čas v ovládacím prvku pro výběr data a času.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parametry

*timeNew*<br/>
Odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obsahující, na který bude ovládací prvek nastaven.

*pTimeNew*<br/>
Ve druhé verzi výše je ukazatel na objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) obsahující čas, na který bude ovládací prvek nastaven. Ve třetí verzi výše je ukazatel na strukturu [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) obsahující čas, do kterého bude ovládací prvek nastaven.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime), jak je popsáno v Windows SDK. V implementaci knihovny MFC `SetTime`lze použít třídy `COleDateTime` nebo `CTime`, případně můžete použít strukturu `SYSTEMTIME` k nastavení časových údajů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Viz také

[CMNCTRL1 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl – třída](../../mfc/reference/cmonthcalctrl-class.md)
