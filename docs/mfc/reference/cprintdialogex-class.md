---
title: CPrintDialogEx – třída
ms.date: 11/04/2016
f1_keywords:
- CPrintDialogEx
- AFXDLGS/CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CreatePrinterDC
- AFXDLGS/CPrintDialogEx::DoModal
- AFXDLGS/CPrintDialogEx::GetCopies
- AFXDLGS/CPrintDialogEx::GetDefaults
- AFXDLGS/CPrintDialogEx::GetDeviceName
- AFXDLGS/CPrintDialogEx::GetDevMode
- AFXDLGS/CPrintDialogEx::GetDriverName
- AFXDLGS/CPrintDialogEx::GetPortName
- AFXDLGS/CPrintDialogEx::GetPrinterDC
- AFXDLGS/CPrintDialogEx::PrintAll
- AFXDLGS/CPrintDialogEx::PrintCollate
- AFXDLGS/CPrintDialogEx::PrintCurrentPage
- AFXDLGS/CPrintDialogEx::PrintRange
- AFXDLGS/CPrintDialogEx::PrintSelection
- AFXDLGS/CPrintDialogEx::m_pdex
helpviewer_keywords:
- CPrintDialogEx [MFC], CPrintDialogEx
- CPrintDialogEx [MFC], CreatePrinterDC
- CPrintDialogEx [MFC], DoModal
- CPrintDialogEx [MFC], GetCopies
- CPrintDialogEx [MFC], GetDefaults
- CPrintDialogEx [MFC], GetDeviceName
- CPrintDialogEx [MFC], GetDevMode
- CPrintDialogEx [MFC], GetDriverName
- CPrintDialogEx [MFC], GetPortName
- CPrintDialogEx [MFC], GetPrinterDC
- CPrintDialogEx [MFC], PrintAll
- CPrintDialogEx [MFC], PrintCollate
- CPrintDialogEx [MFC], PrintCurrentPage
- CPrintDialogEx [MFC], PrintRange
- CPrintDialogEx [MFC], PrintSelection
- CPrintDialogEx [MFC], m_pdex
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
ms.openlocfilehash: 52e992cf021a592198daeddf0a4321fcea487f72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364031"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx – třída

Zapouzdřuje služby poskytované listem vlastností Windows Print.

