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
ms.openlocfilehash: ebef892e174525c0b907818c02b7d34b1b41f850
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916899"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx – třída

Zapouzdřuje služby poskytované seznamem vlastností tisk systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|`CPrintDialogEx` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Vytvoří kontext zařízení tiskárny bez zobrazení dialogového okna Tisk.|
|[CPrintDialogEx::DoModal](#domodal)|Zobrazí dialogové okno a umožní uživateli provést výběr.|
|[CPrintDialogEx:: rekopie](#getcopies)|Načte počet požadovaných kopií.|
|[CPrintDialogEx:: GetDefaults](#getdefaults)|Načte výchozí nastavení zařízení bez zobrazení dialogového okna.|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Načte název aktuálně vybraného tiskového zařízení.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|`DEVMODE` Načte strukturu.|
|[CPrintDialogEx::GetDriverName](#getdrivername)|Načte název ovladače zařízení definovaného systémem.|
|[CPrintDialogEx:: GetPort](#getportname)|Načte název aktuálně vybraného portu tiskárny.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Načte popisovač do kontextu zařízení tiskárny.|
|[CPrintDialogEx::PrintAll](#printall)|Určuje, zda se mají tisknout všechny stránky dokumentu.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Určuje, zda jsou požadovány Kompletované kopie.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Určuje, zda má být vytištěna aktuální stránka dokumentu.|
|[CPrintDialogEx::PrintRange](#printrange)|Určuje, zda tisknout pouze zadaný rozsah stránek.|
|[CPrintDialogEx::PrintSelection](#printselection)|Určuje, zda se mají tisknout pouze aktuálně vybrané položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|Struktura používaná k přizpůsobení `CPrintDialogEx` objektu.|

## <a name="remarks"></a>Poznámky

Můžete spoléhat na rozhraní a zpracovávat mnoho aspektů procesu tisku pro vaši aplikaci. Další informace o použití architektury ke zpracování úloh tisku najdete v článku [Tisk](../../mfc/printing.md).

Pokud chcete, aby aplikace zpracovávala tisk bez zapojení rozhraní, můžete použít `CPrintDialogEx` třídu "tak, jak je" se zadaným konstruktorem, nebo můžete odvodit vlastní třídu dialogového okna z `CPrintDialogEx` a napsat konstruktor, který bude vyhovovat vašim potřebám. V obou případech se tato dialogová okna budou chovat jako standardní dialogová okna knihovny MFC, protože jsou odvozena z třídy `CCommonDialog`.

Chcete-li `CPrintDialogEx` použít objekt, nejprve vytvořte objekt `CPrintDialogEx` pomocí konstruktoru. Po vytvoření dialogového okna můžete nastavit nebo změnit libovolné hodnoty ve struktuře [m_pdex](#m_pdex) a inicializovat tak hodnoty ovládacích prvků dialogového okna. Struktura je typu PrintDlgEx. [](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) `m_pdex` Další informace o této struktuře naleznete v Windows SDK.

`m_pdex` Pokud nezadáte vlastní popisovače v nástroji `hDevMode` pro členy a `hDevNames` , nezapomeňte po dokončení dialogového okna zavolat funkci `GlobalFree` systému Windows pro tyto popisovače.

Po inicializaci ovládacích prvků dialogového okna zavolejte `DoModal` členskou funkci pro zobrazení dialogového okna a umožněte uživateli vybrat možnosti tisku. Po `DoModal` návratu můžete určit, zda uživatel vybral tlačítko OK, použít nebo Storno.

Pokud uživatel stiskne OK, můžete použít `CPrintDialogEx`členské funkce k načtení informací o vstupu uživatele.

`CPrintDialogEx::GetDefaults` Členská funkce je užitečná pro načítání současných výchozích nastavení tiskárny bez zobrazení dialogového okna. Tato metoda nevyžaduje žádnou interakci s uživatelem.

Funkci Windows `CommDlgExtendedError` můžete použít k určení, zda došlo k chybě během inicializace dialogového okna a další informace o chybě. Další informace o této funkci naleznete v Windows SDK.

Další informace o použití `CPrintDialogEx`naleznete v tématu [Common dialoging Class](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs. h

##  <a name="cprintdialogex"></a>CPrintDialogEx::CPrintDialogEx

Sestaví seznam vlastností tisku ve Windows.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Jeden nebo více příznaků, které lze použít k přizpůsobení nastavení dialogového okna v kombinaci s použitím bitového operátoru OR. Například příznak PD_ALLPAGES nastaví výchozí rozsah tisku na všechny stránky dokumentu. Další informace o těchto příznacích najdete v [PrintDlgEx](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) struktuře v Windows SDK.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastní okno dialogového okna.

### <a name="remarks"></a>Poznámky

Tato členská funkce vytvoří pouze objekt. K zobrazení dialogového okna použijte členskoufunkci.`DoModal`

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

Vytvoří kontext zařízení tiskárny ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES –](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač nově vytvořeného kontextu zařízení tiskárny.

### <a name="remarks"></a>Poznámky

Vrácený řadič domény je uložen také v `hDC` členu [m_pdex](#m_pdex).

Tento řadič domény se považuje za aktuální řadič domény tiskárny a všechny další dříve získané tiskárny se musí odstranit. Tuto funkci lze volat a výsledný použitý řadič domény, aniž byste museli zobrazovat dialogové okno Tisk.

##  <a name="domodal"></a>  CPrintDialogEx::DoModal

Voláním této funkce zobrazíte seznam vlastností tisku systému Windows a povolíte uživateli vybrat různé možnosti tisku, například počet kopií, rozsah stránek a to, zda mají být kopie řazeny.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota INT_PTR je ve skutečnosti HRESULT. Viz část návratové hodnoty v [PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\)) v Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé možnosti dialogového okna pro tisk nastavením členů `m_pdex` struktury, měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

Po volání `DoModal`můžete zavolat jiné členské funkce a načíst nastavení nebo zadání informací uživatelem do dialogového okna.

Pokud se při volání `DoModal`použije příznak PD_RETURNDC, bude `hDC` v členu [m_pdex](#m_pdex)vrácen řadič domény tiskárny. Tento řadič domény musí být uvolněn voláním [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) volajícím `CPrintDialogEx`.

##  <a name="getcopies"></a>CPrintDialogEx:: rekopie

Tuto funkci zavolejte po volání `DoModal` , aby se načetl požadovaný počet kopií.

```
int GetCopies() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet požadovaných kopií

##  <a name="getdefaults"></a>CPrintDialogEx:: GetDefaults

Voláním této funkce načtete výchozí nastavení zařízení výchozí tiskárny bez zobrazení dialogového okna.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je to úspěšné, jinak FALSE.

### <a name="remarks"></a>Poznámky

Vytvoří kontext zařízení tiskárny ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES –](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) .

`GetDefaults`nezobrazuje seznam vlastností tisk. Místo toho nastaví `hDevNames` a `hDevMode` členové [m_pdex](#m_pdex) pro zpracování do struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES –](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) , které jsou inicializovány pro výchozí tiskárnu systému. A musí mít hodnotu null nebo `GetDefaults` se nezdařila. `hDevMode` `hDevNames`

Pokud je nastaven příznak PD_RETURNDC, `hDevNames` nebude tato funkce vracet pouze a `hDevMode` (umístěn v `m_pdex.hDevNames` a `m_pdex.hDevMode`) volajícímu, ale také vrátí řadič domény tiskárny v `m_pdex.hDC`. Je odpovědností volajícího odstranit řadič domény tiskárny a volat funkci Windows [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) v popisovačích po dokončení `CPrintDialogEx` objektu.

##  <a name="getdevicename"></a>CPrintDialogEx:: getnázev_zařízení

Tuto funkci zavolejte po volání metody [DoModal](#domodal) , která načte název aktuálně vybrané tiskárny, nebo po volání funkce [](#getdefaults) GetDefaults pro načtení názvu výchozí tiskárny.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybrané tiskárny.

### <a name="remarks"></a>Poznámky

Použijte ukazatel na `CString` objekt `GetDeviceName` vrácený jako hodnota `lpszDeviceName` v volání metody [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getdevmode"></a>CPrintDialogEx:: getdevmode

Tuto funkci zavolejte po volání [DoModal](#domodal) nebo [](#getdefaults) GetDefaults, aby se načetly informace o tiskovém zařízení.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Struktura dat [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , která obsahuje informace o inicializaci zařízení a prostředí ovladače tiskárny. Paměť, kterou tato struktura provedla, je nutné odemknout pomocí funkce Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) , která je popsána v Windows SDK.

##  <a name="getdrivername"></a>CPrintDialogEx:: getnázev_ovladače

Tuto funkci zavolejte po volání [DoModal](#domodal) nebo [](#getdefaults) GetDefaults, aby se načetl název ovladače zařízení definovaného systémem.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Návratová hodnota

`CString` Zadání názvu ovladače definovaného systémem.

### <a name="remarks"></a>Poznámky

`CString` Použijte ukazatel na `GetDriverName` objekt vrácený jako hodnota *lpszDriverName* ve volání metody [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getportname"></a>CPrintDialogEx:: GetPort

Tuto funkci zavolejte po volání [DoModal](#domodal) nebo [](#getdefaults) GetDefaults, aby se načetl název aktuálně vybraného portu tiskárny.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybraného portu tiskárny.

##  <a name="getprinterdc"></a>CPrintDialogEx::GetPrinterDC

Vrátí popisovač kontextu zařízení tiskárny.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení tiskárny.

### <a name="remarks"></a>Poznámky

Chcete-li odstranit kontext zařízení po jeho použití, je třeba zavolat funkci Windows [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) .

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

Struktura PRINTDLGEX, jejíž členové ukládají charakteristiky objektu dialogového okna.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Poznámky

Po sestavení `CPrintDialogEx` objektu lze použít `m_pdex` k nastavení různých aspektů dialogového okna před voláním členské funkce [DoModal](#domodal) . Další informace o `m_pdex` struktuře naleznete v tématu [PrintDlgEx](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) v Windows SDK.

Změníte-li datový člen přímo, přepíšete všechny výchozí chování. `m_pdex`

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

Voláním této funkce po `DoModal` volání určete, zda se mají vytisknout všechny stránky v dokumentu.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se mají vytisknout všechny stránky v dokumentu; v opačném případě FALSE.

##  <a name="printcollate"></a>CPrintDialogEx::P rintCollate

Tuto funkci zavolejte po volání `DoModal` , aby se určilo, jestli má tiskárna třídit všechny tištěné kopie dokumentu.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud uživatel v dialogovém okně vybere zaškrtávací políčko COLLATE; v opačném případě FALSE.

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

Voláním této funkce po `DoModal` volání určete, zda se má vytisknout aktuální stránka v dokumentu.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je v dialogovém okně Tisk vybraná možnost **Tisk aktuální stránky** ; v opačném případě FALSE.

##  <a name="printrange"></a>CPrintDialogEx::P rintRange

Tuto funkci zavolejte po volání `DoModal` , aby se určilo, jestli se má v dokumentu tisknout jenom rozsah stránek.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, je-li vytištěn pouze rozsah stránek v dokumentu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Zadané rozsahy stránek lze určit z [m_pdex](#m_pdex) ( `nPageRanges`viz, `nMaxPageRanges`a `lpPageRanges` ve struktuře [PrintDlgEx](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) v Windows SDK).

##  <a name="printselection"></a>CPrintDialogEx::P rintSelection

Tuto funkci zavolejte po volání `DoModal` , aby se určilo, jestli se mají tisknout jenom aktuálně vybrané položky.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se mají tisknout jenom vybrané položky; v opačném případě FALSE.

## <a name="see-also"></a>Viz také:

[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo – struktura](../../mfc/reference/cprintinfo-structure.md)
