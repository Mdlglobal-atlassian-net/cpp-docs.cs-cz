---
title: Třída CPrintDialog
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
ms.openlocfilehash: 6490e5488c5ab3b808a02e3608b75541e4063d8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364067"
---
# <a name="cprintdialog-class"></a>Třída CPrintDialog

Zapouzdřuje služby poskytované běžným dialogovým oknem systému Windows pro tisk.

## <a name="syntax"></a>Syntaxe

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|Vytvoří `CPrintDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Vytvoří kontext zařízení tiskárny bez zobrazení tiskového dialogového okna.|
|[CPrintDialog::DoModální](#domodal)|Zobrazí dialogové okno a umožní uživateli provést výběr.|
|[CPrintDialog::GetCopies](#getcopies)|Načte počet požadovaných kopií.|
|[CPrintDialog::GetDefaults](#getdefaults)|Načte výchozí hodnoty zařízení bez zobrazení dialogového okna.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Načte název aktuálně vybraného tiskového zařízení.|
|[CPrintDialog::GetDevMode](#getdevmode)|Načte `DEVMODE` strukturu.|
|[CPrintDialog::GetDriverName](#getdrivername)|Načte název aktuálně vybraného ovladače tiskárny.|
|[CPrintDialog::GetFromPage](#getfrompage)|Načte počáteční stránku rozsahu tisku.|
|[CPrintDialog::GetPortName](#getportname)|Načte název aktuálně vybraného portu tiskárny.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Načte popisovač do kontextu zařízení tiskárny.|
|[CPrintDialog::GetToPage](#gettopage)|Načte koncovou stránku rozsahu tisku.|
|[CPrintDialog::PrintAll](#printall)|Určuje, zda se mají vytisknout všechny stránky dokumentu.|
|[CPrintDialog::PrintCollate](#printcollate)|Určuje, zda jsou požadovány kompletované kopie.|
|[CPrintDialog::PrintRange](#printrange)|Určuje, zda se má vytisknout pouze zadaný rozsah stránek.|
|[CPrintDialog::PrintSelection](#printselection)|Určuje, zda se mají vytisknout pouze aktuálně vybrané položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Struktura slouží k `CPrintDialog` přizpůsobení objektu.|

## <a name="remarks"></a>Poznámky

Běžná tisková dialogová okna poskytují snadný způsob implementace dialogových oken Nastavení tisku a tisku způsobem, který je v souladu se standardy systému Windows.

> [!NOTE]
> Třída `CPrintDialogEx` zapouzdřuje služby poskytované v seznamu vlastností Windows Print. Další informace naleznete v přehledu [CPrintDialogEx.](../../mfc/reference/cprintdialogex-class.md)

`CPrintDialog`Funkce programu CPageSetupDialog je nahrazena funkcí [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), která je navržena tak, aby vám poskytla společné dialogové okno pro nastavení tisku i nastavení stránky.

Můžete se spolehnout na rozhraní pro zpracování mnoha aspektů procesu tisku pro vaši aplikaci. V takovém případě se v rámci automaticky zobrazí běžné dialogové okno systému Windows pro tisk. Můžete také nechat vytisknout popisovač architektury pro vaši aplikaci, ale přepsat společné tiskové dialogové okno s vlastním tiskovým dialogovým oknem. Další informace o použití rozhraní pro zpracování tiskových úloh naleznete v článku [Tisk](../../mfc/printing.md).

Pokud chcete, aby vaše aplikace zpracovávat tisk bez zapojení `CPrintDialog` rámci, můžete použít třídu "tak, jak je" s `CPrintDialog` konstruktorem k dispozici, nebo můžete odvodit vlastní dialog třídy z a napsat konstruktor, aby vyhovoval vašim potřebám. V obou případech se tato dialogová okna budou chovat jako standardní `CCommonDialog`dialogová okna knihovny MFC, protože jsou odvozena z třídy .

Chcete-li `CPrintDialog` použít objekt, nejprve `CPrintDialog` vytvořte objekt pomocí konstruktoru. Po vytvoření dialogového okna můžete nastavit nebo upravit libovolné hodnoty ve struktuře [m_pd](#m_pd) a inicializovat hodnoty ovládacích prvků dialogového okna. Struktura `m_pd` je typu [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga). Další informace o této struktuře naleznete v souboru Windows SDK.

Pokud nezadáte vlastní popisovače `m_pd` pro `hDevMode` členy `hDevNames` a, nezapomeňte volat funkci `GlobalFree` systému Windows pro tyto popisovače, když budete hotovi s dialogovým oknem. Při použití implementace nastavení tisku rozhraní `CWinApp::OnFilePrintSetup`poskytované rozhraním není k dispozici, není třeba uvolnit tyto popisovače. Úchyty jsou `CWinApp` udržovány `CWinApp`a jsou uvolněny v 's destruktoru. Je nutné uvolnit pouze tyto úchyty při použití `CPrintDialog` samostatné.

Po inicializaci ovládacích `DoModal` prvků dialogového okna zavolejte členské funkce, aby zobrazila dialogové okno a umožnila uživateli vybrat možnosti tisku. `DoModal`vrátí, zda uživatel zvolil tlačítko OK (IDOK) nebo Cancel (IDCANCEL).

Pokud `DoModal` vrátí IDOK, můžete `CPrintDialog`použít jednu z 's členské funkce načíst informace vstup uživatelem.

Členská `CPrintDialog::GetDefaults` funkce je užitečná pro načítání aktuálních výchozích hodnot tiskárny bez zobrazení dialogového okna. Tato členská funkce nevyžaduje žádnou interakci s uživatelem.

Pomocí funkce systému Windows `CommDlgExtendedError` můžete určit, zda došlo k chybě během inicializace dialogového okna a získat další informace o chybě. Další informace o této funkci naleznete v souboru Windows SDK.

`CPrintDialog`spoléhá na COMMDLG. Soubor DLL, který je dodáván se systémem Windows verze 3.1 a novější.

Chcete-li dialogové okno přizpůsobit, `CPrintDialog`odvoděte třídu z aplikace , zadejte vlastní šablonu dialogového okna a přidejte mapu zpráv pro zpracování zpráv s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měly být předány základní třídě. Přizpůsobení funkce háku není nutné.

Chcete-li zpracovat stejnou zprávu odlišně v závislosti na tom, zda je dialogové okno Tisk nebo Nastavení tisku, musíte odvodit třídu pro každé dialogové okno. Musíte také přepsat funkci `AttachOnSetup` systému Windows, která zpracovává vytvoření nového dialogového okna, když je v tiskovém dialogovém okně vybráno tlačítko Nastavení tisku.

Další informace o `CPrintDialog`použití naleznete v [tématu Common Dialog Classes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="cprintdialogcprintdialog"></a><a name="cprintdialog"></a>CPrintDialog::CPrintDialog

Vytvoří buď objekt dialogového okna Tisk nebo Nastavení tisku.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*bPrintSetupOnly*<br/>
Určuje, zda se zobrazí standardní tiskové dialogové okno systému Windows nebo dialogové okno Print Setup. Nastavte tento parametr na HODNOTU TRUE, aby se zobrazilo standardní dialogové okno Nastavení tisku systému Windows. Nastavte ji na HODNOTU NEPRAVDA, aby se zobrazilo tiskové dialogové okno systému Windows. Pokud je *bPrintSetupOnly* NEPRAVDA, v dialogovém okně Tisk se stále zobrazuje tlačítko Možnost iinstalační ho příkazu Print Setup.

*dwFlags*<br/>
Jeden nebo více příznaků, které můžete použít k přizpůsobení nastavení dialogového okna, kombinované pomocí bitového operátoru OR. Například příznak PD_ALLPAGES nastaví výchozí rozsah tisku na všechny stránky dokumentu. Další informace o těchto příznaky naleznete ve struktuře [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) v sadě Windows SDK.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastníjméno okna dialogového okna.

### <a name="remarks"></a>Poznámky

Tato členská funkce pouze vytvoří objekt. Dialogové `DoModal` okno se zobrazí pomocí členské funkce.

Všimněte si, že při volání konstruktoru s *bPrintSetupOnly* nastavena na FALSE, PD_RETURNDC příznak se automaticky použije. Po `DoModal`volání `GetDefaults`aplikace `GetPrinterDC`, nebo bude vrácen `m_pd.hDC`řadič domény tiskárny. Tento řadič domény musí být uvolněna s `CPrintDialog`voláním [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) volajícím .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

## <a name="cprintdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC

Vytvoří kontext zařízení tiskárny (DC) ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Návratová hodnota

Zpracovat nově vytvořený kontext zařízení tiskárny.

### <a name="remarks"></a>Poznámky

Předpokládá se, že tento řadič domény je aktuální řadičdomény tiskárny a uživatel musí odstranit všechny ostatní dříve získané řadiče domény tiskárny. Tuto funkci lze volat a použít výsledný řadič domény, aniž by se někdy zobrazilo tiskové dialogové okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

## <a name="cprintdialogdomodal"></a><a name="domodal"></a>CPrintDialog::DoModální

Zobrazí běžné tiskové dialogové okno systému Windows a umožňuje uživateli vybrat různé možnosti tisku, například počet kopií, rozsah stránek a zda mají být kopie shromážděny.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud je vrácena funkce IDCANCEL, zavolejte funkci Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) a zjistěte, zda došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel zvolil tlačítko OK nebo Cancel.

### <a name="remarks"></a>Poznámky

Chcete-li inicializovat různé možnosti tiskového `m_pd` dialogu nastavením členů struktury, měli byste to provést před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Po `DoModal`volání můžete volat další členské funkce a načíst nastavení nebo informace vstupující uživatelem do dialogového okna.

Všimněte si, že při volání konstruktoru s *bPrintSetupOnly* nastavena na FALSE, PD_RETURNDC příznak se automaticky použije. Po `DoModal`volání `GetDefaults`aplikace `GetPrinterDC`, nebo bude vrácen `m_pd.hDC`řadič domény tiskárny. Tento řadič domény musí být uvolněna s `CPrintDialog`voláním [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) volajícím .

### <a name="example"></a>Příklad

  Viz příklad [cprintdialog::CreatePrinterDC](#createprinterdc).

## <a name="cprintdialoggetcopies"></a><a name="getcopies"></a>CPrintDialog::GetCopies

Načte počet požadovaných kopií.

```
int GetCopies() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet požadovaných kopií.

