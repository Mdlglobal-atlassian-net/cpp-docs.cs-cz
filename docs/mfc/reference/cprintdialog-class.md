---
title: CPrintDialog – třída
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: ccc673d665d6d5beb92f398b21e6ffd313a58fc9
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741365"
---
# <a name="cprintdialog-class"></a>CPrintDialog – třída

Zapouzdřuje služby poskytované běžným dialogovým oknem systému Windows pro tisk.

## <a name="syntax"></a>Syntaxe

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|`CPrintDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Vytvoří kontext zařízení tiskárny bez zobrazení dialogového okna Tisk.|
|[CPrintDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožní uživateli provést výběr.|
|[CPrintDialog::GetCopies](#getcopies)|Načte počet požadovaných kopií.|
|[CPrintDialog:: GetDefaults](#getdefaults)|Načte výchozí nastavení zařízení bez zobrazení dialogového okna.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Načte název aktuálně vybraného tiskového zařízení.|
|[CPrintDialog::GetDevMode](#getdevmode)|`DEVMODE` Načte strukturu.|
|[CPrintDialog::GetDriverName](#getdrivername)|Načte název aktuálně vybraného ovladače tiskárny.|
|[CPrintDialog::GetFromPage](#getfrompage)|Načte úvodní stránku rozsahu tisku.|
|[CPrintDialog::GetPortName](#getportname)|Načte název aktuálně vybraného portu tiskárny.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Načte popisovač do kontextu zařízení tiskárny.|
|[CPrintDialog::GetToPage](#gettopage)|Načte koncovou stránku rozsahu tisku.|
|[CPrintDialog::PrintAll](#printall)|Určuje, zda se mají tisknout všechny stránky dokumentu.|
|[CPrintDialog::PrintCollate](#printcollate)|Určuje, zda jsou požadovány Kompletované kopie.|
|[CPrintDialog::PrintRange](#printrange)|Určuje, zda tisknout pouze zadaný rozsah stránek.|
|[CPrintDialog::PrintSelection](#printselection)|Určuje, zda se mají tisknout pouze aktuálně vybrané položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Struktura používaná k přizpůsobení `CPrintDialog` objektu.|

## <a name="remarks"></a>Poznámky

Společná dialogová okna pro tisk poskytují snadný způsob implementace tisku a dialogových oken nastavení tisku způsobem konzistentním s normami Windows.

> [!NOTE]
>  `CPrintDialogEx` Třída zapouzdřuje služby poskytované seznamem vlastností tisk systému Windows. Další informace najdete v přehledu [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) .

`CPrintDialog`je nahrazena funkcí [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), která je navržena tak, aby vám poskytovala společné dialogové okno pro nastavení tisku a nastavení stránky.

Můžete spoléhat na rozhraní a zpracovávat mnoho aspektů procesu tisku pro vaši aplikaci. V tomto případě rozhraní automaticky zobrazí dialogové okno Windows Common pro tisk. Architekturu pro aplikaci můžete také zpracovat, ale přepsat běžný dialog tisku pomocí vlastního dialogového okna pro tisk. Další informace o použití architektury ke zpracování úloh tisku najdete v článku [Tisk](../../mfc/printing.md).

Pokud chcete, aby aplikace zpracovávala tisk bez zapojení rozhraní, můžete použít `CPrintDialog` třídu "tak, jak je" se zadaným konstruktorem, nebo můžete odvodit vlastní třídu dialogového okna z `CPrintDialog` a napsat konstruktor, který bude vyhovovat vašim potřebám. V obou případech se tato dialogová okna budou chovat jako standardní dialogová okna knihovny MFC, protože jsou odvozena z třídy `CCommonDialog`.

Chcete-li `CPrintDialog` použít objekt, nejprve vytvořte objekt `CPrintDialog` pomocí konstruktoru. Po vytvoření dialogového okna můžete nastavit nebo změnit libovolné hodnoty ve struktuře [m_pd](#m_pd) a inicializovat tak hodnoty ovládacích prvků dialogového okna. Struktura je typu PRINTDLG. [](/windows/win32/api/commdlg/ns-commdlg-printdlga) `m_pd` Další informace o této struktuře naleznete v Windows SDK.

`m_pd` Pokud nezadáte vlastní popisovače v nástroji `hDevMode` pro členy a `hDevNames` , nezapomeňte po dokončení dialogového okna zavolat funkci `GlobalFree` systému Windows pro tyto popisovače. Při použití implementace nastavení tisku v rozhraní `CWinApp::OnFilePrintSetup`, které poskytuje, není nutné tyto popisovače uvolnit. Popisovače jsou uchovávány pomocí `CWinApp` a jsou uvolněny v `CWinApp`destruktoru. Tyto popisovače je nutné uvolnit pouze při použití `CPrintDialog` samostatného.

Po inicializaci ovládacích prvků dialogového okna zavolejte `DoModal` členskou funkci pro zobrazení dialogového okna a umožněte uživateli vybrat možnosti tisku. `DoModal`Vrátí, zda uživatel vybral tlačítko OK (IDOK) nebo zrušit (IDCANCEL).

Pokud `DoModal` vrátí IDOK, můžete použít jednu z `CPrintDialog`členských funkcí k načtení informací o vstupu uživatele.

`CPrintDialog::GetDefaults` Členská funkce je užitečná pro načítání současných výchozích nastavení tiskárny bez zobrazení dialogového okna. Tato členská funkce nevyžaduje žádnou interakci s uživatelem.

Funkci Windows `CommDlgExtendedError` můžete použít k určení, zda došlo k chybě během inicializace dialogového okna a další informace o chybě. Další informace o této funkci naleznete v Windows SDK.

`CPrintDialog`spoléhá na COMMDLG. Soubor DLL dodávaný se systémem Windows verze 3,1 nebo novějším.

Chcete-li přizpůsobit dialogové okno, odvodit třídu `CPrintDialog`z, zadat vlastní šablonu dialogového okna a přidat mapu zpráv pro zpracování zpráv s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měly být předány základní třídě. Přizpůsobení funkce zavěšení není vyžadováno.

Chcete-li zpracovat stejnou zprávu odlišně v závislosti na tom, zda je dialogové okno Tisk nebo nastavení tisku, je nutné pro každé dialogové okno odvodit třídu. Je také nutné přepsat funkci systému `AttachOnSetup` Windows, která zpracovává vytvoření nového dialogového okna v případě, že je vybráno tlačítko Tisk v dialogovém okně Tisk.

Další informace o použití `CPrintDialog`naleznete v tématu [Common dialoging Class](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs. h

##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog

Sestaví buď dialogové okno tiskového nebo tiskového nastavení systému Windows.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*bPrintSetupOnly*<br/>
Určuje, zda se zobrazí dialogové okno standardní tisk systému Windows nebo nastavení tisku. Nastavením tohoto parametru na hodnotu TRUE zobrazíte standardní dialogové okno nastavení tisku systému Windows. Nastavte na hodnotu FALSE, chcete-li zobrazit dialogové okno Tisk systému Windows. Pokud má *bPrintSetupOnly* hodnotu false, v dialogovém okně Tisk se stále zobrazuje tlačítko možností nastavení tisku.

*dwFlags*<br/>
Jeden nebo více příznaků, které lze použít k přizpůsobení nastavení dialogového okna v kombinaci s použitím bitového operátoru OR. Například příznak PD_ALLPAGES nastaví výchozí rozsah tisku na všechny stránky dokumentu. Další informace o těchto příznacích najdete v [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) struktuře v Windows SDK.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastní okno dialogového okna.

### <a name="remarks"></a>Poznámky

Tato členská funkce vytvoří pouze objekt. K zobrazení dialogového okna použijte členskoufunkci.`DoModal`

Všimněte si, že při volání konstruktoru s *bPrintSetupOnly* nastavenou na hodnotu false je automaticky použit příznak PD_RETURNDC. Po volání `DoModal`, `GetDefaults`nebo `GetPrinterDC`se vrátí řadič domény tiskárny v `m_pd.hDC`. Tento řadič domény musí být uvolněn voláním [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) volajícím `CPrintDialog`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC

Vytvoří kontext zařízení tiskárny ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES –](/windows/win32/api/commdlg/ns-commdlg-devnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač nově vytvořeného kontextu zařízení tiskárny.

### <a name="remarks"></a>Poznámky

Tento řadič domény se považuje za aktuální řadič domény a všechny další dříve získané tiskárny musí odstranit uživatel. Tuto funkci lze volat a výsledný použitý řadič domény, aniž byste museli zobrazovat dialogové okno Tisk.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>  CPrintDialog::DoModal

Zobrazí dialogové okno běžný tisk systému Windows a umožňuje uživateli vybrat různé možnosti tisku, například počet kopií, rozsah stránek a to, zda mají být kopie řazeny.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud se vrátí IDCANCEL, zavolejte funkci Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) a určete, jestli došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo Storno.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé možnosti dialogového okna pro tisk nastavením členů `m_pd` struktury, měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

Po volání `DoModal`můžete zavolat jiné členské funkce a načíst nastavení nebo zadání informací uživatelem do dialogového okna.

Všimněte si, že při volání konstruktoru s *bPrintSetupOnly* nastavenou na hodnotu false je automaticky použit příznak PD_RETURNDC. Po volání `DoModal`, `GetDefaults`nebo `GetPrinterDC`se vrátí řadič domény tiskárny v `m_pd.hDC`. Tento řadič domény musí být uvolněn voláním [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) volajícím `CPrintDialog`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog:: CreatePrinterDC](#createprinterdc).

##  <a name="getcopies"></a>CPrintDialog:: rekopie

Načte počet požadovaných kopií.

```
int GetCopies() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet požadovaných kopií

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte po volání `DoModal` , aby se načetl požadovaný počet kopií.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdefaults"></a>CPrintDialog:: GetDefaults