## <a name="syntax"></a>Syntaxe

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|Vytvoří `CPrintDialogEx` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPrintDialogEx::VytvořitprinterDC](#createprinterdc)|Vytvoří kontext zařízení tiskárny bez zobrazení tiskového dialogového okna.|
|[CPrintDialogEx::DoModální](#domodal)|Zobrazí dialogové okno a umožní uživateli provádět výběry.|
|[CPrintDialogEx::GetCopies](#getcopies)|Načte počet požadovaných kopií.|
|[CPrintDialogEx::GetDefaults](#getdefaults)|Načte výchozí hodnoty zařízení bez zobrazení dialogového okna.|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Načte název aktuálně vybraného tiskového zařízení.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|Načte `DEVMODE` strukturu.|
|[CPrintDialogex::GetDriverName](#getdrivername)|Načte název systémově definovaného ovladače zařízení tiskárny.|
|[CPrintDialogex::GetPortName](#getportname)|Načte název aktuálně vybraného portu tiskárny.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Načte popisovač do kontextu zařízení tiskárny.|
|[CPrintDialogEx::PrintAll](#printall)|Určuje, zda se mají vytisknout všechny stránky dokumentu.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Určuje, zda jsou požadovány kompletované kopie.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Určuje, zda se má vytisknout aktuální stránka dokumentu.|
|[CPrintDialogEx::PrintRange](#printrange)|Určuje, zda se má vytisknout pouze zadaný rozsah stránek.|
|[CPrintDialogEx::PrintSelection](#printselection)|Určuje, zda se mají vytisknout pouze aktuálně vybrané položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|Struktura slouží k `CPrintDialogEx` přizpůsobení objektu.|

## <a name="remarks"></a>Poznámky

Můžete se spolehnout na rozhraní pro zpracování mnoha aspektů procesu tisku pro vaši aplikaci. Další informace o použití rozhraní pro zpracování tiskových úloh naleznete v článku [Tisk](../../mfc/printing.md).

Pokud chcete, aby vaše aplikace zpracovávat tisk bez zapojení `CPrintDialogEx` rámci, můžete použít třídu "tak, jak je" s `CPrintDialogEx` konstruktorem k dispozici, nebo můžete odvodit vlastní dialog třídy z a napsat konstruktor, aby vyhovoval vašim potřebám. V obou případech se tato dialogová okna budou chovat jako standardní `CCommonDialog`dialogová okna knihovny MFC, protože jsou odvozena z třídy .

Chcete-li `CPrintDialogEx` použít objekt, nejprve `CPrintDialogEx` vytvořte objekt pomocí konstruktoru. Po vytvoření dialogového okna můžete nastavit nebo upravit libovolné hodnoty ve struktuře [m_pdex](#m_pdex) a inicializovat hodnoty ovládacích prvků dialogového okna. Struktura `m_pdex` je typu [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw). Další informace o této struktuře naleznete v souboru Windows SDK.

Pokud nezadáte vlastní popisovače `m_pdex` pro `hDevMode` členy `hDevNames` a, nezapomeňte volat funkci `GlobalFree` systému Windows pro tyto popisovače, když budete hotovi s dialogovým oknem.

Po inicializaci ovládacích `DoModal` prvků dialogového okna zavolejte členské funkce, aby zobrazila dialogové okno a umožnila uživateli vybrat možnosti tisku. Když `DoModal` se vrátí, můžete určit, zda uživatel vybral tlačítko OK, Použít nebo Storno.

Pokud uživatel stiskl tlačítko OK, můžete použít `CPrintDialogEx`členské funkce aplikace k načtení informací, které uživatel zadá.

Členská `CPrintDialogEx::GetDefaults` funkce je užitečná pro načítání aktuálních výchozích hodnot tiskárny bez zobrazení dialogového okna. Tato metoda nevyžaduje žádnou interakci uživatele.

Pomocí funkce systému Windows `CommDlgExtendedError` můžete určit, zda došlo k chybě během inicializace dialogového okna a získat další informace o chybě. Další informace o této funkci naleznete v souboru Windows SDK.

Další informace o `CPrintDialogEx`použití naleznete v [tématu Common Dialog Classes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="cprintdialogexcprintdialogex"></a><a name="cprintdialogex"></a>CPrintDialogEx::CPrintDialogEx

Vytvoří seznam vlastností Windows Print.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Jeden nebo více příznaků, které můžete použít k přizpůsobení nastavení dialogového okna, kombinované pomocí bitového operátoru OR. Například příznak PD_ALLPAGES nastaví výchozí rozsah tisku na všechny stránky dokumentu. Další informace o těchto příznaky naleznete ve struktuře [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) v ksouboru Windows SDK.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastníjméno okna dialogového okna.

### <a name="remarks"></a>Poznámky

Tato členská funkce pouze vytvoří objekt. Dialogové `DoModal` okno se zobrazí pomocí členské funkce.

## <a name="cprintdialogexcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialogEx::VytvořitprinterDC

Vytvoří kontext zařízení tiskárny (DC) ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Návratová hodnota

Zpracovat nově vytvořený kontext zařízení tiskárny.

### <a name="remarks"></a>Poznámky

Vrácený řadič domény je `hDC` také uložen v členu [m_pdex](#m_pdex).

Předpokládá se, že tento řadič domény je aktuální řadičdomény tiskárny a všechny ostatní dříve získané řadiče domény tiskárny musí být odstraněny. Tuto funkci lze volat a použít výsledný řadič domény, aniž by se někdy zobrazilo tiskové dialogové okno.

## <a name="cprintdialogexdomodal"></a><a name="domodal"></a>CPrintDialogEx::DoModální

Voláním této funkce zobrazíte seznam vlastností systému Windows Print a umožníte uživateli vybrat různé možnosti tisku, například počet kopií, rozsah stránek a zda mají být kopie shromážděny.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota INT_PTR je ve skutečnosti HRESULT. Viz oddíl Návratové hodnoty v [printdlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\)) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Chcete-li inicializovat různé možnosti tiskového `m_pdex` dialogu nastavením členů struktury, měli byste to provést před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Po `DoModal`volání můžete volat další členské funkce a načíst nastavení nebo informace vstupující uživatelem do dialogového okna.

Pokud je při volání `DoModal`použit příznak PD_RETURNDC , bude `hDC` řadič domény tiskárny vrácen v členu [m_pdex](#m_pdex). Tento řadič domény musí být uvolněna s `CPrintDialogEx`voláním [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) volajícím .

## <a name="cprintdialogexgetcopies"></a><a name="getcopies"></a>CPrintDialogEx::GetCopies

Volání této funkce `DoModal` po volání načíst počet požadovaných kopií.

```
int GetCopies() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet požadovaných kopií.

## <a name="cprintdialogexgetdefaults"></a><a name="getdefaults"></a>CPrintDialogEx::GetDefaults

Voláním této funkce načtěte výchozí nastavení zařízení výchozí tiskárny bez zobrazení dialogového okna.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu, jinak FALSE.

### <a name="remarks"></a>Poznámky

Vytvoří kontext zařízení tiskárny (DC) ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

`GetDefaults`nezobrazí seznam vlastností Tisk. Místo `hDevNames` toho nastaví `hDevMode` a členy [m_pdex](#m_pdex) pro zpracování [devmode](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) struktury, které jsou inicializovány pro výchozí tiskárnu systému. Oba `hDevNames` `hDevMode` a musí být `GetDefaults` NULL nebo se nezdaří.

Pokud je nastaven příznak PD_RETURNDC, tato `hDevNames` funkce `hDevMode` se `m_pdex.hDevNames` vrátí `m_pdex.hDevMode`nejen a (umístěna v a `m_pdex.hDC`) volajícímu, ale také vrátí řadič domény tiskárny v . Je odpovědností volajícího odstranit řadič domény tiskárny a volat funkci Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) na úchyty po dokončení s objektem. `CPrintDialogEx`

## <a name="cprintdialogexgetdevicename"></a><a name="getdevicename"></a>CPrintDialogEx::GetDeviceName

Volání této funkce po volání [DoModal](#domodal) načíst název aktuálně vybrané tiskárny nebo po volání [GetDefaults](#getdefaults) načíst název výchozí tiskárny.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybrané tiskárny.

### <a name="remarks"></a>Poznámky

Použijte ukazatel na `CString` objekt `GetDeviceName` vrácený jako `lpszDeviceName` hodnotu volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cprintdialogexgetdevmode"></a><a name="getdevmode"></a>CPrintDialogEx::GetDevMode

Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst informace o tiskovézařízení.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Datová struktura [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) která obsahuje informace o inicializaci zařízení a prostředí tiskového ovladače. Je nutné odemknout paměť převzatou touto strukturou pomocí funkce Windows [GlobalUnlock,](/windows/win32/api/winbase/nf-winbase-globalunlock) která je popsána v sadě Windows SDK.

## <a name="cprintdialogexgetdrivername"></a><a name="getdrivername"></a>CPrintDialogex::GetDriverName

Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název systémově definované ovladače tiskárny zařízení.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CString` zadání systémově definovaného názvu ovladače.

### <a name="remarks"></a>Poznámky

Použijte ukazatel na `CString` objekt `GetDriverName` vrácený jako hodnotu *lpszDriverName* ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cprintdialogexgetportname"></a><a name="getportname"></a>CPrintDialogex::GetPortName

Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název aktuálně vybraného portu tiskárny.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybraného portu tiskárny.

## <a name="cprintdialogexgetprinterdc"></a><a name="getprinterdc"></a>CPrintDialogEx::GetPrinterDC

Vrátí popisovač do kontextu zařízení tiskárny.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení tiskárny.

### <a name="remarks"></a>Poznámky

Chcete-li odstranit kontext zařízení po dokončení jeho používání, je nutné volat funkci [Windows DeleteDC.](/windows/win32/api/wingdi/nf-wingdi-deletedc)

## <a name="cprintdialogexm_pdex"></a><a name="m_pdex"></a>CPrintDialogEx::m_pdex

Struktura PRINTDLGEX, jejíž členy ukládají vlastnosti objektu dialogového okna.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Poznámky

Po vytvoření `CPrintDialogEx` objektu můžete `m_pdex` před voláním členské funkce [DoModal](#domodal) nastavit různé aspekty dialogového okna. Další informace o `m_pdex` struktuře naleznete v tématu [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) v sadě Windows SDK.

Pokud změníte `m_pdex` datový člen přímo, přepíšete jakékoli výchozí chování.

## <a name="cprintdialogexprintall"></a><a name="printall"></a>CPrintDialogEx::PrintAll

Volání této funkce `DoModal` po volání k určení, zda chcete vytisknout všechny stránky v dokumentu.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud mají být vytištěny všechny stránky v dokumentu; jinak FALSE.

## <a name="cprintdialogexprintcollate"></a><a name="printcollate"></a>CPrintDialogEx::PrintCollate

Volání této funkce `DoModal` po volání k určení, zda tiskárna má kompletovat všechny tištěné kopie dokumentu.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud uživatel zaškrtne políčko kompletovat v dialogovém okně; jinak FALSE.

## <a name="cprintdialogexprintcurrentpage"></a><a name="printcurrentpage"></a>CPrintDialogEx::PrintCurrentPage

Volání této funkce `DoModal` po volání k určení, zda chcete vytisknout aktuální stránku v dokumentu.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je v tiskovém dialogovém okně vybraná možnost **Vytisknout aktuální stránku;** jinak FALSE.

## <a name="cprintdialogexprintrange"></a><a name="printrange"></a>CPrintDialogEx::PrintRange

Volání této funkce `DoModal` po volání k určení, zda chcete vytisknout pouze rozsah stránek v dokumentu.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud mají být vytištěny pouze stránky v dokumentu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Zadané rozsahy stránek lze [m_pdex](#m_pdex) určit z `nPageRanges` `nMaxPageRanges`m_pdex `lpPageRanges` (viz , a ve struktuře [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) v sadě Windows SDK).

## <a name="cprintdialogexprintselection"></a><a name="printselection"></a>CPrintDialogEx::PrintSelection

Volání této funkce `DoModal` po volání k určení, zda chcete vytisknout pouze aktuálně vybrané položky.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud mají být vytištěny pouze vybrané položky; jinak FALSE.

## <a name="see-also"></a>Viz také

[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo – struktura](../../mfc/reference/cprintinfo-structure.md)