### <a name="remarks"></a>Poznámky

Volání této funkce `DoModal` po volání načíst počet požadovaných kopií.

### <a name="example"></a>Příklad

  Viz příklad pro [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdefaults"></a><a name="getdefaults"></a>CPrintDialog::GetDefaults

Načte výchozí hodnoty zařízení výchozí tiskárny bez zobrazení dialogového okna.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Načtené hodnoty jsou umístěny ve `m_pd` struktuře.

V některých případech volání této funkce bude `CPrintDialog` volat [konstruktor](#cprintdialog) s *bPrintSetupOnly* nastavena na FALSE. V těchto případech jsou `hDevNames` automaticky `hDevMode` přiděleny řadičdomény `m_pd` tiskárny a (dva popisovače umístěné v datovém prvku).

Pokud konstruktor `CPrintDialog` pro byla volána s *bPrintSetupOnly* nastavena `hDevNames` na `hDevMode` FALSE, tato funkce se vrátí a nachází v `m_pd.hDevNames` a `m_pd.hDevMode`) volajícímu, ale také vrátí řadič domény tiskárny v `m_pd.hDC`. Je odpovědností volajícího odstranit řadič domény tiskárny a volat funkci Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) na úchyty po dokončení s objektem. `CPrintDialog`

### <a name="example"></a>Příklad