Načte výchozí nastavení zařízení výchozí tiskárny bez zobrazení dialogového okna.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla funkce úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Načtené hodnoty se umístí do `m_pd` struktury.

V některých případech volání této funkce vyvolá [konstruktor](#cprintdialog) pro `CPrintDialog` s *bPrintSetupOnly* nastavenou na hodnotu false. V těchto případech jsou automaticky přiděleny tiskárny `hDevNames` DC `hDevMode` a ( `m_pd` dva popisovače umístěné v datovém členu).

Pokud byl konstruktor pro `CPrintDialog` zavolán s *bPrintSetupOnly* nastaven na hodnotu false, tato funkce nevrátí `hDevNames` do volajícího a `m_pd.hDevNames` `hDevMode` jeho `m_pd.hDevMode`umístění pouze v a), ale také vrátí řadič domény tiskárny v umístění `m_pd.hDC`. Je odpovědností volajícího odstranit řadič domény tiskárny a volat funkci Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) v popisovačích po dokončení `CPrintDialog` objektu.

### <a name="example"></a>Příklad

Tento fragment kódu získá kontext zařízení výchozí tiskárny a sestaví uživatele podle rozlišení tiskárny v bodech na palec. (Tento atribut schopností tiskárny se často označuje jako DPI.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>CPrintDialog:: getnázev_zařízení

Načte název aktuálně vybraného tiskového zařízení.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybrané tiskárny.

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte po volání metody [DoModal](#domodal) , která načte název aktuálně vybrané tiskárny, nebo po volání funkce [GetDefaults](#getdefaults) pro načtení aktuálních výchozích hodnot zařízení výchozí tiskárny. Použijte ukazatel na `CString` objekt `GetDeviceName` vrácený jako hodnota `lpszDeviceName` v volání metody [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Příklad

Tento fragment kódu ukazuje výchozí název tiskárny uživatele a port, ke kterému je připojen, spolu s názvem zařazovací služby, kterou tiskárna používá. Kód může zobrazit okno se zprávou, že výchozí tiskárna je HP LaserJet IIIP on \\\server\share s použitím Winspool. ", například.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>CPrintDialog:: getdevmode

`DEVMODE` Načte strukturu.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Struktura dat [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , která obsahuje informace o inicializaci zařízení a prostředí ovladače tiskárny. Paměť, kterou tato struktura provedla, je nutné odemknout pomocí funkce Windows [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) , která je popsána v Windows SDK.

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) , aby se načetly informace o tiskovém zařízení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdrivername"></a>CPrintDialog:: getnázev_ovladače

Načte název aktuálně vybraného ovladače tiskárny.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Návratová hodnota

`CString` Zadání názvu ovladače definovaného systémem.

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) , aby se načetl název ovladače zařízení definovaného systémem. Použijte ukazatel na `CString` objekt `GetDriverName` vrácený jako hodnota `lpszDriverName` v volání metody [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog:: getnázev_zařízení](#getdevicename).

##  <a name="getfrompage"></a>CPrintDialog::GetFromPage

Načte úvodní stránku rozsahu tisku.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční číslo stránky v rozsahu stránek, které se mají vytisknout

### <a name="remarks"></a>Poznámky

Tuto funkci volejte po volání `DoModal` metody k načtení počátečního čísla stránky v rozsahu stránek, které chcete vytisknout.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog:: m_pd](#m_pd).

##  <a name="getportname"></a>CPrintDialog:: GetPort

Načte název aktuálně vybraného portu tiskárny.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybraného portu tiskárny.

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) , aby se načetl název aktuálně vybraného portu tiskárny.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog:: getnázev_zařízení](#getdevicename).

##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC

Načte popisovač do kontextu zařízení tiskárny.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač do kontextu zařízení tiskárny, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud `CPrintDialog` parametr *bPrintSetupOnly* konstruktoru měl hodnotu false (což značí, že se zobrazí dialogové okno Tisk), pak `GetPrinterDC` vrátí popisovač do kontextu zařízení tiskárny. Chcete-li odstranit kontext zařízení po jeho použití, je třeba zavolat funkci Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>  CPrintDialog::GetToPage

Načte koncovou stránku rozsahu tisku.

```
int GetToPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo koncové stránky v rozsahu stránek, které mají být vytištěny.

### <a name="remarks"></a>Poznámky

Tuto funkci volejte po volání `DoModal` metody k načtení čísla koncové stránky v rozsahu stránek, které se mají vytisknout.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog:: m_pd](#m_pd).

##  <a name="m_pd"></a>  CPrintDialog::m_pd

Struktura, jejíž členové ukládají charakteristiky objektu dialogového okna.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Poznámky

Po sestavení `CPrintDialog` objektu lze použít `m_pd` k nastavení různých aspektů dialogového okna před voláním členské funkce [DoModal](#domodal) . Další informace o `m_pd` struktuře naleznete v tématu [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) v Windows SDK.

Změníte-li datový člen přímo, přepíšete všechny výchozí chování. `m_pd`

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>  CPrintDialog::PrintAll

Určuje, zda se mají tisknout všechny stránky dokumentu.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud mají být vytištěny všechny stránky v dokumentu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Voláním této funkce po `DoModal` volání určete, zda se mají vytisknout všechny stránky v dokumentu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog:: m_pd](#m_pd).

##  <a name="printcollate"></a>CPrintDialog::P rintCollate

Určuje, zda jsou požadovány Kompletované kopie.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel v dialogovém okně vybere zaškrtávací políčko COLLATE; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte po volání `DoModal` , aby se určilo, jestli má tiskárna třídit všechny tištěné kopie dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>CPrintDialog::P rintRange

Určuje, zda tisknout pouze zadaný rozsah stránek.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud má být tištěn pouze rozsah stránek v dokumentu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte po volání `DoModal` , aby se určilo, jestli se má v dokumentu tisknout jenom rozsah stránek.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog:: m_pd](#m_pd).

##  <a name="printselection"></a>CPrintDialog::P rintSelection

Určuje, zda se mají tisknout pouze aktuálně vybrané položky.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud mají být vytištěny pouze vybrané položky; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte po volání `DoModal` , aby se určilo, jestli se mají tisknout jenom aktuálně vybrané položky.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog:: m_pd](#m_pd).

## <a name="see-also"></a>Viz také:

[DIBLOOK Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo – struktura](../../mfc/reference/cprintinfo-structure.md)