Tento fragment kódu získá výchozí kontext zařízení tiskárny a hlásí uživateli rozlišení tiskárny v rámci bodů na palec. (Tento atribut možností tiskárny se často označuje jako DPI.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

## <a name="cprintdialoggetdevicename"></a><a name="getdevicename"></a>CPrintDialog::GetDeviceName

Načte název aktuálně vybraného tiskového zařízení.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybrané tiskárny.

### <a name="remarks"></a>Poznámky

Volání této funkce po volání [DoModal](#domodal) načíst název aktuálně vybrané tiskárny nebo po volání [GetDefaults](#getdefaults) načíst aktuální výchozí nastavení zařízení výchozí tiskárny. Použijte ukazatel na `CString` objekt `GetDeviceName` vrácený jako `lpszDeviceName` hodnotu volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Příklad

Tento fragment kódu zobrazuje výchozí název tiskárny uživatele a port, ke kterým je připojen, spolu s názvem zařazovací hodu, který tiskárna používá. Kód může zobrazit okno se zprávou, která například uvádí: \\"Výchozí tiskárnou je HP LaserJet IIIP na \server\share pomocí winspoolu.".

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

## <a name="cprintdialoggetdevmode"></a><a name="getdevmode"></a>CPrintDialog::GetDevMode

Načte `DEVMODE` strukturu.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Datová struktura [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) která obsahuje informace o inicializaci zařízení a prostředí tiskového ovladače. Je nutné odemknout paměť převzatou touto strukturou pomocí funkce Windows [GlobalUnlock,](/windows/win32/api/winbase/nf-winbase-globalunlock) která je popsána v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst informace o tiskovézařízení.

### <a name="example"></a>Příklad

  Viz příklad pro [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdrivername"></a><a name="getdrivername"></a>CPrintDialog::GetDriverName

Načte název aktuálně vybraného ovladače tiskárny.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CString` zadání systémově definovaného názvu ovladače.

### <a name="remarks"></a>Poznámky

Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název systémově definované ovladače tiskárny zařízení. Použijte ukazatel na `CString` objekt `GetDriverName` vrácený jako `lpszDriverName` hodnotu volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Příklad

  Viz příklad [cprintdialog::GetDeviceName](#getdevicename).

## <a name="cprintdialoggetfrompage"></a><a name="getfrompage"></a>CPrintDialog::GetFromPage

Načte počáteční stránku rozsahu tisku.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční číslo stránky v rozsahu stránek, které mají být vytištěny.

### <a name="remarks"></a>Poznámky

Volání této funkce `DoModal` po volání načíst počáteční číslo stránky v rozsahu stránek, které mají být vytištěny.

### <a name="example"></a>Příklad

  Viz příklad [cprintdialog::m_pd](#m_pd).

## <a name="cprintdialoggetportname"></a><a name="getportname"></a>CPrintDialog::GetPortName

Načte název aktuálně vybraného portu tiskárny.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybraného portu tiskárny.

### <a name="remarks"></a>Poznámky

Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název aktuálně vybraného portu tiskárny.

### <a name="example"></a>Příklad

  Viz příklad [cprintdialog::GetDeviceName](#getdevicename).

## <a name="cprintdialoggetprinterdc"></a><a name="getprinterdc"></a>CPrintDialog::GetPrinterDC

Načte popisovač do kontextu zařízení tiskárny.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení tiskárny v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud byl parametr *bPrintSetupOnly* konstruktoru `CPrintDialog` NEPRAVDA (označující, že je `GetPrinterDC` zobrazeno tiskové dialogové okno), vrátí popisovač do kontextu zařízení tiskárny. Chcete-li odstranit kontext zařízení po dokončení jeho používání, je nutné volat funkci [Windows DeleteDC.](/windows/win32/api/wingdi/nf-wingdi-deletedc)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

## <a name="cprintdialoggettopage"></a><a name="gettopage"></a>CPrintDialog::GetToPage

Načte koncovou stránku rozsahu tisku.

```
int GetToPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo koncové stránky v rozsahu stránek, které mají být vytištěny.

### <a name="remarks"></a>Poznámky

Volání této funkce `DoModal` po volání načíst číslo koncové stránky v rozsahu stránek, které mají být vytištěny.

### <a name="example"></a>Příklad

  Viz příklad [cprintdialog::m_pd](#m_pd).

## <a name="cprintdialogm_pd"></a><a name="m_pd"></a>CPrintDialog::m_pd

Struktura, jejíž členové ukládají vlastnosti objektu dialogového okna.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Poznámky

Po vytvoření `CPrintDialog` objektu můžete `m_pd` před voláním členské funkce [DoModal](#domodal) nastavit různé aspekty dialogového okna. Další informace o `m_pd` struktuře naleznete v tématu [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) v sadě Windows SDK.

Pokud změníte `m_pd` datový člen přímo, přepíšete jakékoli výchozí chování.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

## <a name="cprintdialogprintall"></a><a name="printall"></a>CPrintDialog::PrintAll

Určuje, zda se mají vytisknout všechny stránky dokumentu.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud mají být vytištěny všechny stránky v dokumentu; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce `DoModal` po volání k určení, zda chcete vytisknout všechny stránky v dokumentu.

### <a name="example"></a>Příklad

  Viz příklad [cprintdialog::m_pd](#m_pd).

## <a name="cprintdialogprintcollate"></a><a name="printcollate"></a>CPrintDialog::PrintCollate

Určuje, zda jsou požadovány kompletované kopie.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud uživatel zaškrtne políčko kompletovat v dialogovém okně; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce `DoModal` po volání k určení, zda tiskárna má kompletovat všechny tištěné kopie dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

## <a name="cprintdialogprintrange"></a><a name="printrange"></a>CPrintDialog::PrintRange

Určuje, zda se má vytisknout pouze zadaný rozsah stránek.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se má vytisknout pouze rozsah stránek v dokumentu; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce `DoModal` po volání k určení, zda chcete vytisknout pouze rozsah stránek v dokumentu.

### <a name="example"></a>Příklad

  Viz příklad [cprintdialog::m_pd](#m_pd).

## <a name="cprintdialogprintselection"></a><a name="printselection"></a>CPrintDialog::PrintSelection

Určuje, zda se mají vytisknout pouze aktuálně vybrané položky.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud mají být vytištěny pouze vybrané položky; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce `DoModal` po volání k určení, zda chcete vytisknout pouze aktuálně vybrané položky.

### <a name="example"></a>Příklad

  Viz příklad [cprintdialog::m_pd](#m_pd).

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo – struktura](../../mfc/reference/cprintinfo-structure.md)
